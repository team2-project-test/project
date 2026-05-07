# 서비스 아키텍처

## 전체 구조

```mermaid
graph TB
    Client(["👤 Client\n(Postman / Browser)"])

    subgraph MSA ["miniMSA"]
        ConfigServer["⚙️ Config Server\n:8888"]
        EurekaServer["📋 Eureka Server\n:8761"]
        Gateway["🚪 API Gateway\n:8080"]
        ServiceA["🅰️ Service A\n:8081"]
        ServiceB["🅱️ Service B\n:8082"]
    end

    %% 설정 수신 (시작 시)
    Gateway -- "설정 수신 (시작 시)" --> ConfigServer
    ServiceA -- "설정 수신 (시작 시)" --> ConfigServer
    ServiceB -- "설정 수신 (시작 시)" --> ConfigServer

    %% 서비스 등록 & 조회
    Gateway -- "서비스 등록" --> EurekaServer
    ServiceA -- "서비스 등록" --> EurekaServer
    ServiceB -- "서비스 등록" --> EurekaServer
    Gateway -- "서비스 주소 조회 (lb://)" --> EurekaServer

    %% 외부 요청 흐름
    Client -- "GET /service-a/**" --> Gateway
    Client -- "GET /service-b/**" --> Gateway
    Gateway -- "라우팅 (StripPrefix)" --> ServiceA
    Gateway -- "라우팅 (StripPrefix)" --> ServiceB
```

## 실행 순서

```mermaid
sequenceDiagram
    participant CS as Config Server :8888
    participant ES as Eureka Server :8761
    participant SA as Service A :8081
    participant SB as Service B :8082
    participant GW as API Gateway :8080
    participant CL as Client

    Note over CS: 1단계 - Config Server 기동

    SA->>CS: 설정 요청 (service-a.yml)
    CS-->>SA: port, eureka, actuator 설정 반환
    SB->>CS: 설정 요청 (service-b.yml)
    CS-->>SB: port, eureka, actuator 설정 반환
    GW->>CS: 설정 요청 (api-gateway.yml)
    CS-->>GW: port, routes, eureka 설정 반환

    Note over ES: 2단계 - Eureka Server 기동

    SA->>ES: 서비스 등록 (SERVICE-A / :8081)
    SB->>ES: 서비스 등록 (SERVICE-B / :8082)
    GW->>ES: 서비스 등록 (API-GATEWAY / :8080)

    Note over GW: 3단계 - 요청 처리

    CL->>GW: GET /service-a/actuator/health
    GW->>ES: SERVICE-A 주소 조회
    ES-->>GW: IP:8081 반환
    GW->>SA: GET /actuator/health
    SA-->>GW: {"status":"UP"}
    GW-->>CL: {"status":"UP"}
```

## 모듈별 역할 요약

| 모듈 | 포트 | 역할 | 주요 의존성 |
|---|---|---|---|
| `config-server` | 8888 | 전 서비스 설정 중앙 관리 | spring-cloud-config-server |
| `eureka-server` | 8761 | 서비스 주소 등록 & 조회 | spring-cloud-starter-netflix-eureka-server |
| `api-gateway` | 8080 | 단일 진입점, 라우팅 | spring-cloud-starter-gateway |
| `service-a` | 8081 | 비즈니스 서비스 A | spring-boot-starter-actuator |
| `service-b` | 8082 | 비즈니스 서비스 B | spring-boot-starter-actuator |

## Health Check 엔드포인트

| 대상 | URL |
|---|---|
| API Gateway 자체 | `GET http://localhost:8080/actuator/health` |
| Service A (Gateway 경유) | `GET http://localhost:8080/service-a/actuator/health` |
| Service B (Gateway 경유) | `GET http://localhost:8080/service-b/actuator/health` |
| Eureka 대시보드 | `http://localhost:8761` |