# Foundation Prompts

The essential techniques that work with any AI copilot. Master these first before moving to advanced techniques.

---

## Context Loading

**File: `prompts/01-foundation/context-loading.md`**

### 🎯 Purpose

Provide complete context to AI for production-ready code generation instead of generic solutions.

### 📋 Template

```markdown
Context for [FEATURE_NAME]:

## Project Information

- **Tech Stack**: [FRONTEND] + [BACKEND] + [DATABASE]
- **Architecture**: [Monolith/Microservices/Serverless]
- **Scale**: [Users/Requests/Data volume]
- **Team Size**: [Number] developers
- **Timeline**: [Deadline constraints]

## Technical Context

- **Existing Patterns**: See [REFERENCE_FILES]
- **Dependencies**: [External services/APIs]
- **Constraints**: [Performance/Security/Compliance requirements]
- **Integration Points**: [Systems this connects to]

## Business Context

- **User Type**: [Who uses this feature]
- **Success Criteria**: [How success is measured]
- **Edge Cases**: [Known problem scenarios]
- **Compliance**: [GDPR/HIPAA/SOX requirements]

## Implementation Requirements

**Task**: [Specific implementation request]

**Must Include**:

- Comprehensive error handling
- Security best practices
- Performance optimization
- Complete test coverage
- Documentation
- Deployment considerations

**Think through**:

- What could go wrong?
- How does this scale?
- What are the security implications?
- How do we test this thoroughly?
- How do we monitor this in production?

Provide production-ready implementation with architecture rationale.
```

### 💡 Usage Example

```markdown
Context for User Authentication System:

## Project Information

- **Tech Stack**: React + Node.js + PostgreSQL
- **Architecture**: Microservices with API Gateway
- **Scale**: 100k users, 1M requests/day
- **Team Size**: 8 developers
- **Timeline**: 3 weeks to MVP

## Technical Context

- **Existing Patterns**: See /src/services/UserService.js for patterns
- **Dependencies**: Redis for sessions, SendGrid for emails
- **Constraints**: <100ms response time, GDPR compliant
- **Integration Points**: Payment service, Notification service

## Business Context

- **User Type**: B2B SaaS customers (companies)
- **Success Criteria**: <2% authentication failure rate
- **Edge Cases**: Password resets, account lockouts, concurrent sessions
- **Compliance**: GDPR data handling, SOC2 audit requirements

## Implementation Requirements

**Task**: Implement complete JWT-based authentication with refresh tokens

**Must Include**:

- Password hashing with bcrypt
- Rate limiting on auth endpoints
- Session management with Redis
- Email verification flow
- Password reset functionality
- Account lockout after failed attempts
- GDPR-compliant data handling
- Comprehensive audit logging

**Think through**:

- Brute force attack prevention
- Token rotation and revocation
- Cross-device session management
- Recovery flows for edge cases
- Monitoring and alerting strategy

Provide production-ready implementation with security best practices.
```

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐

- **Time Saved**: 4-6 hours
- **Quality Improvement**: Production-ready vs prototype code
- **Use Cases**: Any feature development

---

## Think Step by Step

**File: `prompts/01-foundation/think-step-by-step.md`**

### 🎯 Purpose

Activate AI's deeper reasoning capabilities for complex problem-solving and architecture decisions.

### 📋 Template

```markdown
Think step by step about [PROBLEM/TASK]:

## Analysis Phase

1. **Problem Understanding**

   - What exactly are we trying to solve?
   - What are the core requirements vs nice-to-haves?
   - What constraints do we need to work within?

2. **Architecture Considerations**

   - How does this fit into the existing system?
   - What are the scalability implications?
   - What are potential failure points?

3. **Security Implications**

   - What data are we handling?
   - What attack vectors should we consider?
   - What compliance requirements apply?

4. **Performance Requirements**

   - What are the latency expectations?
   - How much load should this handle?
   - What are the resource constraints?

5. **Integration Challenges**

   - What external systems are involved?
   - How do we handle external service failures?
   - What data consistency requirements exist?

6. **Operational Concerns**
   - How do we monitor this?
   - How do we deploy and rollback?
   - How do we troubleshoot issues?

## Implementation Strategy

Based on the analysis above:

1. **Design the solution architecture**
2. **Identify the critical path and dependencies**
3. **Plan the implementation phases**
4. **Define testing strategy**
5. **Create monitoring and alerting plan**

## Execution

Now implement the solution addressing all considerations above:

[Your specific implementation request]
```

### 💡 Usage Example

```markdown
Think step by step about implementing a real-time notification system:

## Analysis Phase

1. **Problem Understanding**

   - Need to notify users instantly about order updates, messages, system alerts
   - Must work across web, mobile, and email channels
   - Should handle 50k concurrent users
   - Must be reliable (99.9% delivery rate)

2. **Architecture Considerations**

   - WebSocket connections for real-time delivery
   - Message queue for reliability and scale
   - Database for notification history and preferences
   - CDN for global delivery optimization

3. **Security Implications**

   - User authentication for WebSocket connections
   - Message content encryption for sensitive data
   - Rate limiting to prevent spam/abuse
   - Audit logging for compliance

4. **Performance Requirements**

   - <100ms notification delivery time
   - Support for 50k concurrent WebSocket connections
   - 1M notifications per hour processing capacity
   - Graceful degradation under load

5. **Integration Challenges**

   - Integration with existing user service
   - Email service (SendGrid) for fallback delivery
   - Push notification services (FCM, APNS)
   - Analytics service for delivery tracking

6. **Operational Concerns**
   - Connection monitoring and health checks
   - Message delivery tracking and retry logic
   - Scaling WebSocket servers horizontally
   - Dead letter queue for failed notifications

## Implementation Strategy

Based on the analysis above:

1. **Design WebSocket service with Redis pub/sub**
2. **Implement message queue with priority handling**
3. **Create notification preferences system**
4. **Build fallback delivery mechanisms**
5. **Set up comprehensive monitoring**

## Execution

Now implement a production-ready real-time notification system with:

- WebSocket server with Redis clustering
- Message queue with retry logic
- Multi-channel delivery (WebSocket, email, push)
- User preference management
- Delivery tracking and analytics
- Comprehensive error handling and fallbacks
```

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐

- **Time Saved**: 3-5 hours of planning
- **Quality Improvement**: Comprehensive vs superficial solutions
- **Use Cases**: Complex features, system design, architecture decisions

---

## Error-First Development

**File: `prompts/01-foundation/error-first-development.md`**

### 🎯 Purpose

Build robust, production-ready code by considering failure scenarios upfront.

### 📋 Template

````markdown
Implement [FEATURE] with comprehensive error handling:

## Failure Scenario Analysis

Consider what happens when:

### External Dependencies Fail

- **Database connection**: Lost, slow, or corrupted
- **API services**: Down, slow, rate-limited, or returning errors
- **File systems**: Full, permissions denied, or corrupted
- **Network**: Partitions, timeouts, or DNS failures
- **Cache systems**: Unavailable or returning stale data

### Resource Constraints

- **Memory**: Out of memory or memory leaks
- **CPU**: High load or processing timeouts
- **Disk**: Full storage or I/O errors
- **Bandwidth**: Network congestion or limits

### Input Validation Failures

- **Malformed data**: Invalid JSON, wrong types, missing fields
- **Malicious input**: SQL injection, XSS, command injection
- **Size limits**: Too large payloads or too many requests
- **Business rule violations**: Invalid states or constraint violations

### Concurrency Issues

- **Race conditions**: Multiple users modifying same data
- **Deadlocks**: Resource contention between processes
- **Atomic operations**: Partial failures in multi-step operations
- **State consistency**: Distributed system consistency issues

### Security Scenarios

- **Authentication failures**: Invalid tokens, expired sessions
- **Authorization failures**: Insufficient permissions, privilege escalation
- **Data breaches**: Unauthorized access attempts
- **Audit requirements**: Logging failures or compliance violations

## Error Handling Strategy

For each failure scenario above:

1. **Detection**: How do we identify the failure?
2. **Isolation**: How do we prevent cascade failures?
3. **Recovery**: What's our automatic recovery strategy?
4. **Fallback**: What's our graceful degradation approach?
5. **Alerting**: How do we notify operations teams?
6. **User Experience**: How do we communicate to users?

## Implementation Requirements

**Core Feature**: [Your implementation request]

**Must Include**:

- Input validation with detailed error messages
- Retry logic with exponential backoff
- Circuit breaker pattern for external services
- Graceful degradation when dependencies fail
- Comprehensive logging for debugging
- Health checks and monitoring endpoints
- Rollback capabilities for failed operations
- User-friendly error messages
- Security event logging
- Performance monitoring under failure conditions

**Error Response Format**:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "User-friendly error message",
    "details": "Technical details for debugging",
    "timestamp": "2025-01-01T12:00:00Z",
    "request_id": "req_123456",
    "retry_after": 300
  }
}
```
````

Build the implementation that handles ALL failure scenarios gracefully.

````

### 💡 Usage Example

```markdown
Implement payment processing with comprehensive error handling:

## Failure Scenario Analysis
Consider what happens when:

### External Dependencies Fail
- **Stripe API**: Down, rate-limited, webhook delays, or payment failures
- **Database**: Connection lost during transaction, deadlocks
- **Email service**: SendGrid down, bounce rates, delivery delays
- **Fraud detection**: Service timeout, false positives/negatives

### Resource Constraints
- **High transaction volume**: Payment queue backlog, processing delays
- **Memory pressure**: Large payment batch processing
- **Network issues**: Stripe webhook delivery failures

### Input Validation Failures
- **Invalid payment data**: Wrong card numbers, expired cards, insufficient funds
- **Malicious attempts**: Carding attacks, payment fraud attempts
- **Currency mismatches**: Wrong currency codes, conversion failures

### Concurrency Issues
- **Double charges**: User clicking payment button multiple times
- **Inventory conflicts**: Product sold out during payment processing
- **Account balance**: Insufficient funds check race conditions

### Security Scenarios
- **PCI compliance**: Data handling violations, logging sensitive data
- **Fraud detection**: Suspicious patterns, stolen card usage
- **Chargeback scenarios**: Disputed transactions, refund processing

## Error Handling Strategy

1. **Payment Idempotency**: Use idempotency keys to prevent double charges
2. **Retry Logic**: Exponential backoff for transient Stripe errors
3. **Circuit Breaker**: Disable payment processing if Stripe is consistently failing
4. **Graceful Degradation**: Queue payments for later processing if possible
5. **Real-time Monitoring**: Alert on payment failure rate spikes
6. **Customer Communication**: Clear error messages without exposing technical details

## Implementation Requirements

**Core Feature**: Process credit card payments with Stripe integration

**Must Include**:
- Idempotency key generation and validation
- PCI-compliant data handling (no card storage)
- Comprehensive input validation
- Retry logic for network failures
- Payment status tracking and reconciliation
- Fraud detection integration
- Webhook signature verification
- Database transaction atomicity
- Detailed audit logging (without sensitive data)
- Customer notification on success/failure
- Refund and chargeback handling
- Real-time payment monitoring
- Graceful error messages for users

Build a production-ready payment system that handles ALL failure scenarios while maintaining PCI compliance and excellent user experience.
````

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐

- **Time Saved**: 2-4 hours of edge case handling
- **Quality Improvement**: Production-ready vs development-only code
- **Use Cases**: Any feature that handles user data or external APIs
