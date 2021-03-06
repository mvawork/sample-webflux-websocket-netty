# Spring Boot 2.0 WebFlux Reactive WebSocket client and server #

Sample project using **spring-boot-webflux** with **reactor-netty** reactive websocket client and server. The target of the sample is provide a sample on how to directly use WebSocketHandler handle method to receive the messages and publish them to a Flux which the business logic can consume and process as needed. 

## Start ##

To start the sample just run `gradlew bootRun`.

## Message ##

The messages exchanged are plain text integer values starting at 0.

## Server ##

The server will listen to port `${server.port}` and path `${sample.path}` for connections. Once a connection is established it will wait for a message and once is received it will start to send messages to the client each 500 milliseconds.

[ServerLogic](src/main/java/sample/webflux/websocket/netty/logic/ServerLogic.java)

## Client ##

The client will connect two instances to the server. It will send a message while logging any messages received from the server. After 10 seconds the client will disconnect and the application will terminate.

[ClientLogic](src/main/java/sample/webflux/websocket/netty/logic/ClientLogic.java)

## Notes ##

Make sure you don't have **spring-boot-starter-web** as dependency or the embedded server will not correctly register your handlers since it will be expecting the servlet version instead the reactive version.

## Documentation ##

[WebSocket](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html#webflux-websocket)

[Servers](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html#webflux-httphandler)