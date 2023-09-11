## 메모리 관리 기법에는 2가지가 있다.
1. 페이징 paging 기법 - **일정한 크기 단위( page )**의 page로 메모리를 나누어 할당하는 방법
     => 내부단편화 (프로세스 논리적 메모리 공간에 빈공간 생기는 것 -> 필요한 메모리 공간보다 더 큰 논리적 메모리 공간이 할당되어 메모리가 낭비되는 문제)
3. 세그먼테이션 segmentation 기법 - **논리적 의미 단위( segment )**의 segmentation으로 메모리를 할당하는 방법
     => 외부단편화 (물리적 메모리 공간에 빈 공간이 생기는 것 -> 활용 불가)


## segmentation에 대해서 설명해주세요.
- segmentation이란 프로세스가 할당 받은 논리적 주소 공간을 논리적 의미 단위(segment)로 나누어,
  연속되지 않는 물리적 메모리에 할당될 수 있도록 하는 메모리 관리 기법입니다.
=> 세그먼테이션 기법이란, 프로세스가 할당받은 논리적 주소 공간을 논리적 의미의 일정 단위인 segment로 나누어 물리적 메모리에 할당되는 기법입니다.

- segmentation 기법은 프로세스가 할당받은 논리적 메모리 공간을 논리적 의미 단위(segment)로 나누어 물리적 메모리 공간에 할당될 수 있도록 하는 메모리 관리 기법입니다.
- 일반적으로 프로세스의 메로리 영역 중 code, data, heap, stack 등의 **의미** 단위로 **세그먼트를 정의**하는 경우가 많습니다.
- 주소 바인딩을 위해 각 프로세스마다 segment table을 갖습니다.
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/86f5c7d9-a4e5-48fc-aa8e-de6b4d9545d2)



### segmentation의 메모리 단편화(Memory Fragmentation) 문제에 대해서 설명해주세요.
```
segmentation 기법에서는 segment 단위로 메모리를 할당하기 때문에 내부단편화 문제가 발생하지 않습니다.
하지만, 서로 다른 크기의 segment들이 메모리에 적재되고 제거되는 일이 반복되면,
외부 단편화 문제가 발생할 수 있습니다.
```

### paging과 segmentation의 차이는 뭔가요?
```
paging은 일정한 크기 단위인 page로 메모리 공간을 나누어 할당되도록 하는 기법이고,
segmentation은 의미 단위인 segment로 나누어 메모리에 할당되록 하는 기법입니다.
여기서 의미 단위는 일반적으로 code, data, heap, stack 과 같은 단위로 나누게 됩니다.

paging의 경우에는 내부 단편화 문제가 발생할 수 있고, segmentation은 외부 단편화 문제가 발생할 수 있습니다.
```

### paged segmentation 페이지드 세그먼테이션 기법에 대해서 아시나요?
```
paged segmentation은 segmentation 기법을 기본으로 하되 segment를 page 단위의 배수로 관리하는 기법입니다.

즉, 프로세스의 메모리 공간을 의미 단위인 segment로 나누고, 이 개별 segment를 다시 page 단위로 나누어 page의 배수가 되도록 하는 방법입니다.

이를 통해 segmentation 기법에서 발생하는 외부 단편화 문제를 해결할 수 있습니다. ( 내부 단편화는 발생할 수 있음 )
동시에 segment 단위로 프로세스 간의 공유, 접근 권한 보호와 같이 paging 기법의 단점이 보완될 수 있도록 할 수 있습니다.
```
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/0a7c27bd-3d6d-49a4-9ab7-6f95f0b0459e)








