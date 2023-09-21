# HTTP request method 중 GET vs POST를 비교설명해주세요.
- GET 메소드는 클라이언트가 서버에게 리소스를 요청할 때 사용하는 메소드이고,
- POST 메소드는 클라이언트가 서버에게 데이터 처리(주로 생성)를 요청할 때 사용하는 메소드입니다.

- GET 요청의 경우 필요한 정보를 특정하기 위해 URL 뒤에 Query String을 추가하여 정보를 조회하고,
- POST 요청의 경우 전달할 데이터를 Body 부분에 포함하여 통신합니다.

- GET 요청의 경우 URL 뒤의 Query String까지 포함해서 브라우저 히스토리에 남게 되고 캐시가 가능하지만,
- POST 요청의 경우 브라우저 히스토리에 남지 않고 캐시도 불가능합니다.


**캐시란 ?**
```
한 번 접근 후, 같은 요청을 할 경우 빠르게 접근하기 위해
데이터를 저장시켜 놓는다.
```


# 주요 HTTP request Method
- GET, POST, PUT, DELETE, PATCH


## GET
- 리소스 조회
- GET 메소드는 클라이언트가 서버에게 정보를 요청할 때 사용하는 method입니다.
- GET을 통한 요청은 URL 주소 끝에 key-value 쌍으로 파라미터를 포함하여 전송합니다. 이 부분을 Query String 쿼리스트링 이라고 합니다.
- GET의 주요한 특징 중 하나는 **캐시가 가능**하다는 것입니다.
  한 번 서버에 GET 요청을 한 적이 있다면 브라우저가 그 결과를 저장해둡니다. 이후 동일한 요청은 브라우저에 저장된 값으로 가져올 수 있습니다.
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/9ef8a408-96f3-4348-a8dd-32dd9d5726fb)


## POST
- 리소스 생성 (요청데이터 처리)
- POST 메소드는 클라이언트가 서버에게 body를 통해 전달한 데이터를 서버가 처리하도록 요청하는 메소드입니다.
- 서버는 POST 메소드로 요청이 들어오면 꼭 리소스를 등록하는 것뿐만 아니라 리소스마다 다양하게 처리를 합니다.
  데이터를 생성하거나 변경하기도 하지만 특정 프로세스를 처리하기도 합니다.

## DELETE
- 리소스 삭제

## PUT
- 리소스 모두 대체
```
요청 전 서버 리소스
user/10
{
  name: "Suna",
  language: "Java"
}

요청
PUT user/10
{
  name: "Suna"
}

요청 후 서버 리소스
user/10
{
  name: "Suna"
}

```

## PATCH
- 리소스 일부만 수정
```
요청 전 서버 리소스
user/10
{
  name: "Suna",
  language: "Java"
}

요청
PUT user/10
{
  name: "Suna"
}

요청 후 서버 리소스
user/10
{
  name: "Suna",
  language: "Java"
}

```


### HTTP request method 중 PUT vs Patch를 비교 설명해주세요.
```
PUT 메소드와 PATCH 메소드는 모두 서버의 리소스를 업데이트하는 메소드라는 공통점이 있습니다.
하지만 PUT 요청의 경우, 모든 리소스를 대체하고
PATCH 요청의 경우, 일부 리소스만 수정하게 됩니다.
```


