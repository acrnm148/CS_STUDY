## 운영체제의 메모리 관리

## paging이란 뭔가요?
- paging이란 process가 할당받은 메모리 공간을 일정한 page 단위로 나누어,
물리 메모리(LAM)에서 연속되지 않는 서로 다른 위치에 저장하는 메모리 관리 기법입니다.
=> 물리 메모리(LAM)의 연속되지 않는 서로 다른 위치에 page 단위만큼 저장한다.

- paging 기법은 process가 할당받은 메모리 공간을 동일한 크기의 page 단위로 나누고, (=> 논리적 메모리)
    물리적 메모리(LAM) 의 서로 다른 위치에 이 page들을 저장하는 메모리 관리 기법입니다.
  
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/0cbed6c2-96b3-429a-a31c-9a80dfbfe5f9)

=> 연속되는 메모리 공간에 넣기에는 너무 크므로 잘라서 서로 다른 위치에 저장하는 것.
=> 이렇게 넣으면 CPU가 접근할 때 찾아야 한다. 이 때 쓰는게 주소 바인딩을 위한 페이지 테이블이다.

- paging 기법에서는 물리적 메모리를 미리 page와 같은 크기로 나누어둡니다.
  => page 단위로 메모리 적재가 이루어지기 때문에, 미리 분할해두면 빠르게 메모리 할당이 이루어집니다.
- paging 기법에서는 하나의 process 내에서도 page 단위로 서로 다른 물리적 메모리에 저장되기 때문에 주소 바인딩을 위해서는 별도의 page table이 필요합니다.
  => 모든 process가 각각의 주소 변환을 위한 page table을 갖습니다.


## 논리적 주소 (logical address)
- 논리적 주소는 process가 메모리에 적재되기 위해 생성되는 독립적인 주소 공간입니다.
- 논리적 주소는 각 process마다 독립적으로 할당되며, 0번지부터 시작합니다.

## 물리적 주소 (Pyhsical address)
- 물리적 주소는 process가 실제로 메모리에 적재되는 위치입니다.

## 주소 바인딩 (address binding)
- CPU가 기계어 명령을 수행하기 위해 process의 논리적 주소가 실제 물리적 메모리의 어느 위치에 맵핑이 되는지 확인하는 과정입니다.


## 페이징의 장점
- 물리적 메모리(LAM)에 page 단위별로 저장하게 되어 메모리 낭비를 줄일 수 있다.
- 각각의 process별로 page table은 별도로 존재한다. 그래야 CPU가 접근하고 싶을 때 쉽게 찾아서 접근할 수 있다.

![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/17f05cf3-ca18-4dc4-9ac4-fec78295b93c)


## 페이징의 단점
### => "메모리 단편화"
```
외부 단편화 : 메모리 상의 비어있는 공간의 크기가 작아서, 빈 메모리 공간임에도 활용되지 못하는 문제입니다.
=> 메모리 내 빈 공간 크기가 작아서 활용하지 못하는 문제 ( 부족한 것 )
내부 단편화 : 프로세스가 필요한 메모리 양보다 더 큰 메모리가 할당되어서 메모리 공간이 낭비되는 상황입니다.
=> 프로세스가 필요한 메모리 양보다 더 큰 메모리가 할당이 되어서 메모리 공간이 낭비되는 문제 ( 더 많이 준 것 )
```
페이징 기법에서는 프로세스의 논리적 주소 공간과 물리적 메모리가 페이지 단위로 동일한 크기로 나누어져 있어 외부 단편화 문제는 발생하지 않습니다.
다만, **프로세스의 논리적 주소 공간의 크기가 페이지 단위의 배수라는 보장이 없기 때문에**
프로세스의 주소 공간 중 가장 마지막 페이지는 내부 단편화 문제가 발생할 수 있습니다.


## 내부단편화와 외부단편화란 무엇인가요?
```
내부 단편화란 프로세스가 필요한 논리적 주소 공간보다 더 큰 크기의 물리적 메모리 공간이 할당되어서 그만큼 메모리 공간이 낭비되는 문제입니다.
외부 단편화란 물리적 메모리의 빈 공간의 크기가 작아서 활용되지 못하는 문제입니다.
```
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/5b3aa6e8-a09b-409a-b676-ce9bb143f854)


