# 프로젝트 구조

```
├── README.md
├── api-gateway
│   ├── build
│   │   ├── classes
│   │   │   └── java
│   │   │       └── main
│   │   │           └── com
│   │   │               └── sparta
│   │   │                   └── apigateway
│   │   │                       └── ApiGatewayApplication.class
│   │   ├── generated
│   │   │   └── sources
│   │   │       ├── annotationProcessor
│   │   │       │   └── java
│   │   │       │       └── main
│   │   │       └── headers
│   │   │           └── java
│   │   │               └── main
│   │   ├── resources
│   │   │   └── main
│   │   │       └── application.yml
│   │   └── tmp
│   │       └── compileJava
│   │           └── previous-compilation-data.bin
│   ├── build.gradle
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── sparta
│           │           └── apigateway
│           │               └── ApiGatewayApplication.java
│           └── resources
│               └── application.yml
├── build.gradle
├── config-server
│   ├── build
│   │   ├── classes
│   │   │   └── java
│   │   │       └── main
│   │   │           └── com
│   │   │               └── sparta
│   │   │                   └── configserver
│   │   │                       └── ConfigServerApplication.class
│   │   ├── generated
│   │   │   └── sources
│   │   │       ├── annotationProcessor
│   │   │       │   └── java
│   │   │       │       └── main
│   │   │       └── headers
│   │   │           └── java
│   │   │               └── main
│   │   ├── resources
│   │   │   └── main
│   │   │       ├── application.yml
│   │   │       └── config
│   │   │           ├── api-gateway.yml
│   │   │           ├── service-a.yml
│   │   │           └── service-b.yml
│   │   └── tmp
│   │       └── compileJava
│   │           └── previous-compilation-data.bin
│   ├── build.gradle
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── sparta
│           │           └── configserver
│           │               └── ConfigServerApplication.java
│           └── resources
│               ├── application.yml
│               └── config
│                   ├── api-gateway.yml
│                   ├── service-a.yml
│                   └── service-b.yml
├── eureka-server
│   ├── build
│   │   ├── classes
│   │   │   └── java
│   │   │       └── main
│   │   │           └── com
│   │   │               └── sparta
│   │   │                   └── eurekaserver
│   │   │                       └── EurekaServerApplication.class
│   │   ├── generated
│   │   │   └── sources
│   │   │       ├── annotationProcessor
│   │   │       │   └── java
│   │   │       │       └── main
│   │   │       └── headers
│   │   │           └── java
│   │   │               └── main
│   │   ├── resources
│   │   │   └── main
│   │   │       └── application.yml
│   │   └── tmp
│   │       └── compileJava
│   │           └── previous-compilation-data.bin
│   ├── build.gradle
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── sparta
│           │           └── eurekaserver
│           │               └── EurekaServerApplication.java
│           └── resources
│               └── application.yml
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradlew
├── gradlew.bat
├── service-a
│   ├── build
│   │   ├── classes
│   │   │   └── java
│   │   │       └── main
│   │   │           └── com
│   │   │               └── sparta
│   │   │                   └── servicea
│   │   │                       └── ServiceAApplication.class
│   │   ├── generated
│   │   │   └── sources
│   │   │       ├── annotationProcessor
│   │   │       │   └── java
│   │   │       │       └── main
│   │   │       └── headers
│   │   │           └── java
│   │   │               └── main
│   │   ├── resources
│   │   │   └── main
│   │   │       └── application.yml
│   │   └── tmp
│   │       └── compileJava
│   │           └── previous-compilation-data.bin
│   ├── build.gradle
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── sparta
│           │           └── servicea
│           │               └── ServiceAApplication.java
│           └── resources
│               └── application.yml
├── service-b
│   ├── build
│   │   ├── classes
│   │   │   └── java
│   │   │       └── main
│   │   │           └── com
│   │   │               └── sparta
│   │   │                   └── serviceb
│   │   │                       └── ServiceBApplication.class
│   │   ├── generated
│   │   │   └── sources
│   │   │       ├── annotationProcessor
│   │   │       │   └── java
│   │   │       │       └── main
│   │   │       └── headers
│   │   │           └── java
│   │   │               └── main
│   │   ├── resources
│   │   │   └── main
│   │   │       └── application.yml
│   │   └── tmp
│   │       └── compileJava
│   │           └── previous-compilation-data.bin
│   ├── build.gradle
│   └── src
│       └── main
│           ├── java
│           │   └── com
│           │       └── sparta
│           │           └── serviceb
│           │               └── ServiceBApplication.java
│           └── resources
│               └── application.yml
└── settings.gradle
```
