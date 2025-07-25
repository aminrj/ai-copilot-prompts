# Architecture Prompts

System design and high-level planning templates for building scalable, maintainable applications.

---

## System Design

**File: `prompts/03-architecture/system-design.md`**

### 🎯 Purpose

Design complete systems from business requirements with proper architecture considerations.

### 📋 Template

```markdown
Design a complete system for [SYSTEM_NAME]:

## Business Requirements Analysis

### Functional Requirements

**Core Features**:

- [Feature 1]: [Detailed description with acceptance criteria]
- [Feature 2]: [Detailed description with acceptance criteria]
- [Feature 3]: [Detailed description with acceptance criteria]

**User Types and Roles**:

- [User Type 1]: [Permissions and capabilities]
- [User Type 2]: [Permissions and capabilities]
- [Admin Users]: [Administrative capabilities]

**Business Rules**:

- [Rule 1]: [Specific business logic constraint]
- [Rule 2]: [Workflow or process requirement]
- [Rule 3]: [Data validation or compliance rule]

### Non-Functional Requirements

**Performance Requirements**:

- **Users**: [Concurrent users supported]
- **Load**: [Requests per second, data volume]
- **Response Time**: [Latency requirements by operation type]
- **Throughput**: [Transactions per minute/hour]
- **Availability**: [Uptime SLA requirements]

**Scalability Requirements**:

- **Growth Projections**: [User growth, data growth over time]
- **Peak Load**: [Expected peak usage patterns]
- **Geographic Distribution**: [Global/regional deployment needs]
- **Seasonal Patterns**: [Traffic variations throughout year]

**Security Requirements**:

- **Data Sensitivity**: [Classification of data types]
- **Compliance**: [GDPR, HIPAA, SOC2, PCI-DSS requirements]
- **Authentication**: [SSO, MFA, OAuth requirements]
- **Authorization**: [Role-based, attribute-based access control]
- **Audit**: [Logging, monitoring, compliance reporting]

**Integration Requirements**:

- **External Systems**: [Third-party APIs, legacy systems]
- **Data Sources**: [Databases, file systems, APIs to integrate]
- **Real-time Requirements**: [Event streaming, notifications]
- **Batch Processing**: [ETL, reporting, background jobs]

## System Architecture Design

### High-Level Architecture

**Architecture Pattern**: [Monolith, Microservices, Serverless, Hybrid]
**Reasoning**: [Why this pattern fits the requirements]
```

[ASCII Art System Diagram]
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Client │───▶│Load Balancer│───▶│ API GW │
│ Apps │ │ │ │ │
└─────────────┘ └─────────────┘ └─────────────┘
│
┌────────────────────┼────────────────────┐
▼ ▼ ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Service A │ │ Service B │ │ Service C │
│ │ │ │ │ │
└─────────────┘ └─────────────┘ └─────────────┘
│ │ │
└────────────────────┼────────────────────┘
▼
┌─────────────────┐
│ Database │
│ Cluster │
└─────────────────┘

````

### Component Architecture
**Core Components**:

1. **Presentation Layer**
   - **Web Application**: [Frontend technology and architecture]
   - **Mobile Apps**: [Native, hybrid, or PWA approach]
   - **API Documentation**: [Interactive API docs, SDK]

2. **API Gateway Layer**
   - **Request Routing**: [Load balancing, service discovery]
   - **Authentication**: [JWT validation, OAuth integration]
   - **Rate Limiting**: [Per-user, per-endpoint limits]
   - **Monitoring**: [Request logging, metrics collection]

3. **Business Logic Layer**
   - **[Service 1]**: [Specific business capability and responsibilities]
   - **[Service 2]**: [Specific business capability and responsibilities]
   - **[Service 3]**: [Specific business capability and responsibilities]

4. **Data Layer**
   - **Primary Database**: [Technology choice and schema approach]
   - **Caching Layer**: [Redis, Memcached for performance]
   - **Search Engine**: [Elasticsearch, Solr for full-text search]
   - **File Storage**: [Object storage for files and media]

5. **Integration Layer**
   - **Message Queue**: [Async communication between services]
   - **Event Streaming**: [Real-time event processing]
   - **External APIs**: [Third-party service integrations]
   - **Data Pipeline**: [ETL, data synchronization]

### Technology Stack Recommendations

**Frontend Stack**:
- **Framework**: [React, Vue, Angular with reasoning]
- **State Management**: [Redux, Vuex, or context-based]
- **Build Tools**: [Webpack, Vite, or framework defaults]
- **Testing**: [Jest, Cypress, Testing Library]

**Backend Stack**:
- **Runtime**: [Node.js, Python, Java, Go with reasoning]
- **Framework**: [Express, FastAPI, Spring Boot, Gin]
- **Database**: [PostgreSQL, MongoDB, MySQL with reasoning]
- **Caching**: [Redis, Memcached]
- **Message Queue**: [RabbitMQ, Apache Kafka, AWS SQS]

**Infrastructure Stack**:
- **Cloud Provider**: [AWS, GCP, Azure with service selections]
- **Containerization**: [Docker, Kubernetes orchestration]
- **CI/CD**: [GitHub Actions, Jenkins, GitLab CI]
- **Monitoring**: [Prometheus, DataDog, New Relic]

## Data Architecture Design

### Database Design Strategy
**Database Selection Criteria**:
- **Data Consistency**: [ACID requirements, eventual consistency tolerance]
- **Query Patterns**: [Read-heavy, write-heavy, complex queries]
- **Scalability Needs**: [Horizontal vs vertical scaling requirements]
- **Performance Requirements**: [Latency, throughput needs]

**Recommended Database Architecture**:
```sql
-- Primary Database Schema Design
-- [Include key tables with relationships]

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role user_role NOT NULL DEFAULT 'user',
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE [business_entity] (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    -- [Business-specific fields]
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- [Additional tables for core business entities]
````

### Data Flow Architecture

**Data Movement Patterns**:

1. **Request/Response**: [Synchronous API calls for immediate data]
2. **Event-Driven**: [Asynchronous events for state changes]
3. **Batch Processing**: [Scheduled data processing and analytics]
4. **Real-time Streaming**: [Live data updates and notifications]

**Data Consistency Strategy**:

- **Strong Consistency**: [Critical business data requiring ACID properties]
- **Eventual Consistency**: [Data that can tolerate temporary inconsistency]
- **Conflict Resolution**: [Strategies for handling data conflicts]

## Security Architecture

### Security Design Principles

**Authentication Architecture**:

- **Identity Provider**: [Auth0, AWS Cognito, custom JWT implementation]
- **Multi-Factor Authentication**: [TOTP, SMS, biometric options]
- **Session Management**: [JWT tokens, refresh token rotation]
- **Single Sign-On**: [SAML, OAuth, OpenID Connect integration]

**Authorization Model**:

- **Role-Based Access Control (RBAC)**: [Role definitions and permissions]
- **Attribute-Based Access Control (ABAC)**: [Fine-grained permissions]
- **Resource-Level Permissions**: [Object-level access control]

**Data Protection Strategy**:

- **Encryption at Rest**: [Database encryption, file encryption]
- **Encryption in Transit**: [TLS/SSL configuration, API security]
- **Key Management**: [HSM, cloud key management services]
- **Data Masking**: [PII protection in non-production environments]

### Security Controls Implementation

**Application Security**:

- **Input Validation**: [Comprehensive validation at all entry points]
- **Output Encoding**: [XSS prevention, data sanitization]
- **SQL Injection Prevention**: [Parameterized queries, ORM usage]
- **CSRF Protection**: [Token-based protection, SameSite cookies]

**Infrastructure Security**:

- **Network Segmentation**: [VPC design, security groups]
- **Firewall Rules**: [Ingress/egress traffic control]
- **DDoS Protection**: [CDN, rate limiting, traffic filtering]
- **Vulnerability Management**: [Regular scanning, patch management]

## Performance and Scalability Design

### Performance Optimization Strategy

**Caching Strategy**:

- **Application-Level Caching**: [In-memory caches, Redis]
- **Database Query Caching**: [Query result caching]
- **CDN Integration**: [Static asset caching, edge locations]
- **Cache Invalidation**: [Strategies for cache freshness]

**Database Performance**:

- **Indexing Strategy**: [Primary, composite, partial indexes]
- **Query Optimization**: [Execution plan analysis, query tuning]
- **Connection Pooling**: [Optimal pool sizing, connection management]
- **Read Replicas**: [Read scaling, eventual consistency handling]

### Scalability Architecture

**Horizontal Scaling Design**:

- **Load Balancing**: [Algorithm selection, health checks]
- **Service Scaling**: [Auto-scaling policies, metrics-based scaling]
- **Database Scaling**: [Sharding, clustering, federation]
- **Stateless Design**: [Session externalization, shared state management]

**Vertical Scaling Considerations**:

- **Resource Optimization**: [CPU, memory, storage scaling]
- **Performance Monitoring**: [Resource utilization tracking]
- **Capacity Planning**: [Growth projections, resource allocation]

## Deployment and Operations Design

### Infrastructure Architecture

**Cloud Infrastructure Design**:

```yaml
# Infrastructure as Code Example (Terraform/CloudFormation)
# [Include key infrastructure components]

# Load Balancer Configuration
load_balancer:
  type: application
  scheme: internet-facing
  security_groups: [web-sg]
  subnets: [public-subnet-1, public-subnet-2]

# Auto Scaling Group
api_servers:
  min_size: 2
  max_size: 10
  desired_capacity: 3
  health_check_type: ELB
  health_check_grace_period: 300

# Database Configuration
database:
  engine: postgresql
  instance_class: db.r5.xlarge
  multi_az: true
  backup_retention: 7
  encryption: true
```

**Deployment Pipeline**:

1. **Source Control**: [Git workflow, branch protection]
2. **Build Process**: [Automated testing, artifact creation]
3. **Staging Deployment**: [Integration testing, performance testing]
4. **Production Deployment**: [Blue-green, rolling, canary strategies]
5. **Rollback Strategy**: [Automated rollback triggers, manual procedures]

### Monitoring and Observability

**Monitoring Strategy**:

- **Application Metrics**: [Response time, error rate, throughput]
- **Infrastructure Metrics**: [CPU, memory, disk, network]
- **Business Metrics**: [User engagement, conversion rates]
- **Security Metrics**: [Failed logins, suspicious activity]

**Logging Architecture**:

- **Structured Logging**: [JSON format, consistent fields]
- **Log Aggregation**: [Centralized logging system]
- **Log Analysis**: [Search, alerting, dashboards]
- **Retention Policies**: [Compliance-driven retention rules]

**Alerting Framework**:

- **Critical Alerts**: [System down, security breaches]
- **Warning Alerts**: [Performance degradation, resource utilization]
- **Informational Alerts**: [Deployment notifications, scheduled events]

## Implementation Roadmap

### Phase 1: MVP Foundation (Months 1-2)

**Core Infrastructure**:

- [ ] Basic application architecture setup
- [ ] Database schema and core APIs
- [ ] Authentication and basic authorization
- [ ] Essential business logic implementation
- [ ] Basic monitoring and logging

**Success Criteria**:

- [ ] Core user workflows functional
- [ ] Basic security controls in place
- [ ] Performance meets minimum requirements
- [ ] Deployment pipeline operational

### Phase 2: Scale and Polish (Months 3-4)

**Enhanced Features**:

- [ ] Advanced business logic implementation
- [ ] Performance optimization and caching
- [ ] Enhanced security controls
- [ ] Comprehensive monitoring and alerting
- [ ] Load testing and performance validation

**Success Criteria**:

- [ ] System handles projected load
- [ ] Security audit passed
- [ ] Monitoring provides actionable insights
- [ ] User experience polished

### Phase 3: Advanced Capabilities (Months 5-6)

**Advanced Features**:

- [ ] Advanced integrations and APIs
- [ ] Analytics and reporting capabilities
- [ ] Advanced security features
- [ ] Multi-region deployment
- [ ] Disaster recovery implementation

**Success Criteria**:

- [ ] All business requirements implemented
- [ ] High availability achieved
- [ ] Disaster recovery tested
- [ ] Performance exceeds requirements

## Risk Assessment and Mitigation

### Technical Risks

**High-Risk Areas**:

- **Data Loss**: [Backup strategy, replication, disaster recovery]
- **Security Breaches**: [Security controls, monitoring, incident response]
- **Performance Issues**: [Load testing, monitoring, scaling strategy]
- **Integration Failures**: [Circuit breakers, fallback strategies]

### Operational Risks

**Business Continuity**:

- **Service Downtime**: [High availability design, failover procedures]
- **Data Corruption**: [Data validation, backup verification]
- **Compliance Violations**: [Audit controls, policy enforcement]
- **Scalability Bottlenecks**: [Capacity planning, performance monitoring]

### Mitigation Strategies

**Risk Reduction**:

- **Redundancy**: [Multi-AZ deployment, service redundancy]
- **Monitoring**: [Proactive alerting, anomaly detection]
- **Testing**: [Chaos engineering, disaster recovery drills]
- **Documentation**: [Runbooks, incident response procedures]

Provide the complete system design addressing all architectural concerns for this specific system.

````

### 💡 Usage Example

```markdown
Design a complete system for Real-time Collaborative Document Editor:

## Business Requirements Analysis

### Functional Requirements
**Core Features**:
- **Document Creation/Editing**: Users can create, edit, and format text documents with rich text support
- **Real-time Collaboration**: Multiple users can edit same document simultaneously with live cursor positions
- **Version History**: Complete version control with diff visualization and rollback capabilities
- **Sharing and Permissions**: Document sharing with view/edit/comment permissions and expiration dates
- **Comments and Suggestions**: Inline comments, suggestions, and approval workflows
- **Offline Support**: Local editing with sync when connection restored

**User Types and Roles**:
- **Document Owner**: Full control, can delete, manage permissions, export
- **Editor**: Can edit content, add comments, suggest changes
- **Viewer**: Read-only access, can add comments if permitted
- **Anonymous Users**: Limited access to shared documents with links

**Business Rules**:
- **Concurrent Editing**: Operational transformation to resolve conflicts
- **Auto-save**: Changes saved every 2 seconds, no manual save required
- **Document Limits**: Free accounts limited to 10 documents, premium unlimited
- **File Size**: Maximum 50MB per document, 1GB total storage per user

### Non-Functional Requirements
**Performance Requirements**:
- **Users**: 10,000 concurrent active editors across all documents
- **Load**: 100,000 operations per second (text edits, cursor moves)
- **Response Time**: <50ms for edit operations, <100ms for document loading
- **Throughput**: Support 1,000 simultaneous document collaborations
- **Availability**: 99.9% uptime with <5 second failover time

**Scalability Requirements**:
- **Growth Projections**: 10x user growth over 2 years (100k to 1M users)
- **Peak Load**: 5x normal load during business hours (9am-5pm)
- **Geographic Distribution**: Global deployment with <200ms latency worldwide
- **Document Scaling**: Support documents up to 1M words with 50 concurrent editors

**Security Requirements**:
- **Data Sensitivity**: User documents contain confidential business information
- **Compliance**: GDPR for EU users, enterprise SOC2 compliance required
- **Authentication**: SSO integration (Google, Microsoft), optional 2FA
- **Authorization**: Granular document permissions, team-based access control
- **Audit**: Complete edit history, user action logging, export capabilities

**Integration Requirements**:
- **External Systems**: Google Drive, Dropbox, OneDrive for import/export
- **Real-time Requirements**: WebSocket connections for live collaboration
- **File Formats**: Import/export Word, PDF, HTML, Markdown formats
- **API Access**: RESTful API for third-party integrations and mobile apps

## System Architecture Design

### High-Level Architecture
**Architecture Pattern**: Microservices with Event-Driven Architecture
**Reasoning**: Real-time collaboration requires independent scaling of document editing, user management, and file operations. Event-driven design enables real-time updates across services.

````

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ Web Client │ │ Mobile App │ │ Third-party │
│ (React) │───▶│ (React Native │───▶│ API │
└─────────────────┘ │ Flutter) │ │ Clients │
└─────────────────┘ └─────────────────┘
│ │
└───────────┬───────────┘
▼
┌─────────────────┐
│ CDN + WAF │
│ (CloudFlare) │
└─────────────────┘
│
▼
┌─────────────────┐
│ Load Balancer │
│ (AWS ALB) │
└─────────────────┘
│
▼
┌─────────────────┐
│ API Gateway │
│ (Kong/AWS) │
└─────────────────┘
│
┌───────────────────────┼───────────────────────┐
▼ ▼ ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ Auth Service │ │Document Service │ │ User Service │
│ (Node.js) │ │ (Node.js) │ │ (Node.js) │
└─────────────────┘ └─────────────────┘ └─────────────────┘
│ │ │
└───────────────────────┼───────────────────────┘
│
┌─────────────────┼─────────────────┐
▼ ▼ ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ Collaboration │ │ File Service │ │Notification Svc │
│ Service │ │ (Node.js) │ │ (Node.js) │
│ (Node.js) │ └─────────────────┘ └─────────────────┘
└─────────────────┘ │ │
│ ▼ │
│ ┌─────────────────┐ │
│ │ File Storage │ │
│ │ (AWS S3) │ │
│ └─────────────────┘ │
│ │
└─────────────────┬─────────────────────────┘
▼
┌─────────────────┐
│Event Streaming │
│ (Apache Kafka) │
└─────────────────┘
│
┌─────────────────┼─────────────────┐
▼ ▼ ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ PostgreSQL │ │ Redis │ │ Elasticsearch │
│ (Primary) │ │ (Cache + │ │ (Search + │
│ │ │ Sessions) │ │ Analytics) │
└─────────────────┘ └─────────────────┘ └─────────────────┘

````

### Component Architecture
**Core Components**:

1. **Presentation Layer**
   - **Web Application**: React with TypeScript, real-time editing with Quill.js/TinyMCE
   - **Mobile Apps**: React Native for cross-platform, offline-first architecture
   - **API Documentation**: OpenAPI spec with interactive docs, WebSocket API docs

2. **API Gateway Layer**
   - **Request Routing**: Kong API Gateway with service discovery
   - **Authentication**: JWT validation, OAuth2 integration with external providers
   - **Rate Limiting**: 1000 requests/minute per user, 10,000 ops/minute for editing
   - **WebSocket Proxy**: Real-time connection management and load balancing

3. **Business Logic Layer**
   - **Document Service**: Document CRUD, operational transformation engine
   - **Collaboration Service**: Real-time editing coordination, conflict resolution
   - **User Service**: User management, team organization, permissions
   - **Auth Service**: Authentication, authorization, SSO integration
   - **File Service**: Import/export, format conversion, file storage management
   - **Notification Service**: Real-time notifications, email alerts, webhooks

4. **Data Layer**
   - **Primary Database**: PostgreSQL for documents, users, permissions
   - **Cache Layer**: Redis for sessions, document locks, real-time state
   - **Search Engine**: Elasticsearch for document search, analytics
   - **File Storage**: AWS S3 for document exports, file attachments, backups

5. **Integration Layer**
   - **Event Streaming**: Kafka for real-time collaboration events
   - **Message Queue**: RabbitMQ for background jobs, file processing
   - **External APIs**: Google Drive, Dropbox, Office 365 integrations
   - **WebSocket Manager**: Socket.io for real-time client connections

### Technology Stack Recommendations

**Frontend Stack**:
- **Framework**: React with TypeScript for type safety and better collaboration
- **Real-time Editing**: Quill.js with custom operational transformation
- **State Management**: Redux Toolkit with RTK Query for API management
- **Real-time Connection**: Socket.io client with reconnection logic
- **Testing**: Jest, React Testing Library, Cypress for E2E

**Backend Stack**:
- **Runtime**: Node.js for consistent JavaScript across stack, excellent WebSocket support
- **Framework**: Express.js with TypeScript, Socket.io for real-time features
- **Database**: PostgreSQL for ACID compliance, complex queries, JSON support
- **Caching**: Redis for session management, real-time state, document locks
- **Message Streaming**: Apache Kafka for scalable event streaming

**Infrastructure Stack**:
- **Cloud Provider**: AWS for global reach, managed services, enterprise compliance
- **Containerization**: Docker with Kubernetes for orchestration and scaling
- **CI/CD**: GitHub Actions with automated testing, security scanning
- **Monitoring**: DataDog for APM, Prometheus for metrics, ELK for logging

## Data Architecture Design

### Database Design Strategy
**Database Selection Criteria**:
- **Strong Consistency**: Document integrity critical, ACID properties required
- **Complex Queries**: Advanced permission queries, full-text search needs
- **JSON Support**: Document content stored as structured JSON with metadata
- **Horizontal Scaling**: Read replicas for global distribution

**Recommended Database Architecture**:
```sql
-- Document-centric schema with collaboration support

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    name VARCHAR(255) NOT NULL,
    avatar_url VARCHAR(500),
    subscription_type VARCHAR(50) DEFAULT 'free',
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE documents (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(500) NOT NULL,
    content JSONB NOT NULL DEFAULT '{"ops":[]}', -- Quill Delta format
    owner_id UUID REFERENCES users(id) ON DELETE CASCADE,
    version INTEGER DEFAULT 1,
    is_public BOOLEAN DEFAULT false,
    last_edited_at TIMESTAMP DEFAULT NOW(),
    created_at TIMESTAMP DEFAULT NOW(),

    -- Full-text search
    content_text TEXT GENERATED ALWAYS AS (
        content ->> 'text'
    ) STORED
);

CREATE TABLE document_permissions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    document_id UUID REFERENCES documents(id) ON DELETE CASCADE,
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    permission_type VARCHAR(20) CHECK (permission_type IN ('view', 'comment', 'edit', 'admin')),
    granted_by UUID REFERENCES users(id),
    expires_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT NOW(),

    UNIQUE(document_id, user_id)
);

CREATE TABLE document_versions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    document_id UUID REFERENCES documents(id) ON DELETE CASCADE,
    version INTEGER NOT NULL,
    content JSONB NOT NULL,
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMP DEFAULT NOW(),

    UNIQUE(document_id, version)
);

CREATE TABLE collaboration_sessions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    document_id UUID REFERENCES documents(id) ON DELETE CASCADE,
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    cursor_position INTEGER DEFAULT 0,
    last_seen TIMESTAMP DEFAULT NOW(),
    is_active BOOLEAN DEFAULT true,

    UNIQUE(document_id, user_id)
);

CREATE TABLE operations_log (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    document_id UUID REFERENCES documents(id) ON DELETE CASCADE,
    user_id UUID REFERENCES users(id),
    operation JSONB NOT NULL, -- Operational transformation delta
    operation_sequence BIGSERIAL,
    applied_at TIMESTAMP DEFAULT NOW()
);

-- Indexes for performance
CREATE INDEX idx_documents_owner ON documents(owner_id);
CREATE INDEX idx_documents_updated ON documents(last_edited_at DESC);
CREATE INDEX idx_doc_permissions_doc ON document_permissions(document_id);
CREATE INDEX idx_doc_permissions_user ON document_permissions(user_id);
CREATE INDEX idx_operations_doc_seq ON operations_log(document_id, operation_sequence);
CREATE INDEX idx_content_search ON documents USING gin(to_tsvector('english', content_text));
````

### Data Flow Architecture

**Real-time Collaboration Flow**:

1. **User Edit Operation**: Client sends operation via WebSocket
2. **Operational Transform**: Server applies transformation algorithm
3. **Persistence**: Operation logged to database with sequence number
4. **Broadcast**: Transformed operation sent to all connected collaborators
5. **Client Application**: Clients apply operation to local document state

**Data Consistency Strategy**:

- **Strong Consistency**: Document content and permissions require immediate consistency
- **Eventual Consistency**: User presence, cursor positions can tolerate brief delays
- **Conflict Resolution**: Operational transformation ensures deterministic conflict resolution

## Security Architecture

### Authentication Architecture

**Identity Management**:

- **Primary Authentication**: Email/password with bcrypt hashing (cost factor 12)
- **OAuth Integration**: Google, Microsoft, GitHub OAuth2 flows
- **Session Management**: JWT access tokens (15min) + refresh tokens (30 days)
- **Multi-Factor Authentication**: TOTP-based 2FA for premium accounts

**Authorization Model**:

- **Document-Level Permissions**: Owner, Editor, Viewer, Commenter roles
- **Team-Based Access**: Organizational teams with inherited permissions
- **Time-Based Access**: Expiring document shares with link-based access
- **API Key Management**: Service-to-service authentication for integrations

### Security Controls Implementation

**Application Security**:

- **Input Validation**: Comprehensive validation on all document operations
- **XSS Prevention**: Content sanitization, CSP headers, output encoding
- **CSRF Protection**: SameSite cookies, anti-CSRF tokens for state changes
- **Rate Limiting**: Operation-level rate limits, IP-based abuse prevention

**Data Protection**:

- **Encryption at Rest**: AES-256 encryption for documents, user data
- **Encryption in Transit**: TLS 1.3 for all connections, certificate pinning
- **Key Management**: AWS KMS for encryption key rotation and management
- **Data Anonymization**: Personal data pseudonymization for analytics

Provide the complete collaborative document editor system design with all architectural components.

```

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐
- **Time Saved**: 8-16 hours of architecture planning
- **Quality Improvement**: Comprehensive vs ad-hoc system design
- **Use Cases**: New system design, architecture reviews, system modernization
```
