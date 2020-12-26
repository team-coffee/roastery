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