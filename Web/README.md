# Web

* [쿠키와 세션](#쿠키와-세션)
* HTTP Status Code
* REST
* 브라우저 주소 창에 www.naver.com을 쳤을 때 동작 과정
* [HTTP 1.0, 1.1, 2.0, 3.0 대표 차이점](#HTTP-버전-차이점)
* [아파치와 엔진엑스의 차이](#아파치와-엔진엑스의-차이점)
* WAS 서버와 WEB 서버의 차이
* 스프링 프레임워크란
* 스프링과 스프링 부트의 차이
* 스프링 MVC 구조
* 스프링 필터와 인터셉터 차이
* Dispatcher-Servlet
* Dependency Injection
* Aspect Oriented Programming
* Data Access Object

<br />
---

## 쿠키와 세션

* 일반적으로 HTTP는 Connectionless/Stateless이다. 하지만 많은 웹 서비스의 경우, 로그인 한 계정 상태 등을 유지한 채로 서비스를 제공해야 한다. 따라서, 필요한 정보 및 상태를 유지 및 저장하기 위해 쿠키/세션을 사용한다.
* 우선 클라이언트가 로그인 요청을 하면, 서버는 해당 요청의 유효성을 확인하고, 로그인 정보에 맞춰 세션 아이디를 저장한다. 그 후 클라이언트에게 응답으로 세션 정보를 쿠키라는 형태로 넘겨주어 클라이언트는 이 쿠키를 로컬에 저장한다.
* 클라이언트가 서버에 요청 시 쿠키 값을 함께 전달하여 Stateful한 서비스를 제공받는다.

## HTTP 버전 차이점

* HTTP 1.0은 상태 코드가 존재하는 기본적인 프로토콜이다. 일반적으로 HTTP에 대해 알고있는 것처럼 Connectionless/Stateless해서 모든 요청마다 새로운 TCP 요청 생성 및 해제를 수행한다.
* HTTP 1.1에 추가된 가장 큰 특징은 Connection 유지다. Persistent-Connection(HTTP Keep-Alive)이나 HTTP Piplelining과 같은 모델이 있는데, 커넥션 유지를 통해 TCP 세션 처리 부하를 굉장히 줄일 수 있다. 
* HTTP 2.0에는 대표적으로 Multiplexed Stream 기능이 추가되었고, Head of Line Blocking이 발생하는 것을 막는다.
* HTTP 3.0의 가장 큰 격변은 QUIC라는 UDP 기반 프로토콜의 적용이다. 기존 HTTP는 TCP 위에서 동작한 것에 비해 HTTP 3.0은 UDP 위에서 동작한다. QUIC는 여러 최신 프로토콜의 특장점을 합쳐 만들어져서 속도, 보안, 신뢰성, 효율성 등 다양한 측면에서 우수하다.

## 아파치와 엔진엑스의 차이점

* 아파치는 클라이언트 접속마다 프로세스나 쓰레드를 생성하는 구조다. 
* 엔진엑스는 이벤트를 기반으로 select(범용 디폴트)/epoll(리눅스)/IOCP(윈도우)를 사용하여 IO를 처리한다.
* 아파치는 확장성이나 호환성에 유리한데 비해, 엔진엑스가 성능면에서 유리하다. (엔진엑스가 컨텍스트 스위칭이 훨씬 적고 연결 오버헤드가 적다.)