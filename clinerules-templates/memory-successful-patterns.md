# Successful Patterns

This document catalogs effective patterns discovered and implemented during the project. These patterns represent proven solutions to common problems and should be considered for similar situations.

## Table of Contents
1. [Pattern: Repository Abstraction](#pattern-repository-abstraction)
2. [Pattern: Feature Flag Configuration](#pattern-feature-flag-configuration)
3. [Pattern: Circuit Breaker for External Services](#pattern-circuit-breaker-for-external-services)

---

## Pattern: Repository Abstraction
**ID:** 2025-03-15-01  
**Pattern Name:** Repository Abstraction  
**Category:** Data Access

### Type
Successful Pattern

### Problem
Direct database access code scattered throughout the application creates tight coupling between business logic and data access mechanisms, making it difficult to test, modify the data source, or adapt to changing requirements.

### Context
This pattern is applicable when:
- The application performs complex data operations
- You want to isolate business logic from data access details
- Multiple data sources might be used
- Unit testing without database dependencies is required

### Solution/Structure
Implement a repository layer that abstracts data access operations behind a consistent interface:

```typescript
// Define a repository interface
interface UserRepository {
  findById(id: string): Promise<User | null>;
  findByEmail(email: string): Promise<User | null>;
  create(userData: UserCreationData): Promise<User>;
  update(id: string, userData: Partial<User>): Promise<User>;
  delete(id: string): Promise<boolean>;
}

// Implement for specific database
class PostgresUserRepository implements UserRepository {
  constructor(private db: DatabaseConnection) {}
  
  async findById(id: string): Promise<User | null> {
    const result = await this.db.query(
      'SELECT * FROM users WHERE id = $1',
      [id]
    );
    return result.rows[0] ? this.mapToUser(result.rows[0]) : null;
  }
  
  // Other methods implemented similarly...
  
  private mapToUser(row: any): User {
    return {
      id: row.id,
      name: row.name,
      email: row.email,
      // other fields...
    };
  }
}

// Usage in business logic
class UserService {
  constructor(private userRepository: UserRepository) {}
  
  async getUserProfile(userId: string): Promise<UserProfile> {
    const user = await this.userRepository.findById(userId);
    if (!user) {
      throw new UserNotFoundError(userId);
    }
    return this.createUserProfile(user);
  }
  
  // Other business logic...
}
```

### Consequences
- Decouples business logic from data access implementation
- Makes unit testing easier through repository interfaces
- Centralizes data access logic and query management
- Allows for easier switching between data sources
- Provides a consistent abstraction for different data operations

### Implementation Considerations
- Create repository interfaces for each domain entity
- Consider using a factory pattern for repository creation
- Be mindful of transaction management across repositories
- For complex queries, consider using a query object pattern
- Use dependency injection to provide repositories to services

### Related Patterns
- Unit of Work
- Domain-Driven Design Aggregate Patterns
- Factory Pattern for repository creation

### Known Uses
- User management module
- Product catalog system
- Order processing workflow

### References
- Task: "Refactor Data Access Layer"
- [Domain-Driven Design References](https://example.com/ddd)
- Architecture decision record #45

### Cross-References
- Related Decision: Data Access Layer Architecture
- Related Learning: SQL Query Optimization

---

## Pattern: Feature Flag Configuration
**ID:** 2025-03-10-02  
**Pattern Name:** Feature Flag Configuration  
**Category:** Application Configuration

### Type
Successful Pattern

### Problem
Deploying new features to production carries risk, especially for large changes. Traditional feature branches lead to long-lived branches and difficult merges, while direct deployments can impact all users at once if problems occur.

### Context
This pattern is applicable when:
- You want to deploy code to production without activating it immediately
- You need to test features with a subset of users before full release
- Different environments require different feature sets
- You want to A/B test variations of a feature

### Solution/Structure
Implement a feature flag system that allows enabling/disabling features at runtime:

```typescript
// Feature flag configuration service
class FeatureFlagService {
  private flags: Map<string, FeatureFlag>;
  
  constructor(private configSource: ConfigurationSource) {
    this.flags = new Map();
    this.loadFlags();
  }
  
  private async loadFlags() {
    const configs = await this.configSource.getConfigurations();
    configs.forEach(config => {
      this.flags.set(config.name, {
        name: config.name,
        enabled: config.enabled,
        rules: config.rules || []
      });
    });
  }
  
  isEnabled(flagName: string, context?: EvaluationContext): boolean {
    const flag = this.flags.get(flagName);
    if (!flag) return false;
    
    // Global flag state
    if (!flag.enabled) return false;
    
    // No specific rules, use global state
    if (!flag.rules || flag.rules.length === 0) return true;
    
    // Evaluate rules if context is provided
    if (context) {
      return this.evaluateRules(flag.rules, context);
    }
    
    return true;
  }
  
  private evaluateRules(rules: FeatureRule[], context: EvaluationContext): boolean {
    // Rule evaluation logic here
    // e.g., user percentage rollouts, user properties, time-based activation
    // ...
  }
}

// Usage in application code
function renderComponent() {
  if (featureFlagService.isEnabled('new-user-profile', { userId: currentUser.id })) {
    return <NewUserProfileComponent />;
  }
  return <LegacyUserProfileComponent />;
}
```

### Consequences
- Reduces risk by controlling feature rollout
- Enables canary releases and gradual rollouts
- Allows for A/B testing of features
- Simplifies emergency feature deactivation
- Enables environment-specific feature configurations

### Implementation Considerations
- Store flag configurations in a central location (database, configuration service)
- Consider caching flag states to improve performance
- Design feature flags to be temporary when possible
- Create a management UI for controlling flags
- Regularly clean up unused feature flags

### Related Patterns
- Circuit Breaker Pattern
- Strategy Pattern for feature variations
- Observer Pattern for flag state changes

### Known Uses
- User interface revamp
- New payment processing system
- Search algorithm improvements
- Premium feature rollout

### References
- [Feature Flagging Best Practices](https://example.com/feature-flags)
- Architecture decision record #38
- Task: "Implement Feature Flag System"

### Cross-References
- Related Decision: Continuous Deployment Strategy
- Related Learning: Canary Release Implementation

---

## Pattern: Circuit Breaker for External Services
**ID:** 2025-03-05-03  
**Pattern Name:** Circuit Breaker for External Services  
**Category:** Integration Resilience

### Type
Successful Pattern

### Problem
External service calls can fail or experience timeout issues. Continuous retry attempts during service degradation can worsen the situation by increasing load on the struggling service, while also blocking threads and resources in the calling application.

### Context
This pattern is applicable when:
- The application depends on external APIs or services
- Service calls might experience intermittent failures
- You want to prevent cascading failures
- You need graceful degradation during integration issues

### Solution/Structure
Implement a circuit breaker that monitors for failures and temporarily "opens" (blocks) requests after a threshold is reached:

```typescript
enum CircuitState {
  CLOSED,   // Normal operation, requests go through
  OPEN,     // Circuit is open, requests fail fast
  HALF_OPEN // Testing if service is recovered
}

class CircuitBreaker {
  private state: CircuitState = CircuitState.CLOSED;
  private failureCount: number = 0;
  private lastFailureTime: number = 0;
  private successCount: number = 0;
  
  constructor(
    private failureThreshold: number = 5,
    private resetTimeout: number = 30000, // 30 seconds
    private halfOpenSuccessThreshold: number = 3
  ) {}
  
  async executeRequest<T>(request: () => Promise<T>, fallback?: () => Promise<T>): Promise<T> {
    if (this.state === CircuitState.OPEN) {
      if (Date.now() - this.lastFailureTime > this.resetTimeout) {
        this.state = CircuitState.HALF_OPEN;
        this.successCount = 0;
      } else {
        // Circuit is open, fail fast
        if (fallback) {
          return fallback();
        }
        throw new Error('Circuit is open');
      }
    }
    
    try {
      const result = await request();
      
      // Success handling
      if (this.state === CircuitState.HALF_OPEN) {
        this.successCount++;
        if (this.successCount >= this.halfOpenSuccessThreshold) {
          // Service has recovered
          this.state = CircuitState.CLOSED;
          this.failureCount = 0;
        }
      } else {
        // Normal success in closed state
        this.failureCount = 0;
      }
      
      return result;
    } catch (error) {
      // Failure handling
      this.lastFailureTime = Date.now();
      this.failureCount++;
      
      if (this.state === CircuitState.CLOSED && this.failureCount >= this.failureThreshold) {
        this.state = CircuitState.OPEN;
      } else if (this.state === CircuitState.HALF_OPEN) {
        this.state = CircuitState.OPEN;
      }
      
      if (fallback) {
        return fallback();
      }
      throw error;
    }
  }
}

// Usage example
const paymentServiceBreaker = new CircuitBreaker(3, 60000);

async function processPayment(paymentData) {
  return paymentServiceBreaker.executeRequest(
    // Main request
    () => paymentApiClient.processPayment(paymentData),
    // Fallback function
    () => {
      logPaymentForManualProcessing(paymentData);
      return { status: 'pending', message: 'Payment queued for processing' };
    }
  );
}
```

### Consequences
- Prevents cascading failures across services
- Reduces load on failing external services
- Improves response time during failure scenarios by failing fast
- Enables graceful degradation through fallback mechanisms
- Automatically recovers when external service becomes available

### Implementation Considerations
- Configure appropriate thresholds based on service characteristics
- Implement different circuit breaker instances for different services
- Consider adding monitoring and alerting for circuit state changes
- Use exponential backoff for retry attempts in half-open state
- Combine with bulkhead pattern to isolate failures

### Related Patterns
- Retry Pattern
- Bulkhead Pattern
- Fallback Pattern
- Health Endpoint Monitoring

### Known Uses
- Payment processing service integration
- Third-party authentication service calls
- External shipping API integration
- Cloud storage service access

### References
- [Circuit Breaker Pattern](https://example.com/circuit-breaker)
- [Resilience4j Documentation](https://example.com/resilience4j)
- Architecture decision record #32

### Cross-References
- Related Decision: External Service Integration Strategy
- Related Learning: Resilient System Design
- Related Pattern: Retry with Exponential Backoff
