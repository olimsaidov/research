# System Architecture Diagram

## Overview
This diagram illustrates the comprehensive system architecture of the E-Jarima platform, showing how different components interact to create a scalable civic technology solution for traffic violation reporting.

## Architecture Diagram

```mermaid
graph TB
    subgraph "User Layer"
        C[Citizens<br/>Mobile/Web]
        S[Staff/Inspectors<br/>Web Portal]
        A[Administrators<br/>Admin Panel]
        TP[Third-party Apps<br/>via API]
    end

    subgraph "API Gateway Layer"
        AG[API Gateway<br/>- Authentication<br/>- Rate Limiting<br/>- Request Routing]
        OAuth[OAuth2 Server<br/>- Authorization Code<br/>- Client Credentials<br/>- Token Management]
    end

    subgraph "Application Layer"
        subgraph "Core Services"
            WA[Web Application<br/>Clojure/Luminus]
            RS[Report Service]
            VS[Violation Service]
            US[User Service]
            PS[Payment Service]
            NS[Notification Service]
        end
        
        subgraph "Background Workers"
            ET[Encoder Ticker<br/>60s interval]
            DT[Detector Ticker<br/>100s interval]
            WT[Webhook Ticker<br/>60s interval]
            TB[Telegram Bot]
        end
    end

    subgraph "Microservices Layer"
        ES[Encoder Service<br/>Video Transcoding]
        DS[Detector Service<br/>AI Detection]
    end

    subgraph "Data Layer"
        PG[(PostgreSQL<br/>- User Data<br/>- Reports<br/>- Violations<br/>- Transactions)]
        Redis[(Redis<br/>- Sessions<br/>- Cache<br/>- Temp Data)]
        MinIO[(MinIO Clusters<br/>- Videos<br/>- Images<br/>- Documents)]
    end

    subgraph "External Services"
        ASBT[ASBT<br/>Government System]
        Kash[Kash Gateway<br/>Phone Credits]
        UzCard[UzCard<br/>Bank Transfers]
        SMS[SMS Provider]
    end

    %% User connections
    C --> AG
    S --> AG
    A --> AG
    TP --> OAuth
    OAuth --> AG

    %% API Gateway to services
    AG --> WA
    AG --> RS
    AG --> VS
    AG --> US
    AG --> PS
    AG --> NS

    %% Service to data layer
    WA --> PG
    WA --> Redis
    RS --> PG
    RS --> MinIO
    VS --> PG
    US --> PG
    PS --> PG
    NS --> PG

    %% Background workers
    ET --> ES
    ET --> MinIO
    DT --> DS
    DT --> MinIO
    WT --> PG
    TB --> NS

    %% Microservices connections
    ES --> MinIO
    DS --> MinIO
    RS --> ES
    RS --> DS

    %% External service connections
    VS --> ASBT
    PS --> Kash
    PS --> UzCard
    NS --> SMS
    NS --> TB

    %% Data flow styling
    classDef userLayer fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef apiLayer fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef appLayer fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
    classDef dataLayer fill:#fff3e0,stroke:#e65100,stroke-width:2px
    classDef externalLayer fill:#fce4ec,stroke:#880e4f,stroke-width:2px
    classDef microLayer fill:#f1f8e9,stroke:#33691e,stroke-width:2px

    class C,S,A,TP userLayer
    class AG,OAuth apiLayer
    class WA,RS,VS,US,PS,NS,ET,DT,WT,TB appLayer
    class PG,Redis,MinIO dataLayer
    class ASBT,Kash,UzCard,SMS externalLayer
    class ES,DS microLayer
```

## Component Description

### User Layer
- **Citizens**: Primary users who report violations via web or mobile
- **Staff/Inspectors**: Government employees who review and process violations
- **Administrators**: System administrators managing users and configuration
- **Third-party Apps**: External applications accessing the platform via OAuth2 APIs

### API Gateway Layer
- **API Gateway**: Central entry point handling authentication, rate limiting, and routing
- **OAuth2 Server**: Manages authorization for third-party applications with multiple grant types

### Application Layer
#### Core Services
- **Web Application**: Main Clojure/Luminus monolith handling business logic
- **Report Service**: Manages violation reports from submission to resolution
- **Violation Service**: Processes individual violations within reports
- **User Service**: Handles user management and authentication
- **Payment Service**: Manages rewards and payment processing
- **Notification Service**: Sends alerts via SMS, email, and Telegram

#### Background Workers
- **Encoder Ticker**: Processes video encoding queue every 60 seconds
- **Detector Ticker**: Manages AI detection queue every 100 seconds
- **Webhook Ticker**: Delivers webhook notifications to OAuth clients
- **Telegram Bot**: Handles Telegram messaging and notifications

### Microservices Layer
- **Encoder Service**: External service for video transcoding and standardization
- **Detector Service**: AI-powered service for violation detection and license plate recognition

### Data Layer
- **PostgreSQL**: Primary database for all transactional data
- **Redis**: Session storage and caching layer
- **MinIO**: Distributed object storage for videos and images

### External Services
- **ASBT**: Government traffic violation system integration
- **Kash Gateway**: Payment provider for phone credit top-ups
- **UzCard**: National payment system for bank card transfers
- **SMS Provider**: SMS notification delivery

## Key Architectural Decisions

1. **Hybrid Architecture**: Core business logic in monolith with CPU-intensive tasks as microservices
2. **Queue-Based Processing**: Asynchronous processing for scalability
3. **Multi-Storage Strategy**: PostgreSQL for data, Redis for cache, MinIO for objects
4. **Service Isolation**: External services wrapped with circuit breakers
5. **Horizontal Scalability**: Stateless design enabling easy scaling

## Performance Characteristics

- **Request Handling**: 10,000+ requests/minute capacity
- **Video Processing**: 30-second average processing time
- **Payment Processing**: 100,000+ transactions/day capability
- **Storage**: Multi-terabyte video storage across CDNs
- **Availability**: 99.9% uptime achieved

## Security Features

- **Multi-layer Authentication**: Session, OAuth2, API keys, 2FA
- **Role-Based Access Control**: Granular permissions per user type
- **Data Encryption**: At-rest and in-transit encryption
- **Audit Logging**: Complete trail of all operations
- **API Security**: Rate limiting, CORS, input validation
