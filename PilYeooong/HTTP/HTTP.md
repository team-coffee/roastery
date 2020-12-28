## HTTP (Hyper Text Trasfer Protocol)

W3 상에서 정보를 주고받을 수 있는 프로토콜이며, 웹에서 이루어지는 모든 데이터 교환의 기초

### 기반 프로토콜

- 현재 주로 사용하는 HTTP/1.1은 **TCP**를 기반으로 동작한다
- HTTP/2 또한 TCP를 기반으로 동작하며, HTTP/3은 UDP를 기반하고 있다

### 특징

- 클라이언트 / 서버의 구조
- 단순하며, 확장이 용이하다
- 무상태(Stateless) - 서버는 클라이언트의 상태를 저장하고 있지 않는다
- 비연결성 - 기본적으로는 서버 / 클라이언트간의 연결을 유지하지 않는다
    - 비연결성의 한계
        1. 매번 TCP/IP 연결을 맺어야 함
        2. HTML 뿐만이 아닌 JS, CSS, 이미지 등 수많은 자원들에 대한 연결이 각각 맺어짐
    - 극복
        1. 현재는 HTTP 지속 연결(Persistent Connections)로 문제를 해결
        (한번의 연결로, 필요한 자원을 모두 받고 연결을 종료)

## HTTP 메시지

HTTP 메시지를 통해 거의 모든 형태의 데이터를 전송 할 수 있으며, 서버 간의 통신에도 이용된다.
(HTML, TEXT, JSON, XML, img, mov, etc...)

### 종류

- Request Message - 요청 메시지
- Response Message - 응답메시지

### 요청 메시지에 포함되는 것들

- HTTP 메서드 (GET, POST, PUT, PATCH, DELETE ...)
- 요청 대상
ex) year?query=2020
- HTTP 버전
- HTTP 헤더 (Accept, Host ...)

### 응답 메시지에 포함되는 것들

- HTTP 버전
- HTTP 상태코드 (2xx, 3xx, 4xx, 5xx)
- HTTP 헤더 (Content-Type, Content-Length ...)
- HTTP 메시지 바디 (전송 할 데이터가 담겨있음)

## HTTP 메서드

- **주요 메서드**
    - GET - 리소스 조회
    - POST - 요청 데이터 처리 (리소스 등록)
    - PUT - 리소스를 대체, 리소스가 존재 하지 않으면 생성
    - PATCH - 리소스의 특정 부분을 변경
    - DELETE - 리소스 삭제
- **기타 메서드**
    - HEAD - GET과 동일하지만, 메시지 부분을 제외하고, 상태와 헤더만 반환
    - OPTIONS - 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명
    ex) CORS의 Preflight
    - CONNECT - 대상 자원으로 식별되는 서버에 대한 터널을 설정
    - TRACE - 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트 수행
- **HTTP 메서드의 속성**
    - 안전 - 호출해도 리소스를 변경하지 않는다. (GET, HEAD, OPTIONS)
    - 멱등 - 여러번 호출하여도 결과는 일정 (GET, PUT, DELETE), 외부 요인으로 인해 중간에 리소스가 변경     되는 부분까지는 고려하지 않는다.
    - 캐시 가능

## HTTP 상태코드

- 1xx (Informational) - 요청이 수신되어 처리 중
- 2xx (Successfult) - 요청이 정상적으로 처리 됨
    - 200 (OK)
        - 요청이 성공적
    - 201 (Created) 
        - 요청이 성공적이며, 새로운 리소스가 생성됨
    - 202 (Accepted) 
        - 요청이 받아졌으나, 처리가 완료되지 않았다
    - 204 (No Content) 
        - 서버가 요청을 정상적으로 수행하였으나, 응답으로 보낼 본문이 없다
- 3xx (Redirection) - 요청을 완료하기 위해서 추가 동작이 필요하다 (리다이렉션)
    - 301 (Moved Permanently) 
        - 영구적 리다이렉션
        - 리다이렉트시 요청 메서드가 GET으로 변경, 요청 본문이 제거 될 수 있음
    - 302 (Found) 
        - 일시적 리다이렉션
        - 요청 메서드가 GET으로 변경, 요청 본문이 제거 될 수 있음
    - 304 (Not Modified) 
        - 캐시 목적으로 사용
        - 클라이언트는 계속해서 응답의 캐시된 버전을 사용할 수 있다.
    - 307 (Temporary Redirect) 
        - 일시적 리다이렉션
        - 요청 메서드와 본문이 유지 된다. (변경되면 안됨)
    - 308 (Permanent Redirect) 
        - 영구적 리다이렉션
        - 리다이렉트시 요청 메서드와 본문을 그대로 유지
- 4xx (Client Error) - 클라이언트 오류, 잘못 된 문법으로 인해 서버가 요청을 처리할 수 없다
    - 400 (Bad Request) 
        - 클라이언트가 잘못된 요청을 해서 서버가 요청을 처리 할 수 없음
    - 401 (Unauthorized)
        - 인증(Authentication) 되지 않음
        - 오류 발생시 응답 헤더에 WWW-Authenticate  헤더를 추가하여 인증 방법을 첨부
        - 메시지는 Unauthorized이지만 인증(Authentication)의 용도로 사용 된다.
    - 403 (Forbidden)
        - 인증은 되었지만, 접근 권한이 존재 하지 않을 때
        - ex) 관리자 전용 페이지에 일반 사용자가 접근하려 하는 경우
    - 404 (Not Found)
        - 요청 리소스가 서버에 존재하지 않는다.
- 5xx (Server Error) - 서버 오류, 서버가 요청을 정상적으로 처리하지 못한다
    - 500 (Internal Server Error) 
        - 서버 내부 문제로 인한 오류
    - 503 (Service Unavailable) 
        - 서버가 일시적인 과부화, 혹은 점검으로 인해 잠시 요청을 처리 할 수 없음
        - Retry-After 헤더 필드로 복구 시점을 전달 가능
