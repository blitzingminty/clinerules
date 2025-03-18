# Strict Coding Rules

## Purpose

These rules establish the most rigorous standards for software development, designed for mission-critical systems where reliability, security, and performance are paramount. The policy mandates exhaustive testing and validation, comprehensive documentation, and zero-tolerance for quality compromises. This approach ensures the highest level of code quality throughout the development lifecycle, minimizing the risk of critical failures in production environments.

## Core Principles

1. **Zero Defect Tolerance**: No known defects are acceptable in production code.
2. **Comprehensive Testing**: All code must undergo exhaustive testing at multiple levels.
3. **Security First**: Security considerations must be integrated at every stage of development.
4. **Performance Excellence**: Code must be optimized for maximum performance and efficiency.
5. **Complete Traceability**: Every line of code must be traceable to requirements and design specifications.
6. **Continuous Verification**: Quality must be continuously verified through automated and manual processes.

## Code Standards

### General Coding Standards

1. **Code Clarity**:
   - All code must be self-explanatory, with clear naming and structure
   - Complex logic must be refactored into smaller, well-named functions
   - Avoid clever or obscure programming techniques
   - Magic numbers and strings must be replaced with named constants

2. **Code Structure**:
   - Functions/methods must not exceed 50 lines of code
   - Files must not exceed 500 lines of code
   - Classes must adhere to single responsibility principle
   - Cyclomatic complexity must not exceed 10 for any function
   - Nesting levels must not exceed 3 levels deep

3. **Code Readability**:
   - Consistent indentation and formatting must be used
   - All code must follow project style guide without exceptions
   - Variable and function names must clearly indicate purpose and usage
   - Use whitespace effectively to separate logical sections

### Language-Specific Standards

For each programming language used in the project, detailed standards must be documented covering:
- Language-specific pitfalls and how to avoid them
- Memory management practices
- Concurrency and threading rules
- Performance optimization techniques
- Library and dependency usage guidelines

### Secure Coding Standards

1. **Input Validation**:
   - All input must be validated before processing
   - Input validation must happen at system boundaries
   - Strict type checking must be enforced
   - Defense in depth must be implemented

2. **Output Encoding**:
   - All output must be properly encoded for its destination context
   - Content Security Policy must be implemented
   - Output filtering must be implemented as appropriate

3. **Authentication and Authorization**:
   - Strong authentication mechanisms must be used
   - Multi-factor authentication must be implemented for sensitive operations
   - Authorization checks must be performed at each access point
   - Principle of least privilege must be enforced

4. **Data Protection**:
   - All sensitive data must be encrypted in transit and at rest
   - Key management procedures must be documented and followed
   - Data retention policies must be implemented
   - Secure deletion practices must be followed

5. **Error Handling**:
   - All errors must be handled appropriately
   - Error messages must not expose sensitive information
   - Errors must be logged with sufficient context for debugging
   - Critical errors must trigger appropriate alerts

### Performance Standards

1. **Resource Efficiency**:
   - Memory usage must be optimized and monitored
   - CPU usage must be optimized for critical paths
   - I/O operations must be minimized and optimized
   - Network traffic must be minimized and optimized

2. **Response Time**:
   - Critical operations must complete within defined time limits
   - Response time must be measured and monitored
   - Performance degradation must trigger alerts
   - Performance tests must verify response time requirements

3. **Scalability**:
   - Code must scale horizontally and vertically
   - Load tests must verify scalability requirements
   - Resource usage must be linear with load
   - Bottlenecks must be identified and eliminated

## Testing Requirements

### Unit Testing

1. **Coverage Requirements**:
   - Line coverage must exceed 95%
   - Branch coverage must exceed 90%
   - Function coverage must be 100%
   - Complex conditional coverage must exceed 95%

2. **Test Quality Requirements**:
   - Tests must be independent and idempotent
   - Tests must verify both positive and negative cases
   - Tests must verify boundary conditions
   - Tests must verify error handling

3. **Mocking Guidelines**:
   - External dependencies must be properly mocked
   - Mocks must accurately simulate dependency behavior
   - Mocks must verify interaction patterns
   - Over-mocking must be avoided

### Integration Testing

1. **Scope Requirements**:
   - All module interactions must be tested
   - All API endpoints must be tested
   - All external service integrations must be tested
   - All data flows must be tested

2. **Environment Requirements**:
   - Integration tests must run in environments similar to production
   - Data fixtures must represent realistic scenarios
   - Integration test environments must be isolated
   - Integration tests must clean up after themselves

3. **Verification Requirements**:
   - Contract conformance must be verified
   - Error handling and recovery must be verified
   - Performance at integration points must be verified
   - Security at integration points must be verified

### System Testing

1. **Functional Testing**:
   - All requirements must be verified through tests
   - All user journeys must be tested
   - All business processes must be tested
   - All edge cases must be tested

2. **Non-Functional Testing**:
   - Performance under expected load must be tested
   - Performance under peak load must be tested
   - Performance under sustained load must be tested
   - Resource utilization must be measured and verified

3. **Security Testing**:
   - Penetration testing must be performed regularly
   - Vulnerability scanning must be performed regularly
   - Threat modeling must be performed for new features
   - Security compliance must be verified

### Specialized Testing

1. **Chaos Engineering**:
   - System must be tested under chaos conditions
   - Recovery from component failures must be tested
   - Degraded operation must be tested
   - Unexpected inputs must be tested

2. **Resilience Testing**:
   - Long-running tests must verify system stability
   - Resource leaks must be detected through long-running tests
   - Recovery from resource exhaustion must be tested
   - Self-healing capabilities must be tested

3. **Compatibility Testing**:
   - Backward compatibility must be verified
   - Forward compatibility must be considered
   - Cross-platform compatibility must be tested
   - Cross-browser compatibility must be tested for web applications

## Code Review Process

### Review Requirements

1. **Review Coverage**:
   - 100% of code changes must be reviewed
   - At least two reviewers must approve each change
   - Domain experts must review domain-specific code
   - Security experts must review security-sensitive code

2. **Review Depth**:
   - Reviewers must verify code correctness
   - Reviewers must verify adherence to all standards
   - Reviewers must verify test coverage and quality
   - Reviewers must verify documentation completeness

3. **Review Timeliness**:
   - Reviews must be completed within 48 hours
   - Review feedback must be addressed promptly
   - Review discussions must be documented
   - Review approvals must be explicit

### Review Checklist

A comprehensive review checklist must be used covering:
- Functional correctness
- Error handling
- Security considerations
- Performance considerations
- Testability
- Documentation
- Maintainability
- Compatibility
- Accessibility (where applicable)

### Pair Programming

1. **Pair Programming Requirements**:
   - Critical code sections must be developed using pair programming
   - Security-sensitive code must be developed using pair programming
   - Complex algorithms must be developed using pair programming
   - Pairing sessions must be documented

## Static Analysis

### Tool Requirements

1. **Required Tools**:
   - Linters for all languages used in the project
   - Complexity analyzers for all languages used in the project
   - Security scanners for all languages used in the project
   - Dependency analyzers for all package ecosystems

2. **Configuration Requirements**:
   - Tools must be configured according to project standards
   - Configuration must be version controlled
   - Configuration must be documented
   - Configuration must be reviewed

3. **Integration Requirements**:
   - Static analysis must be integrated into CI/CD pipeline
   - Static analysis must be integrated into IDEs
   - Static analysis must be integrated into code review process
   - Static analysis results must be tracked over time

### Issue Handling

1. **Issue Categorization**:
   - Issues must be categorized by severity
   - Issues must be categorized by type
   - Issues must be categorized by component
   - Issues must be assigned to owners

2. **Resolution Requirements**:
   - Critical issues must be fixed immediately
   - High-severity issues must be fixed before release
   - Medium-severity issues must have a plan for resolution
   - Low-severity issues must be tracked

3. **False Positive Handling**:
   - False positives must be documented
   - False positives must be reviewed by a second person
   - False positive configurations must be minimized
   - False positive configurations must be reviewed regularly

## Documentation Requirements

### Code Documentation

1. **API Documentation**:
   - All public APIs must be fully documented
   - Parameters and return values must be documented
   - Exceptions and error conditions must be documented
   - Usage examples must be provided
   - API version compatibility must be documented

2. **Implementation Documentation**:
   - Complex algorithms must be documented
   - Non-obvious code must be documented
   - Performance considerations must be documented
   - Threading considerations must be documented

3. **Comment Standards**:
   - Comments must explain why, not what
   - Comments must be kept up-to-date with code changes
   - Comments must use standard documentation formats
   - Comments must be clear and concise

### Technical Documentation

1. **Architecture Documentation**:
   - System architecture must be documented
   - Component relationships must be documented
   - Data flow must be documented
   - Security architecture must be documented

2. **Operation Documentation**:
   - Deployment procedures must be documented
   - Monitoring requirements must be documented
   - Backup and recovery procedures must be documented
   - Troubleshooting guides must be provided

## Compliance Verification

### Automated Verification

1. **CI/CD Requirements**:
   - All verification steps must be automated in CI/CD
   - CI/CD pipeline must fail if any verification fails
   - CI/CD results must be documented and traceable
   - CI/CD pipeline must be secured

2. **Metrics Collection**:
   - Quality metrics must be collected automatically
   - Metrics must be tracked over time
   - Metrics must be visible to all stakeholders
   - Metrics must be used for continuous improvement

### Manual Verification

1. **Code Inspection**:
   - Critical code sections must undergo manual inspection
   - Manual inspections must follow a defined process
   - Manual inspection results must be documented
   - Manual inspections must be performed by qualified personnel

2. **Security Audits**:
   - Regular security audits must be performed
   - Audit findings must be addressed promptly
   - Audit procedures must be documented
   - Audit scope must be comprehensive

## Dependency Management

### Dependency Selection

1. **Selection Criteria**:
   - Dependencies must have a proven track record
   - Dependencies must be actively maintained
   - Dependencies must have adequate documentation
   - Dependencies must have appropriate licensing

2. **Risk Assessment**:
   - Dependencies must undergo security risk assessment
   - Dependencies must undergo reliability risk assessment
   - Dependencies must undergo maintainability risk assessment
   - Risk assessments must be documented

### Dependency Monitoring

1. **Vulnerability Tracking**:
   - Vulnerability scanners must continuously monitor dependencies
   - Vulnerability alerts must be addressed promptly
   - Vulnerability management process must be documented
   - Vulnerability remediation must be prioritized

2. **Version Management**:
   - Dependency versions must be locked
   - Dependency updates must be reviewed and tested
   - Dependency update schedule must be established
   - Dependency changelog must be reviewed

## Incident Response

### Defect Handling

1. **Severity Classification**:
   - Defects must be classified by severity
   - Severity classification criteria must be documented
   - Severity classification must be reviewed
   - Severity classifications must be used for prioritization

2. **Resolution Requirements**:
   - Critical defects must be fixed immediately
   - Defect resolution must be tested thoroughly
   - Defect resolution must be reviewed
   - Defect resolution must be documented

### Root Cause Analysis

1. **Analysis Process**:
   - Significant defects must undergo root cause analysis
   - Analysis must identify both immediate and systemic causes
   - Analysis must result in actionable recommendations
   - Analysis must be documented

2. **Prevention Measures**:
   - Systemic issues must be addressed
   - Prevention measures must be implemented
   - Prevention measure effectiveness must be verified
   - Lessons learned must be shared

## Training and Competency

### Developer Requirements

1. **Required Knowledge**:
   - Developers must understand all applicable standards
   - Developers must be trained in secure coding practices
   - Developers must be familiar with testing methodologies
   - Developers must know how to use all required tools

2. **Verification of Competency**:
   - Developer competency must be verified
   - Competency verification must be documented
   - Competency must be maintained through continuous learning
   - Skills gaps must be addressed through training

### Continuous Improvement

1. **Learning Culture**:
   - Best practices must be shared
   - Continuous learning must be encouraged
   - Knowledge sharing sessions must be held regularly
   - External learning resources must be provided

2. **Process Improvement**:
   - Quality processes must be reviewed regularly
   - Improvement suggestions must be encouraged
   - Process changes must be tested
   - Process improvements must be documented

## Policy Exceptions

### Exception Process

1. **Request Requirements**:
   - Exception requests must be documented
   - Exception requests must include justification
   - Exception requests must include risk assessment
   - Exception requests must include mitigation plan

2. **Approval Requirements**:
   - Exceptions must be approved by designated authorities
   - Approvals must be documented
   - Approvals must specify scope and duration
   - Approvals must be reviewed periodically

### Exception Monitoring

1. **Tracking Requirements**:
   - All exceptions must be tracked
   - Exception status must be reviewed regularly
   - Exception expiration must be enforced
   - Exception impact must be monitored

## Examples

### High-Quality Code Example

```java
/**
 * Processes a payment transaction through the specified payment gateway.
 * <p>
 * This method handles the entire payment processing flow including validation,
 * gateway communication, error handling, retry logic, and transaction recording.
 * It ensures that transactions are atomic and consistent even in the case of
 * partial failures by implementing a two-phase commit pattern with the
 * transaction database and payment gateway.
 * <p>
 * The method is idempotent and can be safely retried with the same transactionId
 * without resulting in duplicate charges. If a transaction with the given ID
 * already exists, the method will return the existing result rather than
 * processing again.
 *
 * @param transactionRequest The payment transaction request containing all necessary
 *                          details for processing the payment. Must not be null.
 *                          All required fields must be populated according to the
 *                          {@link TransactionRequest} documentation.
 * @param gatewayType The payment gateway to use for processing. Must be one of
 *                   the supported gateways defined in {@link GatewayType}.
 *                   If null, the default gateway will be selected based on the
 *                   payment method and transaction properties.
 * @param options Additional processing options that modify the behavior of the
 *               payment processing. Optional, may be null to use default behavior.
 *               See {@link PaymentOptions} for available options.
 *
 * @return A {@link TransactionResult} object containing the complete result of
 *         the transaction, including gateway reference ID, status, and any
 *         error information. Never returns null.
 *
 * @throws ValidationException If the transaction request is invalid or missing
 *                            required fields. The exception will contain detailed
 *                            information about which validations failed.
 * @throws GatewayException If communication with the payment gateway fails or the
 *                         gateway returns an unrecoverable error. Contains the
 *                         specific gateway error code and message.
 * @throws PaymentDeclinedException If the payment was declined by the gateway or
 *                                 issuing bank. Contains the decline code and
 *                                 reason if available.
 * @throws SystemException If an unexpected internal error occurs during processing.
 */
@Transactional
@Monitored(category = "payment", name = "process_transaction")
public TransactionResult processTransaction(
        @NotNull TransactionRequest transactionRequest,
        @Nullable GatewayType gatewayType,
        @Nullable PaymentOptions options) throws ValidationException, 
        GatewayException, PaymentDeclinedException, SystemException {
    
    // Validate inputs
    validateTransactionRequest(transactionRequest);
    
    // Check for existing transaction with same ID to ensure idempotency
    Optional<TransactionResult> existingTransaction = 
            transactionRepository.findByRequestId(transactionRequest.getRequestId());
    if (existingTransaction.isPresent()) {
        logger.info("Retrieved existing transaction for requestId: {}", 
                transactionRequest.getRequestId());
        return existingTransaction.get();
    }
    
    // Select appropriate gateway
    GatewayType selectedGateway = selectGateway(gatewayType, transactionRequest);
    PaymentGateway gateway = gatewayFactory.getGateway(selectedGateway);
    
    // Apply default options if none provided
    PaymentOptions effectiveOptions = 
            options != null ? options : PaymentOptions.getDefaults();
    
    // Begin transaction in pending state
    Transaction transaction = 
            transactionFactory.createTransaction(transactionRequest, selectedGateway);
    transactionRepository.save(transaction);
    
    TransactionResult result;
    try {
        // Process payment through gateway with circuit breaker pattern
        GatewayResponse gatewayResponse = 
                circuitBreaker.executeWithFallback(
                    () -> gateway.processPayment(transactionRequest, effectiveOptions),
                    this::handleGatewayFailure
                );
        
        // Update transaction with gateway response
        transaction.setGatewayReferenceId(gatewayResponse.getReferenceId());
        transaction.setStatus(mapGatewayStatus(gatewayResponse.getStatus()));
        
        // Handle declined payments
        if (gatewayResponse.getStatus() == GatewayStatus.DECLINED) {
            transaction.setErrorCode(gatewayResponse.getErrorCode());
            transaction.setErrorMessage(gatewayResponse.getErrorMessage());
            result = buildDeclinedResult(transaction, gatewayResponse);
            throw new PaymentDeclinedException(result);
        }
        
        // Create successful result
        result = buildSuccessResult(transaction, gatewayResponse);
        
    } catch (GatewayException | SystemException e) {
        // Mark transaction as failed and rethrow
        transaction.setStatus(TransactionStatus.ERROR);
        transaction.setErrorCode(e.getErrorCode());
        transaction.setErrorMessage(e.getMessage());
        transactionRepository.save(transaction);
        
        logger.error("Payment processing failed for transaction: {}", 
                transaction.getId(), e);
        throw e;
    }
    
    // Finalize and return
    transactionRepository.save(transaction);
    notificationService.notifyTransactionComplete(transaction);
    
    logger.info("Successfully processed transaction: {}", transaction.getId());
    return result;
}
```

### Example of Code That Violates Strict Standards

```java
// This code violates multiple strict standards:
// - Lacks proper validation
// - No error handling
// - No parameter documentation
// - Poor naming
// - No transaction management
// - No logging
// - Mixes concerns
// - No idempotency
public boolean pay(String cc, String exp, double amt, String currName) throws Exception {
    // Validate card (weak validation)
    if (cc == null || cc.length() < 16) return false;
    
    // Connect to payment processor
    PaymentProcessor proc = new PaymentProcessor("api-key-1234"); // Hard-coded credential
    
    // Process the payment
    var res = proc.submitPayment(cc, exp, amt, currName);
    
    // Update balance in database
    if (res.status.equals("OK")) {
        double newBal = getAccountBalance() - amt;
        updateBalance(newBal);
        sendEmail(userEmail, "Payment processed", "Your payment of " + amt + " was processed.");
        return true;
    }
    
    return false;
}
