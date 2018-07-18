# logging-demo

## Maven build

```
$ mvn clean package
```

## Docker build

```
$ docker build -t logging-demo .

$ docker images
REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
logging-demo                                latest              1444f50dcadc        9 seconds ago       117M
```

## Run demo application

Run application with docker image.

```
$ docker run -p 8080:8080 logging-demo
```

Connect to localhost:8080 via web browser.

You can see "Hello World!" messages.

## Connect to application via ssh and confirm log file

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
79e28edfbb12        logging-demo        "java -Djava.securit…"   4 minutes ago       Up 4 minutes        0.0.0.0:8080->8080/tcp   gifted_ride

$ docker exec -it 79e28edfbb12 sh
/ # tail -f logs/spring-boot-logging.log 
2018-07-16 17:30:30.949 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Starting ProtocolHandler ["http-nio-8080"]
2018-07-16 17:30:30.985 [main] INFO  o.a.tomcat.util.net.NioSelectorPool - Using a shared selector for servlet write/read
2018-07-16 17:30:31.058 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat started on port(s): 8080 (http)
2018-07-16 17:30:31.084 [main] INFO  com.example.demo.DemoApplication - Started DemoApplication in 11.794 seconds (JVM running for 13.286)
2018-07-16 17:31:40.057 [http-nio-8080-exec-1] INFO  o.a.c.c.C.[Tomcat].[localhost].[/] - Initializing Spring FrameworkServlet 'dispatcherServlet'
2018-07-16 17:31:40.059 [http-nio-8080-exec-1] INFO  o.s.web.servlet.DispatcherServlet - FrameworkServlet 'dispatcherServlet': initialization started
2018-07-16 17:31:40.153 [http-nio-8080-exec-1] INFO  o.s.web.servlet.DispatcherServlet - FrameworkServlet 'dispatcherServlet': initialization completed in 86 ms
2018-07-16 17:31:40.315 [http-nio-8080-exec-1] INFO  com.example.demo.HomeRestController - logback example - info level
2018-07-16 17:31:40.316 [http-nio-8080-exec-1] WARN  com.example.demo.HomeRestController - logback example - warn level
2018-07-16 17:31:40.318 [http-nio-8080-exec-1] ERROR com.example.demo.HomeRestController - logback example - error level
```


