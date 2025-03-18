# Project Mistakes Registry

This document tracks mistakes and issues encountered during the project. Each entry provides analysis and prevention strategies to avoid repeating similar issues in the future.

## Table of Contents
1. [Mistake: N+1 Query Performance Issue](#mistake-n1-query-performance-issue)
2. [Mistake: Memory Leak in Component Lifecycle](#mistake-memory-leak-in-component-lifecycle)
3. [Mistake: Incorrect Timezone Handling](#mistake-incorrect-timezone-handling)

---

## Mistake: N+1 Query Performance Issue
**ID:** 2025-03-10-01  
**Category:** Database Performance

### Description
The product listing page experienced significant performance degradation when displaying products with their associated categories and tags, causing page load times of 5-7 seconds.

### Context
The page was loading a list of products and then making separate database queries for each product's related data (categories and tags), resulting in hundreds of individual queries for a single page load.

### Root Cause Analysis
The ORM was configured to lazy-load relationships, causing additional queries for each product's related data. This created the classic N+1 query problem: 1 query to fetch N products, then N additional queries to fetch related data.

### Impact
- Very slow page load times (5-7 seconds)
- High database server load
- Poor user experience on product listing pages
- Potential for database connection pool exhaustion under high traffic

### Solution
Implemented eager loading of relationships using the ORM's capabilities:

```javascript
// Before
const products = await ProductModel.findAll({
  where: { isActive: true },
  limit: 20,
  offset: 0
});
// Each product access like product.categories triggered a new query

// After
const products = await ProductModel.findAll({
  where: { isActive: true },
  include: [
    { model: CategoryModel },
    { model: TagModel }
  ],
  limit: 20,
  offset: 0
});
// All data loaded in a single query with joins
```

### Prevention Strategy
1. Use query analyzers during development to detect N+1 query patterns
2. Configure ORM to warn about potential N+1 query issues
3. Implement eager loading by default for common relationship access patterns
4. Create a standard data access pattern document for the team
5. Add performance tests that fail if page load requires more than a specified number of queries

### Detection Method
- Monitor query count per request in development
- Set up query logging with timing information
- Use APM tools to identify slow database operations

### References
- Issue #127: Slow Product Listing Page
- [Database Performance Optimization Guide](https://example.com/db-optimization)
- [ORM Documentation - Eager Loading](https://example.com/orm-eager-loading)

### Cross-References
- Related Learning: Optimizing Database Queries
- Related Anti-Pattern: Excessive Database Queries

---

## Mistake: Memory Leak in Component Lifecycle
**ID:** 2025-03-05-02  
**Category:** Frontend Performance

### Description
A memory leak occurred in the dashboard component, causing the application to become increasingly slow and eventually crash after prolonged usage.

### Context
The dashboard component was subscribing to WebSocket events for real-time updates but failing to unsubscribe when the component unmounted.

### Root Cause Analysis
Event listeners and subscriptions were being created in useEffect without proper cleanup. Every time the component re-rendered or remounted, new listeners were added without removing the old ones.

### Impact
- Gradually increasing memory usage
- Degraded application performance over time
- Browser tab crashes after extended use
- Duplicate event processing leading to UI inconsistencies

### Solution
Added proper cleanup in the useEffect hook:

```javascript
// Before
useEffect(() => {
  const socket = new WebSocket('ws://api.example.com/updates');
  socket.addEventListener('message', handleMessage);
  // No cleanup
}, []);

// After
useEffect(() => {
  const socket = new WebSocket('ws://api.example.com/updates');
  socket.addEventListener('message', handleMessage);
  
  // Return cleanup function
  return () => {
    socket.removeEventListener('message', handleMessage);
    socket.close();
  };
}, []);
```

### Prevention Strategy
1. Create a linting rule to detect useEffect without cleanup
2. Implement a standard WebSocket/subscription wrapper that handles cleanup automatically
3. Add memory profiling to the development workflow
4. Create a checklist for component reviews that includes subscription management
5. Educate team on React component lifecycle best practices

### Detection Method
- Use Chrome DevTools Memory profiler to identify retained objects
- Implement performance monitoring that alerts on memory growth
- Add explicit logging for subscription creation and cleanup

### References
- Issue #143: Dashboard Performance Degradation
- [React useEffect Documentation](https://reactjs.org/docs/hooks-effect.html)
- [Memory Leak Detection Guide](https://example.com/memory-leak)

### Cross-References
- Related Anti-Pattern: Uncleaned Component Resources
- Related Learning: React Component Lifecycle Management

---

## Mistake: Incorrect Timezone Handling
**ID:** 2025-02-28-03  
**Category:** Data Processing

### Description
User appointment times were displayed incorrectly, showing times in the server's timezone rather than the user's local timezone.

### Context
The calendar view was showing appointments at wrong times, causing scheduling confusion. For example, a 3 PM appointment would show as 8 PM if the server was 5 hours ahead of the user.

### Root Cause Analysis
Dates were being processed and formatted on the server without timezone context. The server converted all times to its local timezone before sending to the client.

### Impact
- Users missed appointments due to incorrect times
- Scheduling conflicts occurred
- Loss of user trust in the application
- Support team overwhelmed with timezone-related issues

### Solution
Implemented proper timezone handling throughout the application:

```javascript
// Before
const appointmentTime = new Date(appointment.startTime).toLocaleTimeString();

// After
// Store all dates in UTC in the database
// On the server
const utcAppointmentTime = appointment.startTime; // Already in UTC

// On the client
const userTimezone = Intl.DateTimeFormat().resolvedOptions().timeZone;
const appointmentTime = new Date(utcAppointmentTime).toLocaleTimeString(
  undefined,
  { timeZone: userTimezone }
);
```

### Prevention Strategy
1. Store all dates in UTC format in the database
2. Pass timezone information with all date-related API requests
3. Handle date formatting on the client side with user's local timezone
4. Add timezone indicators to all displayed dates
5. Create date/time utility functions that enforce proper timezone handling

### Detection Method
- Add timezone unit tests that verify correct time conversion
- Implement date auditing that logs timezone inconsistencies
- Create a QA test suite specifically for timezone scenarios

### References
- Issue #98: Calendar Timezone Issues
- [JavaScript Date Internationalization](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)
- [Date Best Practices](https://example.com/date-best-practices)

### Cross-References
- Related Decision: Standardized Date Handling Strategy
- Related Learning: Internationalization Implementation
