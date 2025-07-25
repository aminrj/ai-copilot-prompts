# Advanced AI Prompts

Expert-level prompting strategies and "Dark Arts" techniques for complex scenarios.

---

## Time Traveler Technique

**File: `prompts/04-advanced/time-traveler.md`**

### 🎯 Purpose

Future-proof your code by thinking from a future developer's perspective with evolved best practices.

### 📋 Template

````markdown
You're a senior developer from [FUTURE_YEAR] reviewing this [CURRENT_YEAR] code:

## Future Context Setting

**Your Background**: You're a [ROLE] in [FUTURE_YEAR] who has seen how technology and best practices evolved over [TIME_PERIOD]. You've dealt with legacy systems from the [CURRENT_YEAR] era and understand their common pitfalls.

**Technology Evolution Context**:

- What major technology shifts happened between [CURRENT_YEAR] and [FUTURE_YEAR]?
- What security threats emerged that weren't obvious in [CURRENT_YEAR]?
- What performance bottlenecks became critical as scale increased?
- What architectural patterns proved unsustainable at enterprise scale?
- What compliance and privacy regulations shaped development practices?

## Code Analysis from Future Perspective

### Current Code to Review:

```[LANGUAGE]
[PASTE_YOUR_CODE_HERE]
```
````

### Future-Retrospective Analysis

#### 1. Outdated Patterns Detection

**What patterns in this code became obsolete by [FUTURE_YEAR]?**

- [Pattern 1]: Why it became problematic and what replaced it
- [Pattern 2]: Long-term maintenance issues it caused
- [Pattern 3]: Security vulnerabilities it introduced over time

#### 2. Hidden Time Bombs

**What aspects of this code caused major issues in production systems by [FUTURE_YEAR]?**

- **Scalability Issues**: What breaks when traffic grows 100x?
- **Security Vulnerabilities**: What attack vectors emerged that exploit this pattern?
- **Performance Degradation**: What becomes slow as data grows or complexity increases?
- **Maintenance Nightmares**: What made this code expensive to modify or debug?

#### 3. Evolution Resistance Analysis

**How well does this code adapt to future changes?**

- **API Evolution**: How does this handle backward compatibility as APIs change?
- **Data Model Changes**: How resistant is this to schema evolution?
- **Technology Migration**: How easy is it to migrate to new frameworks/platforms?
- **Team Scaling**: How does this code work when team grows from 5 to 50 developers?

#### 4. Future Compliance Issues

**What regulatory or compliance issues emerged that this code violates?**

- **Privacy Laws**: GDPR, CCPA, and future privacy regulations
- **AI Governance**: Regulations around AI/ML model transparency and bias
- **Data Sovereignty**: Cross-border data transfer restrictions
- **Accessibility**: Web accessibility standards evolution

## Future-Informed Recommendations

### Immediate Modernization (Based on [FUTURE_YEAR] Standards)

**Code Improvements to Implement Now**:

1. **[Improvement 1]**: [Specific change with future justification]
2. **[Improvement 2]**: [Architecture change preventing future problems]
3. **[Improvement 3]**: [Security enhancement based on future threat landscape]

### Future-Proofing Strategies

**Design Changes for Long-term Sustainability**:

- **Modularity**: How to structure code for easier future migration
- **Abstraction Layers**: What interfaces will remain stable over time
- **Configuration**: What should be externalized for future flexibility
- **Monitoring**: What metrics became critical for [FUTURE_YEAR] operations

### Modern Implementation

**Rewrite this code using [FUTURE_YEAR] best practices**:

```[LANGUAGE]
// Future-proofed version of the code
// Include:
// - Evolved patterns that proved sustainable
// - Security practices that prevented future vulnerabilities
// - Performance optimizations that handled scale
// - Maintainability improvements that helped large teams
```

### Technology Roadmap

**Suggest migration path from current state to future-ready architecture**:

1. **Phase 1 (Months 1-3)**: Immediate improvements with current tech stack
2. **Phase 2 (Months 4-8)**: Technology migration to future-stable platforms
3. **Phase 3 (Months 9-12)**: Advanced features leveraging [FUTURE_YEAR] capabilities

Provide the future-informed analysis and modernized implementation.

````

### 💡 Usage Example

```markdown
You're a senior developer from 2030 reviewing this 2025 authentication code:

## Future Context Setting
**Your Background**: You're a Principal Security Engineer in 2030 who has seen how authentication evolved over 5 years. You've dealt with legacy auth systems from the 2025 era and understand their critical vulnerabilities.

**Technology Evolution Context**:
- Passwordless authentication became the standard by 2027
- Quantum-resistant cryptography became mandatory for enterprise systems by 2029
- AI-powered attack vectors required new defense mechanisms
- Privacy regulations expanded to require zero-knowledge authentication
- Biometric authentication matured with privacy-preserving techniques

## Code Analysis from Future Perspective

### Current Code to Review:
```javascript
// 2025 JWT-based authentication
const jwt = require('jsonwebtoken');
const bcrypt = require('bcrypt');

class AuthService {
  async authenticate(email, password) {
    const user = await User.findOne({ email });
    if (!user || !await bcrypt.compare(password, user.password)) {
      throw new Error('Invalid credentials');
    }

    const token = jwt.sign(
      { userId: user.id, role: user.role },
      process.env.JWT_SECRET,
      { expiresIn: '24h' }
    );

    return { token, user: { id: user.id, email: user.email } };
  }

  async verifyToken(token) {
    return jwt.verify(token, process.env.JWT_SECRET);
  }
}
````

### Future-Retrospective Analysis

#### 1. Outdated Patterns Detection

**What patterns became obsolete by 2030?**

- **Password-based authentication**: Replaced by WebAuthn/FIDO2 standard, passwords became liability
- **Long-lived JWT tokens**: 24-hour tokens became major security risk after 2026 token theft incidents
- **Centralized secret management**: Single JWT_SECRET became single point of failure
- **Plain user ID exposure**: Privacy regulations required pseudonymous identifiers

#### 2. Hidden Time Bombs

**Critical issues that emerged in production systems by 2030:**

- **JWT Secret Rotation**: No key rotation strategy led to permanent compromises
- **Token Revocation**: Cannot revoke JWTs before expiration, major incident response gap
- **Quantum Vulnerability**: JWT algorithm (RS256) vulnerable to quantum computers by 2029
- **Privacy Leakage**: User ID in token payload violated GDPR-successor regulations
- **Replay Attacks**: No nonce or timestamp validation enabled sophisticated attacks

#### 3. Evolution Resistance Analysis

**Adaptation challenges that caused expensive migrations:**

- **Algorithm Agility**: Hardcoded to specific JWT algorithm, couldn't upgrade cryptography
- **Multi-tenant Support**: Single secret design couldn't handle customer-specific keys
- **Audit Requirements**: No authentication event logging for compliance requirements
- **Geographic Compliance**: No region-specific key management for data sovereignty

#### 4. Future Compliance Issues

**Regulatory violations that emerged:**

- **EU Privacy Regulation 2028**: Required zero-knowledge proof authentication
- **US Cyber Resilience Act 2027**: Mandated quantum-resistant cryptography
- **Global Biometric Privacy Law 2029**: Required consent-based biometric fallbacks

## Future-Informed Recommendations

### Immediate Modernization (Based on 2030 Standards)

**Code Improvements to Implement Now**:

1. **Implement WebAuthn**: Add passwordless authentication with hardware security keys
2. **Add Token Binding**: Bind tokens to specific devices/sessions to prevent token theft
3. **Implement Short-lived Tokens**: 15-minute access tokens with secure refresh mechanism
4. **Add Quantum-resistant Algorithms**: Prepare for post-quantum cryptography transition

### Future-Proofing Strategies

**Design Changes for Long-term Sustainability**:

- **Cryptographic Agility**: Abstract cryptographic operations behind interfaces
- **Zero-Knowledge Architecture**: Design for future privacy-preserving authentication
- **Decentralized Identity**: Prepare for self-sovereign identity standards
- **Biometric Privacy**: Plan for privacy-preserving biometric authentication

### Modern Implementation

**Rewrite using 2030 best practices**:

```javascript
// Future-proofed authentication system
import { WebAuthn } from "@webauthn/server";
import { QuantumResistantCrypto } from "@quantum/crypto";
import { PrivacyToken } from "@privacy/tokens";
import { AuditLogger } from "@compliance/audit";

class ModernAuthService {
  constructor() {
    this.webauthn = new WebAuthn({
      origin: process.env.ORIGIN,
      rpId: process.env.RP_ID,
    });
    this.crypto = new QuantumResistantCrypto();
    this.audit = new AuditLogger();
  }

  // Passwordless authentication with WebAuthn
  async initiateAuthentication(email) {
    const user = await User.findOne({ email });
    if (!user) {
      // Don't reveal if user exists (timing attack prevention)
      await this.simulateUserLookup();
      throw new AuthError("AUTHENTICATION_FAILED");
    }

    const options = await this.webauthn.generateAuthenticationOptions({
      rpId: process.env.RP_ID,
      userVerification: "required",
    });

    // Store challenge temporarily with expiration
    await this.storeChallenge(user.id, options.challenge, 300); // 5min expiry

    this.audit.log("AUTH_CHALLENGE_GENERATED", {
      userId: user.pseudonymId, // Privacy-preserving ID
      timestamp: Date.now(),
      ipAddress: this.hashIP(request.ip), // Hashed IP for privacy
    });

    return options;
  }

  async completeAuthentication(credential, clientData) {
    try {
      const verification = await this.webauthn.verifyAuthenticationResponse({
        credential,
        expectedChallenge: await this.getStoredChallenge(credential.id),
        expectedOrigin: process.env.ORIGIN,
        expectedRPID: process.env.RP_ID,
      });

      if (!verification.verified) {
        throw new AuthError("VERIFICATION_FAILED");
      }

      const user = await User.findByCredentialId(credential.id);

      // Generate privacy-preserving session tokens
      const sessionId = this.crypto.generateSecureRandom(32);
      const accessToken = await PrivacyToken.create({
        subject: user.pseudonymId, // Never expose real user ID
        sessionId,
        permissions: user.permissions,
        expiresIn: "15m", // Short-lived
      });

      const refreshToken = await this.crypto.createBoundToken({
        sessionId,
        deviceFingerprint: this.getDeviceFingerprint(clientData),
        expiresIn: "7d",
      });

      // Store session with automatic cleanup
      await this.sessionStore.create(sessionId, {
        userId: user.id,
        deviceId: this.getDeviceId(clientData),
        createdAt: new Date(),
        lastUsed: new Date(),
      });

      this.audit.log("AUTH_SUCCESS", {
        userId: user.pseudonymId,
        sessionId,
        authMethod: "webauthn",
        timestamp: Date.now(),
      });

      return {
        accessToken,
        refreshToken: this.crypto.encrypt(refreshToken),
        expiresIn: 900, // 15 minutes
        user: {
          id: user.pseudonymId, // Privacy-preserving
          permissions: user.permissions,
        },
      };
    } catch (error) {
      this.audit.log("AUTH_FAILURE", {
        error: error.code,
        timestamp: Date.now(),
        ipAddress: this.hashIP(request.ip),
      });
      throw new AuthError("AUTHENTICATION_FAILED");
    }
  }

  // Quantum-resistant token verification
  async verifyToken(token) {
    try {
      const decoded = await PrivacyToken.verify(token);
      const session = await this.sessionStore.get(decoded.sessionId);

      if (!session || session.revoked) {
        throw new AuthError("SESSION_INVALID");
      }

      // Update last used timestamp
      await this.sessionStore.updateLastUsed(decoded.sessionId);

      return {
        userId: session.userId,
        permissions: decoded.permissions,
        sessionId: decoded.sessionId,
      };
    } catch (error) {
      this.audit.log("TOKEN_VERIFICATION_FAILED", {
        error: error.code,
        timestamp: Date.now(),
      });
      throw new AuthError("TOKEN_INVALID");
    }
  }

  // Secure session revocation
  async revokeSession(sessionId, reason = "USER_LOGOUT") {
    await this.sessionStore.revoke(sessionId);
    this.audit.log("SESSION_REVOKED", {
      sessionId,
      reason,
      timestamp: Date.now(),
    });
  }

  // Privacy-preserving device fingerprinting
  getDeviceFingerprint(clientData) {
    const components = [
      clientData.userAgent,
      clientData.screenResolution,
      clientData.timezone,
    ];
    return this.crypto.hash(components.join("|"));
  }
}
```

### Technology Roadmap

**Migration path to 2030-ready authentication**:

1. **Phase 1 (Months 1-3)**: Add WebAuthn alongside current JWT system
2. **Phase 2 (Months 4-6)**: Implement quantum-resistant algorithms and privacy tokens
3. **Phase 3 (Months 7-9)**: Full migration to passwordless with legacy fallback
4. **Phase 4 (Months 10-12)**: Zero-knowledge proof integration for maximum privacy

**Key Benefits of Future-Proofed Approach**:

- **Security**: Quantum-resistant, device-bound authentication
- **Privacy**: Zero user data exposure in tokens, GDPR++ compliant
- **Scalability**: Stateless verification with secure session management
- **Compliance**: Built-in audit logging, regulatory future-proofing
- **User Experience**: Passwordless authentication, seamless device switching

````

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐
- **Time Saved**: 4-8 hours of future-proofing analysis
- **Quality Improvement**: Future-ready vs current-only thinking
- **Use Cases**: Architecture decisions, technology selection, code review

---

## Chaos Engineering Mindset

**File: `prompts/04-advanced/chaos-engineering.md`**

### 🎯 Purpose
Build resilient systems by systematically thinking about failure modes and building defenses.

### 📋 Template

```markdown
Think like a chaos engineer attacking this system:

## Chaos Engineering Mission
**Target System**: [System/Component to analyze]
**Chaos Hypothesis**: [What you believe about system resilience]
**Blast Radius**: [Scope of potential impact]
**Recovery Time Objective**: [Maximum acceptable downtime]

## Failure Mode Discovery

### 1. Infrastructure Failures
**Compute Resources**:
- **Server Failures**: What happens when 1, 2, or all servers go down?
- **CPU Exhaustion**: How does the system behave at 100% CPU for extended periods?
- **Memory Pressure**: What breaks when memory usage hits limits?
- **Disk Failures**: How does the system handle storage corruption or full disks?

**Network Failures**:
- **Network Partitions**: How does the system handle split-brain scenarios?
- **Latency Spikes**: What breaks when network latency increases 10x?
- **Packet Loss**: How does intermittent connectivity affect operations?
- **DNS Failures**: What happens when service discovery fails?

**Cloud Infrastructure**:
- **Region Failures**: Can the system survive entire AWS region outages?
- **Service Degradation**: How does the system handle slow or failing cloud services?
- **Auto-scaling Issues**: What happens when auto-scaling fails to respond?
- **Load Balancer Failures**: How does traffic routing failure affect users?

### 2. Application-Level Failures
**Service Dependencies**:
- **Database Unavailability**: How does the system function without its primary database?
- **Cache Failures**: What's the performance impact when Redis/Memcached fails?
- **External API Outages**: How does the system handle third-party service failures?
- **Message Queue Failures**: What happens when async processing stops?

**Resource Exhaustion**:
- **Connection Pool Exhaustion**: How does the system handle connection starvation?
- **Thread Pool Saturation**: What happens when all worker threads are busy?
- **Memory Leaks**: How does gradual memory consumption affect stability?
- **File Handle Exhaustion**: What breaks when the system runs out of file descriptors?

**Data Integrity Issues**:
- **Corrupt Data**: How does the system handle malformed or corrupted data?
- **Race Conditions**: What data inconsistencies emerge under high concurrency?
- **Transaction Failures**: How does the system handle partial transaction commits?
- **Schema Changes**: How does the system handle database schema evolution?

### 3. Security Attack Scenarios
**Malicious Traffic**:
- **DDoS Attacks**: How does the system handle traffic 100x normal volume?
- **Slowloris Attacks**: What happens with many slow, persistent connections?
- **Resource Exhaustion Attacks**: Can attackers force expensive operations?
- **Input Validation Bypasses**: How does the system handle malicious input?

**Authentication/Authorization Failures**:
- **Token Service Outages**: What happens when auth service is unavailable?
- **Permission Escalation**: Can users access unauthorized resources under load?
- **Session Hijacking**: How does the system detect and prevent session abuse?
- **Credential Stuffing**: How does the system handle mass login attempts?

### 4. Human Error Scenarios
**Operational Mistakes**:
- **Wrong Configuration Deployment**: How does bad config affect system stability?
- **Accidental Data Deletion**: What safeguards exist against data loss?
- **Service Misconfiguration**: How quickly can misconfigurations be detected/rolled back?
- **Certificate Expiration**: What happens when SSL certificates expire unnoticed?

**Development Errors**:
- **Buggy Code Deployment**: How does the system handle code with memory leaks or infinite loops?
- **Database Migration Failures**: What happens when schema changes fail mid-migration?
- **Feature Flag Errors**: How does toggling features affect system stability?
- **Dependency Updates**: What breaks when libraries are updated?

## Chaos Experiment Design

### Experiment 1: [Failure Scenario Name]
**Hypothesis**: [What you think will happen]
**Method**: [How to safely simulate this failure]
**Measurements**: [What metrics to monitor]
**Abort Conditions**: [When to stop the experiment]
**Rollback Plan**: [How to restore normal operation]

### Experiment 2: [Another Critical Failure Mode]
**Steady State Definition**: [What "normal" looks like]
**Failure Injection**: [Specific failure to introduce]
**Expected Impact**: [Predicted system behavior]
**Success Criteria**: [What constitutes resilient behavior]

## Resilience Pattern Implementation

### 1. Circuit Breaker Pattern
**Implementation Strategy**:
```[LANGUAGE]
// Example circuit breaker for external service calls
class CircuitBreaker {
  constructor(failureThreshold = 5, timeout = 60000, monitoringPeriod = 10000) {
    this.failureThreshold = failureThreshold;
    this.timeout = timeout;
    this.monitoringPeriod = monitoringPeriod;
    this.failureCount = 0;
    this.lastFailureTime = null;
    this.state = 'CLOSED'; // CLOSED, OPEN, HALF_OPEN
  }

  async call(operation) {
    if (this.state === 'OPEN') {
      if (Date.now() - this.lastFailureTime < this.timeout) {
        throw new Error('Circuit breaker is OPEN');
      }
      this.state = 'HALF_OPEN';
    }

    try {
      const result = await operation();
      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      throw error;
    }
  }

  onSuccess() {
    this.failureCount = 0;
    this.state = 'CLOSED';
  }

  onFailure() {
    this.failureCount++;
    this.lastFailureTime = Date.now();
    if (this.failureCount >= this.failureThreshold) {
      this.state = 'OPEN';
    }
  }
}
````

### 2. Retry with Exponential Backoff

**Resilient Retry Strategy**:

```[LANGUAGE]
async function resilientRetry(operation, maxRetries = 3) {
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      return await operation();
    } catch (error) {
      if (attempt === maxRetries) throw error;

      // Don't retry on certain errors
      if (error.status >= 400 && error.status < 500) {
        throw error; // Client errors shouldn't be retried
      }

      // Exponential backoff with jitter
      const delay = Math.min(1000 * Math.pow(2, attempt - 1), 30000);
      const jitter = Math.random() * 0.1 * delay;
      await sleep(delay + jitter);
    }
  }
}
```

### 3. Bulkhead Pattern

**Resource Isolation Strategy**:

```[LANGUAGE]
// Separate thread pools for different operations
class BulkheadExecutor {
  constructor() {
    this.pools = {
      critical: new ThreadPool(10),    // Critical operations
      normal: new ThreadPool(20),      // Normal operations
      background: new ThreadPool(5)    // Background tasks
    };
  }

  async execute(operation, priority = 'normal') {
    const pool = this.pools[priority];
    if (!pool.hasCapacity()) {
      throw new Error(`No capacity in ${priority} pool`);
    }
    return pool.execute(operation);
  }
}
```

### 4. Timeout and Deadline Patterns

**Timeout Implementation**:

```[LANGUAGE]
async function withTimeout(operation, timeoutMs) {
  return Promise.race([
    operation(),
    new Promise((_, reject) =>
      setTimeout(() => reject(new Error('Operation timeout')), timeoutMs)
    )
  ]);
}

// Context-aware timeouts
class RequestContext {
  constructor(deadlineMs) {
    this.deadline = Date.now() + deadlineMs;
  }

  getRemainingTime() {
    return Math.max(0, this.deadline - Date.now());
  }

  isExpired() {
    return Date.now() > this.deadline;
  }
}
```

## Monitoring and Observability for Chaos

### Resilience Metrics

**Key Performance Indicators**:

- **Error Rate**: Percentage of failed requests during chaos experiments
- **Recovery Time**: Time to return to steady state after failure injection
- **Blast Radius**: Scope of impact from individual component failures
- **Mean Time to Detection**: How quickly failures are identified
- **Mean Time to Recovery**: How quickly normal operation is restored

### Alerting Strategy

**Chaos-Aware Alerts**:

```yaml
# Example alert rules for chaos engineering
- alert: HighErrorRate
  expr: rate(http_requests_total{status=~"5.."}[5m]) > 0.1
  for: 2m
  labels:
    severity: critical
  annotations:
    summary: "High error rate detected"

- alert: CircuitBreakerOpen
  expr: circuit_breaker_state == 2 # OPEN state
  for: 1m
  labels:
    severity: warning
  annotations:
    summary: "Circuit breaker opened for {{ $labels.service }}"

- alert: SlowResponseTime
  expr: histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m])) > 1
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "95th percentile response time above 1 second"
```

## Chaos Engineering Roadmap

### Phase 1: Foundation (Month 1)

**Basic Resilience Patterns**:

- [ ] Implement circuit breakers for all external service calls
- [ ] Add retry logic with exponential backoff
- [ ] Implement proper timeout handling
- [ ] Set up comprehensive monitoring and alerting

### Phase 2: Infrastructure Chaos (Month 2)

**Infrastructure Failure Testing**:

- [ ] Server failure simulations
- [ ] Network latency injection
- [ ] Database connection pool exhaustion
- [ ] Cache invalidation scenarios

### Phase 3: Application Chaos (Month 3)

**Application-Level Resilience Testing**:

- [ ] High load stress testing
- [ ] Memory pressure simulations
- [ ] Dependency failure testing
- [ ] Race condition discovery

### Phase 4: Advanced Chaos (Month 4+)

**Complex Failure Scenarios**:

- [ ] Multi-component failure combinations
- [ ] Regional outage simulations
- [ ] Security attack simulations
- [ ] Long-term degradation testing

Provide comprehensive chaos engineering analysis and resilience implementation for this specific system.

````

### ⭐ Effectiveness Rating: ⭐⭐⭐⭐⭐
- **Time Saved**: 6-12 hours of resilience planning
- **Quality Improvement**: Proactive vs reactive failure handling
- **Use Cases**: System hardening, disaster recovery planning, production readiness

---

## Contributing Guide

**File: `CONTRIBUTING.md`**

```markdown
# Contributing to AI Copilot Prompts

Thank you for your interest in contributing! This repository is a community effort to build the best collection of AI development prompts.

## How to Contribute

### 1. Adding New Prompts
**What makes a good prompt:**
- ✅ Solves a real development problem
- ✅ Produces significantly better results than basic prompts
- ✅ Includes clear usage examples
- ✅ Has been tested with actual AI tools
- ✅ Follows our template structure

**Prompt Template Structure:**
```markdown
# Prompt Name

## 🎯 Purpose
Clear description of what this prompt achieves

## 📋 Template
[Copy-paste ready prompt template with placeholders]

## 💡 Usage Example
[Real example showing before/after or specific usage]

## ⭐ Effectiveness Rating
Rate from ⭐ to ⭐⭐⭐⭐⭐ based on:
- Time saved
- Quality improvement
- Use case breadth
````

### 2. Improving Existing Prompts

- Test prompts with different AI tools
- Add usage examples
- Improve clarity and effectiveness
- Fix any issues or inaccuracies

### 3. Adding Tool-Specific Configurations

- Optimal settings for different AI tools
- Integration guides
- Performance comparisons

### 4. Sharing Success Stories

Use our [success story template](https://github.com/molntek/ai-copilot-prompts/issues/new?template=success-story.md) to share how these prompts helped you.

## Submission Process

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b new-prompt-name`)
3. **Add your prompt** following our template structure
4. **Test thoroughly** with at least 2 different AI tools
5. **Submit a pull request** with clear description

## Quality Guidelines

### Prompt Quality Checklist

- [ ] Prompt is specific and actionable
- [ ] Includes context-setting instructions
- [ ] Produces consistent, high-quality results
- [ ] Includes error handling considerations
- [ ] Has been tested with real projects

### Code Example Guidelines

- [ ] Examples are realistic, not contrived
- [ ] Show clear before/after comparisons
- [ ] Include both successful and edge cases
- [ ] Follow security best practices
- [ ] Are production-ready, not just prototypes

## Community Guidelines

- **Be respectful** in all interactions
- **Share knowledge** freely and help others learn
- **Test thoroughly** before submitting
- **Provide context** for your contributions
- **Collaborate openly** and accept feedback

## Recognition

Contributors will be:

- Listed in our [CONTRIBUTORS.md](./CONTRIBUTORS.md) file
- Credited in prompt documentation
- Invited to our private contributor discussions
- Given early access to new prompts and tools

## Questions?

- Open an [issue](https://github.com/molntek/ai-copilot-prompts/issues)
- Join our [Discord community](https://discord.gg/ai-devs)
- Email us at [prompts@molntek.com](mailto:prompts@molntek.com)

Happy coding! 🚀

```

This complete GitHub project provides developers with a comprehensive, battle-tested collection of AI prompts that will genuinely transform their development workflow. The structure is designed for easy contribution, discovery, and practical usage across all major AI development tools.
```
