## Multi Thread에 대해서 설명해주세요.

thread는 한 process 내에서 실행되는 동작의 단위(function의 단위) 입니다. 
각 thread는 속해있는 process의 Stack 메모리를 제외한 나머지 Code, Data, Heap 메모리 영역을 공유할 수 있습니다.
Multi Thread란 하나의 process가 동시에 여러 개의 일을 수행할 수 있도록 해주는 것입니다.
즉, 하나의 process에서 여러 작업을 병렬로 처리하기 위해 multi Thread를 사용합니다.
한 process 내에 여러 개의 Thread가 있고, 각 Thread들은 Stack 메모리를 제외한 나머지 영역(Code, Data, Heap)들을 공유하게 됩니다.


## Multi Thread가 Process의 메모리 영역을 공유할 때 Process의 Stack 영역은 공유되지 않는 이유?

Thread는 독립적인 기능을 수행한다. 즉, 독립적으로 함수를 호출한다.
이를 위해 Stack 메모리 영역이 각자 필요한 것이다.
독립적인 Stack 메모리 영역, PC Register가 필요하다.


## 멀티쓰레드 동시성 (Multi Thread Concurrency)
- 한 프로세스 내에서도 CPU core는 왔다갔다하면서 Context Switching이 일어난다.
- ***쓰레드끼리도 Context Switching 이 일어나***므로 PC Register가 각각 필요하다.


## 멀티쓰레드는 Stack 메모리 & PC Register를 각각 가진다.

**독립적인 Stack 메모리 영역이 필요한 이유?** 
**⇒ 쓰레드는 실행의 단위이므로 독립적인 함수의 단위이다. 함수를 호출하기 위해서 독립적인 Stack 메모리 영역이 필요하다.**
Thread가 함수를 호출하기 위해서는 **파라미터 전달**, **Return Address 전달**, **함수 내 지역변수 저장** 등을 위한 **독립적인 Stack 메모리 영역을 필요**로 한다.
결과적으로 쓰레드는 프로세스로부터 Stack 메모리 영역은 독립적으로 할당 받고, Code, Data, Heap 영역은 공유하는 형태를 갖게 된다.

**독립적인 PC Register가 필요한 이유?**
**⇒ 멀티쓰레드에서도 Context Switching이 일어난다. 때문에 PC Register에 code주소가 저장되어 있어야 왔다갔다 하면서 이어서 실행할 수 있게 된다.**
또한 멀티 쓰레드에서는 각각의 쓰레드마다 PC Register를 가지고 있어야 한다.
그 이유는 한 프로세스 내에서도 쓰레드끼리 Context Switch가 일어나게 되는데, PC Register에 code address가 저장되어 있어야 이어서 실행할 수 있기 때문이다.

---

## 메모리 영역
### 코데힙스

*low memory address 낮은 메모리 주소*
- **Code**
    - 프로그램의 코드
    - Program Counter (PC)
- **Data**
    - 전역변수, static변수
- **Heap**
    - 사용자의 동적할당 (개발자 영역)
- **Stack**
    - 쓰레드(함수)가 쌓이는 영역
    - 시작위치 : Stack Pointer(SP)
*high memory address 높은 메모리 주소*

---

### 1. **Thread는 왜 독립적인 Stack 메모리 영역이 필요한가요?**

```markdown
쓰레드는 프로세스 내에서 독립적인 기능을 수행하는 단위입니다.
따라서 독립적인 함수를 실행하는 단위입니다.
때문에 함수를 호출할 때 필요한 파라미터, return 주소, 지역변수 등을 저장하기 위해
독립적인 스택 메모리 영역을 필요로 합니다. 
```

### 2. **Process와 Thread를 비교해서 설명해주세요.**

```markdown
프로세스는 (운영체제로부터 자원을 할당받는) 작업의 단위이고,
쓰레드는 (프로세스가 할당받은 자원을 이용하는) 실행의 단위입니다.

즉, 프로세스는 메모리에 적재되어 CPU를 할당받아 실행되고
쓰레드는 프로세스 내에서 함수가 실행되는 것입니다.

프로세스는 code, data, heap, stack 메모리 영역을 사용하고
쓰레드는 프로세스의 메모리 영역 중 code, data, heap 영역만 공유해서 사용합니다.
```
