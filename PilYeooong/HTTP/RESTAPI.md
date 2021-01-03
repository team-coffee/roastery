
## # REST API란?

REST API는 REST라는 아키텍쳐 스타일을 따르는 API라고 한다.
여기서 "**아키텍쳐 스타일이 뭐지**?" 라는 말이 나올 수 있는데, 아키텍쳐 스타일은 _**제약 조건들의 집합**_ 이라고 이해하면 된다.

그렇다면 REST의 정의부터 아키텍쳐 스타일까지 좀 더 자세히 알아보도록 하자

<br />

## # REST (Representational State Transfer)의 정의

HTTP를 기반으로, 자원을 정의하고, 자원에 접근하는 방식을 정해 놓은 아키텍쳐이다.
웹에 존재하는 모든 자원에 고유한 식별자인 _**URI**_를 부여해 활용한다.

> 여기서 자원은 저장된 데이터(DBMS), 이미지, 동영상, 문서 파일, 서비스 (이메일, 메시지)를 모두 포함

REST를 프로토콜이나 표준으로 오해하면 안된다.

<br />


## # REST 아키텍쳐에 적용되는 제약 조건
### ✔️ Client - Server
> - 클라이언트와 서버가 각각 독립적으로 분리되어 있다.

### ✔️ Stateless
> - 클라이언트의 상태가 서버가 저장하지 않는다.

### ✔️ Cacheable
> - 클라이언트는 응답을 캐싱 할 수 있다.

### ✔️ Layered system
> - API 서버는 순수 비지니스 로직을 수행 한다.
- 클라이언트는 대상 서버에 직접 연결되었는지, 또는 중간 서버를 통해 연결되었는지 인지 할 수 없다.
- 중간 서버 (로드 밸런싱, 공유 캐시)를 제공함으로써 시스템 규모 확장성이 향상 된다.

### ✔️ Uniform interface
> - 리소스는 URI로 식별 된다.
- HTTP 메시지를 통해 리소스를 조작 할 수 있다.
- Self-descriptive messages (자기 서술적 메시지)
- hypermedia as the engine of application state (HATEOAS)

### ✔️ Code on demand (optional)
> - 서버가 클라이언트에게 코드를 응답해주면, 클라이언트는 응답 코드를 실행 할 수 있다
		ex) **Javascript**      
        

이것이 REST의 제약 조건들이다. 오늘 날의 REST API라고 불리는 API들은 모두 REST의 아키텍쳐 스타일을 만족할까?
대부분은 HTTP의 특징이기도 하며, HTTP만 잘 따르더라도 대부분 잘 지킬 수 있다. 하지만 **Uniform interface**의 **Self-descriptive messages**나 **HATEOAS**를 만족하는 API는 찾기 힘들다고 한다.

<br />

## # 왜 만들었을까?
REST를 만든 사람은 로이 필딩(Roy Fielding)이라는 HTTP의 주요 저자 중 한 사람이다.
2000년도에 로이 필딩의 박사 학위 논문에서 소개 되었으며, 당시 웹(HTTP)의 설계의 우수성에 비해 웹이 제대로 사용되어지지 않는 모습에 안타까워 웹의 장점을 최대한 활용 할 수 있는 아키텍쳐를 만들었으며 그게 바로 **REST**이다.

<br />

## # REST의 목적

서버 / 클라이언트가 각각 독립적으로 진화가 가능해진다.
서버의 기능이 변경되어도 클라이언트 단에서도 업데이트가 이루어지지 않아도 된다는 말이다.

웹은 REST를 잘 따르며 발전 하고 있다.
웹 페이지의 기능이 변경되더라도, 새로운 기능을 반영하기 위해서 웹 브라우저를 업데이트 할 필요가 없다.


<br />

## # 정리

REST는 웹에 사용되는 자원들에 대한 정의, 자원에 접근 방식에 대한 제약 조건들의 집합이며, 이 제약 조건들을 지키며 설계한 API를 REST API라고 할 수 있겠다.

<br />

--- 

_**참고 자료 및 영상**_
> - [그런 REST API로 괜찮은가?](https://www.youtube.com/watch?v=RP_f5dMoHFc)
> - https://www.redhat.com/en/topics/api/what-is-a-rest-api
> - https://www.namespaceit.com/blog/what-is-a-restful-api-rest-api-and-how-does-it-work
