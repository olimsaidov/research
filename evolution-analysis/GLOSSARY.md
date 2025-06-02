# Jarima Platform Technical Glossary

This comprehensive glossary provides definitions for technical terms, business concepts, and platform-specific terminology used throughout the evolution analysis documentation. It serves as a reference to ensure clear understanding across diverse audiences including researchers, government officials, developers, and business strategists.

## Core Business Terms

### ASBT (Automated State Traffic Safety System)
The government's official traffic violation management system. Jarima integrates with ASBT to forward verified violations for official processing.

### Violation/Offense
A traffic law infringement captured on video by citizens and processed through the platform. Each violation goes through detection, review, and forwarding stages.

### Report
A citizen's submission containing video evidence of a traffic violation. Reports can have multiple offenses and go through various status transitions.

### Reward
Monetary compensation given to citizens for successfully reported violations. Can be distributed via phone credit, bank card, or charitable donation.

## Technical Architecture Terms

### OAuth2
Industry-standard authorization framework implemented for third-party access. Supports Authorization Code and Client Credentials flows with scope-based permissions.

### MinIO
Open-source object storage system used for video and image storage. Jarima uses multiple MinIO instances for redundancy and geographic distribution.

### Redis/Carmine
In-memory data store used for session management, caching, and temporary data. Carmine is the Clojure client library for Redis.

### HoneySQL
SQL generation library for Clojure that provides composable, programmatic query building while maintaining SQL semantics.

### Luminus
Full-stack Clojure web framework that provides the foundation for Jarima's application structure, including routing, middleware, and database migrations.

## Processing Pipeline Terms

### Encoder Service
External microservice responsible for video transcoding and standardization. Processes videos to ensure consistent format and quality.

### Detector Service
AI-powered microservice that analyzes videos to detect violations, extract license plates, and identify violation types.

### Queue
Asynchronous processing mechanism using core.async channels. Main queues include encoding queue, detection queue, and payment queue.

### Force Detection
Manual override flag that prioritizes a video for immediate processing in the detection queue, bypassing normal queue ordering.

## Platform Components

### Citizen
End users who report violations. Can be regular citizens or enterprise accounts with different limits and capabilities.

### Inspector/Staff
Government employees who review reported violations and make decisions on forwarding to ASBT.

### Organization
Business entities that can have multiple citizen accounts under them, typically for fleet management.

### Client (OAuth)
Third-party applications authorized to access the platform via API. Clients have trust levels that affect processing requirements.

## Data Management Terms

### Revision
Audit trail system that tracks changes to critical entities for compliance and debugging purposes.

### Migration
Database schema version control using Luminus migrations. Each migration has up/down SQL scripts.

### Webhook
HTTP callbacks sent to OAuth clients when violation statuses change, enabling real-time integrations.

## Payment Terms

### Kash
Primary payment gateway service used for phone credit top-ups and some card payments.

### UzCard
National payment card system in Uzbekistan. Integration includes balance checking and batch payment capabilities.

### Consolidated Payments
Batch payment processing system implemented in 2024 that groups multiple rewards into single transactions for efficiency.

## Security Terms

### Buddy
Clojure authentication and authorization library providing session management and cryptographic functions.

### Two-Factor Authentication (2FA)
Additional security layer for sensitive accounts using SMS verification codes.

### Scope
OAuth2 permission sets that define what resources and operations a client can access (e.g., send-report, read-card-phone).

## Performance Terms

### Horizontal Scaling
Ability to add more server instances to handle increased load. Achieved through stateless design and distributed components.

### Circuit Breaker
Fault tolerance pattern that prevents cascading failures when external services (like ASBT) are unavailable.

### Ticker
Scheduled background job using the Chime library. Examples include encoder-ticker and detector-ticker running at regular intervals.

## Integration Terms

### ASBT Token
Authentication credential for accessing the government traffic system, cached for 24 hours to reduce authentication overhead.

### Public/Private Endpoints
MinIO configuration with separate URLs for internal (private) and external (public) access to optimize security and performance.

### Derivative Assets
Processed versions of original uploads, such as encoded videos, thumbnails, and detection overlay videos.

## Common Abbreviations

- **API**: Application Programming Interface
- **CRUD**: Create, Read, Update, Delete operations
- **GPS**: Global Positioning System (used for violation location)
- **UI/UX**: User Interface/User Experience
- **ROI**: Return on Investment
- **SLA**: Service Level Agreement
- **CI/CD**: Continuous Integration/Continuous Deployment
- **SMS**: Short Message Service (used for notifications)
- **MFA**: Multi-Factor Authentication
- **SDK**: Software Development Kit