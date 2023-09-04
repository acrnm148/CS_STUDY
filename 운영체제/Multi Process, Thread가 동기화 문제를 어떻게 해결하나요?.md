## 동기화 문제
동기화 문제란, 서로 다른 thread가 메모리 영역을 공유하기 때문에 여러 개의 thread가 동시에 동일한 메모리 영역에 접근하여 엉뚱한 값을 읽거나 수정하는 문제입니다.

## Multi Process, Thread 환경에서 동기화 문제를 어떻게 해결하나요?
동기화 문제를 해결하기 위해 Mutex, Semaphore 기법 등을 사용할 수 있습니다.
### Mutex
뮤텍스란 1개의 thread만이 공유 메모리에 접근할 수 있도록 하는 방법입니다.
공유 자원을 점유하는 1개의 thread가 lock을 걸면, 다른 thread는 unlock이 될 때까지 해당 자원에 접근할 수 없습니다.
이는 공유 메모리에 하나의 쓰레드만 접근할 수 있으므로 경쟁상황(race condition)을 방지할 수 있습니다.
### Semaphore
세마포어란 S개의 thread만이 공유 메모리에 접근할 수 있도록 제어하는 동기화 기법입니다.
세마포어 기법에서는
- 정수형 변수 S(세마포) 값을 사용할 수 있는 자원의 수로 초기화 합니다.
- 자원에 접근하면 S-- 연산으로 세마포 값을 감소, 자원을 사용하여 방출하면 S++ 연산을 수행하여 세마포 값을 증가시킵니다.
- 이 때 세마포 값이 0이 되면 모든 자원이 사용 중임을 의미하고, 프로세스는 세마포 값이 0보다 커질 때까지 block 됩니다.


## atomic operation 원자적



## 동기화 문제
동기화 문제란 서로 다른 thread가 메모리 영역을 공유하기 때문에 여러 개의 thread가 동일한 메모리 영역에 접근하여 엉뚱한 값을 읽거나 수정하는 문제입니다.
예를 들면,
count++를 CPU 입장에서 분해해보면 3개의 atomic operations로 나뉩니다.
1. count 변수 값을 가져옵니다.
2. count 변수 값을 1 증가시킵니다.
3. 변경된 count 값을 저장합니다.

CPU는 atomic operation을 연산하게 됩니다. 따라서 count++를 하기 위해 3번의 연산을 하게 됩니다.
가정)
시분할 시스템으로 작동하는 multi process, multi thread 시스템에서 
2개의 thread가 동일한 데이터인 count에 동시에 접근하여 조작하는 상황을 가정해보겠습니다.
1. thread1에서도 count++를 하고, thread2에서도 count++를 한다면 정상적인 실행 결과는 2입니다.
2. 하지만 접근이 발생한 순서에 따라 실행 결과가 달라질 수 있습니다. 이를 경쟁 상황(race condition)이라고 합니다.
즉, 둘 이상의 thread가 동일한 자원에 접근하여 조작하고, 그 실행 결과가 접근이 발생한 순서에 따라 달라지는 것을 경쟁상황이라고 하고,
경쟁상황으로 인해 엉뚱한 값을 읽거나 수정하는 동기화 문제가 발생할 수 있습니다.

경쟁 상황으로부터 보호하기 위해 한 순간에 하나의 process 또는 thread 만이 해당 자원에 접근하여 조작할 수 있도록 보장해야 합니다.
즉, process/thread 들이 동기화되도록 할 필요가 있습니다.

![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/ba4de9a3-ff30-4296-b980-5de3bd57e4dc)

thread1) load count : 0
thread1) count = count + 1
-- context switching --
thread2) load count : 0
thread2) count = count + 1
thread2) save count : 1       => 현재 count : 1
-- context switching --
thread1) save count : 1


## 임계영역 (critical section)
"여러 개의 thread/process가 동시에 접근하는 프로그램 코드 부분으로, 
한 thread/process가 자신의 임계구역에서 수행하는 동안 다른 thread/process에서는 자신의 임계구역에 들어가지 못하도록 원자적으로 실행되어야 한다."

2개 이상의 thread 또는 process가 동시에 동일한 자원에 접근하도록 하는 프로그램 코드 부분.
한 process나 thread가 자신의 임계구역에서 수행하는 동안에는 다른 process나 thread들은 그들의 임계구역에 들어갈 수 없어야 한다는 것입니다.
즉, 임계 영역 내 코드는 원자적으로 실행되어야 합니다. (atomically)

임계영역이 원자적으로 실행되기 위해서는
각각의 thread/process는 그들의 임계영역에 진입하려면 
1, 진입 허가 요청을 해야합니다. 이 부분을 entry section 이라고 합니다.
2. 진입이 허가되면 임계 영역을 수행합니다. (critical section)
3. 임계 영역이 끝나면 퇴출을 하게 됩니다. 이 부분을 exit section 이라고 합니다.

임계영역의 원자성을 보장하여 process/thread 들이 동기화되도록 하는 방법이 Mutex와 Semaphore 입니다.


## Mutex 뮤텍스

동기화 방법 중 하나로 Mutual exclusion의 축약어입니다.
공유 자원에 접근할 수 있는 process/thread 개수를 1개로 제한합니다.
임계 영역을 보호하고, 경쟁상황을 방지하기 위해 mutex lock(뮤텍스 락)을 사용합니다.
즉, process/thread는 임계 영역에 들어가기 전에 반드시 lock을 획득해야 하고, 임계 영역 실행 후 빠져나올 때는 lock을 반환해야 합니다.
acquire() 함수가 lcok을 획득하고, release() 함수가 lock을 반환합니다.

```
acquire() // entry section
//critical section
release() // exit section
```
```
acquire() {
  while (!available);  // busy waiting : CPU 낭비
  available = false;  // 다른 녀석들 임계영역 진입 불가
}
```
```
release() {
  available = true;
}
```

![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/aeaccb56-bede-4ed2-83a6-37e64b38063d)

Thread1)
1. entry section : acquire() - lock 획득
2. 공유 자원 count에 접근하여 critical section 실행 (Thread1 : lock, Thread2 : blcok)
3. exit section : release() - lock 반환 (unlock)
Thread2)
1. entry section : acquire() - lock 획득
2. 공유 자원 count에 접근하여 critical sectino 실행 (Thread2 : lock, Thread1 : block)
3. exit section : release() - lock 반환 (unlock)



## Semaphore 세마포어

동기화 방법 중 하나로, 2개 이상의 process/thread가 공유 자원에 접근할 수 있는 동기화 방법입니다. (뮤텍스는 1개만 가능)
세마포어 변수 S(세마포)를 사용하여 동시에 접근 가능한 process/thread 개수를 저장합니다.
S가 0보다 크면 임계 영역에 들어갈 수 있고, entry section에서 S값을 1 감소시킵니다.
S가 0이면 다른 process/thread 들은 임계영역에 진입할 수 없습니다.
임계 영역이 끝나면 exit section에서 S값을 1 증가시킵니다.

세마포어에서 S값이 0,1만 가질 수 있을 경우 Binary Semaphore라고 합니다. 이는 Mutex와 거의 유사하게 작동합니다.

```
wait(S)     // entry section
critical section
signal(S)   // exit section
```
```
wait(S) {
  while (S <= 0); //busy wait
  S--;
}
```
```
signal(S) {
  S++;  
}
```

![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/420adff8-7892-4471-828b-f9dd27cbf2f1)


## 뮤텍스 & 세마포어
뮤텍스
1. entry section : acquire() - lock
2. critical section
3. exit section : release() - unlock
세마포어
1. entry section : wait(S)
2. critical section
3. exit section : signal(S)



### 뮤텍스와 세마포어 기법을 비교해서 설명해주세요.
```
Mutex는 오직 1개의 process/thread 만이 공유 자원에 접근할 수 있습니다.
Semaphore는 세마포 변수 S의 값 만큼 process/thread 들이 공유 자원에 접근할 수 있습니다.
Mutex는 binary semaphore라고 할 수 있습니다.
```

