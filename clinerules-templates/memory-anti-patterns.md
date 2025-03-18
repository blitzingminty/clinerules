# Anti-Patterns

This document catalogs problematic patterns observed during the project. These anti-patterns represent approaches that should be avoided based on previous negative experiences.

## Table of Contents
1. [Anti-Pattern: God Component](#anti-pattern-god-component)
2. [Anti-Pattern: Direct DOM Manipulation with React](#anti-pattern-direct-dom-manipulation-with-react)
3. [Anti-Pattern: Nested Callback Hell](#anti-pattern-nested-callback-hell)

---

## Anti-Pattern: God Component
**ID:** 2025-03-15-01  
**Pattern Name:** God Component  
**Category:** Frontend Architecture

### Type
Anti-Pattern

### Problem
A single component takes on too many responsibilities, becoming overly complex, difficult to test, and challenging to maintain. These components often grow to hundreds or thousands of lines of code.

### Context
This anti-pattern tends to emerge when:
- Features are continuously added to an existing component
- There's pressure to deliver quickly without refactoring
- Component boundaries aren't clearly defined
- Developers are hesitant to break down functionality

### Solution/Structure to Avoid
Avoid creating components that:
- Manage multiple unrelated pieces of state
- Handle many different user interactions
- Contain business logic, UI rendering, and data fetching
- Have deeply nested conditional rendering

```jsx
// Example of a God Component to avoid
class DashboardPage extends Component {
  constructor(props) {
    super(props);
    this.state = {
      user: null,
      orders: [],
      products: [],
      notifications: [],
      activeTab: 'overview',
      isLoading: true,
      error: null,
      filterOptions: { /* complex filter state */ },
      sortOptions: { /* complex sort state */ },
      pagination: { /* pagination state */ },
      modalOpen: false,
      selectedItem: null,
      formData: { /* complex form state */ }
    };
  }
  
  // Dozens of methods for handling different aspects
  fetchUserData() { /* ... */ }
  fetchOrders() { /* ... */ }
  fetchProducts() { /* ... */ }
  handleTabChange() { /* ... */ }
  handleFilterChange() { /* ... */ }
  handleSort() { /* ... */ }
  handlePagination() { /* ... */ }
  openModal() { /* ... */ }
  closeModal() { /* ... */ }
  handleFormSubmit() { /* ... */ }
  processOrderData() { /* ... */ }
  // Many more methods...
  
  render() {
    // Hundreds of lines of JSX with complex conditional rendering
    return (
      <div className="dashboard">
        {this.state.isLoading && <LoadingSpinner />}
        {this.state.error && <ErrorMessage error={this.state.error} />}
        {!this.state.isLoading && !this.state.error && (
          <React.Fragment>
            <UserHeader user={this.state.user} />
            <TabNavigation 
              activeTab={this.state.activeTab} 
              onTabChange={this.handleTabChange}
            />
            {this.state.activeTab === 'overview' && (
              <OverviewPanel 
                data={this.processOverviewData()} 
                // many more props
              />
            )}
            {this.state.activeTab === 'orders' && (
              <div>
                <FilterBar 
                  options={this.state.filterOptions} 
                  onChange={this.handleFilterChange} 
                />
                <SortControls 
                  options={this.state.sortOptions} 
                  onChange={this.handleSort} 
                />
                <OrderList 
                  orders={this.state.orders} 
                  onItemSelect={this.openModal} 
                />
                <Pagination 
                  {...this.state.pagination} 
                  onChange={this.handlePagination} 
                />
              </div>
            )}
            {/* Many more tab conditions */}
            {this.state.modalOpen && (
              <Modal 
                item={this.state.selectedItem} 
                onClose={this.closeModal}
                onSubmit={this.handleFormSubmit}
                formData={this.state.formData}
                // many more props
              />
            )}
          </React.Fragment>
        )}
      </div>
    );
  }
}
```

### Consequences
- Difficult to understand and maintain
- Hard to test due to many interconnected responsibilities
- Prone to bugs due to complex state interactions
- Poor performance due to frequent re-renders
- Code duplication as developers avoid modifying the complex component
- Difficult to reuse any part of the functionality

### Prevention Strategy
1. **Component Decomposition**:
   - Break down by feature or responsibility
   - Extract reusable UI elements into components
   - Create container/presenter component pairs

2. **State Management**:
   - Use context API or state management libraries for shared state
   - Keep component state focused on UI concerns
   - Move business logic to hooks or services

3. **Architectural Guidelines**:
   - Establish clear component size limits (e.g., <300 lines)
   - Use static analysis tools to flag large components
   - Implement regular architectural reviews

### References
- Issue #187: "Dashboard Performance Issues"
- Refactoring PR #203: "Break down Dashboard Component"
- [Frontend Architecture Guidelines](https://example.com/frontend-architecture)

### Cross-References
- Related Mistake: Performance Issues in Dashboard
- Related Learning: Component Composition Patterns
- Related Pattern: Container/Presenter Pattern

---

## Anti-Pattern: Direct DOM Manipulation with React
**ID:** 2025-03-10-02  
**Pattern Name:** Direct DOM Manipulation with React  
**Category:** React Development

### Type
Anti-Pattern

### Problem
Bypassing React's virtual DOM by directly manipulating the DOM using vanilla JavaScript or jQuery within React components. This breaks React's declarative paradigm and can lead to state inconsistencies and difficult-to-track bugs.

### Context
This anti-pattern tends to emerge when:
- Developers with traditional JavaScript/jQuery experience are new to React
- Complex DOM manipulations are needed (animations, focus management)
- Third-party libraries require direct DOM access
- Performance optimizations are attempted incorrectly

### Solution/Structure to Avoid
Avoid direct DOM manipulations that bypass React's rendering cycle:

```jsx
// Anti-pattern example to avoid
class ChartComponent extends React.Component {
  componentDidMount() {
    // Direct DOM manipulation bypassing React
    const chart = document.getElementById('chart-container');
    chart.innerHTML = ''; // Clearing content
    
    const canvas = document.createElement('canvas');
    canvas.width = 500;
    canvas.height = 300;
    chart.appendChild(canvas);
    
    // More direct DOM manipulations
    const ctx = canvas.getContext('2d');
    ctx.fillStyle = '#3498db';
    // Drawing directly to canvas
    
    // Adding event listeners directly to DOM
    canvas.addEventListener('click', (e) => {
      // Handle click without updating React state
      const rect = canvas.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.beginPath();
      ctx.arc(x, y, 10, 0, 2 * Math.PI);
      ctx.fill();
    });
  }
  
  // No state updates to reflect the canvas changes
  
  render() {
    return (
      <div>
        <h2>Chart View</h2>
        <div id="chart-container"></div>
      </div>
    );
  }
}
```

### Consequences
- Component state becomes out of sync with the DOM
- React's virtual DOM diffing becomes ineffective
- Components don't re-render properly when props or state change
- Memory leaks from unremoved event listeners
- Difficult to debug issues as they occur outside React's lifecycle
- Testing becomes more difficult

### Prevention Strategy
1. **Use Refs for DOM Access**:
   - Use React refs for necessary DOM access
   - Confine DOM manipulations to appropriate lifecycle methods or hooks
   - Always update state to reflect DOM changes

2. **Leverage React Patterns**:
   - Use controlled components for forms
   - Implement state-driven UI updates
   - Use React portals for DOM positioning needs

3. **Integration Strategies**:
   - Properly wrap third-party libraries in React components
   - Use lifecycle methods to initialize and clean up DOM effects
   - Consider React-specific alternatives to DOM-manipulating libraries

```jsx
// Better approach using refs and React patterns
function ChartComponent() {
  const [points, setPoints] = useState([]);
  const canvasRef = useRef(null);
  
  // Use effect for initialization
  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    
    // Clear and redraw based on state
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    
    // Draw all points from state
    points.forEach(point => {
      ctx.beginPath();
      ctx.arc(point.x, point.y, 10, 0, 2 * Math.PI);
      ctx.fill();
    });
  }, [points]); // Redraw when points change
  
  // Handle click through React
  const handleCanvasClick = (e) => {
    const canvas = canvasRef.current;
    const rect = canvas.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    // Update state, which triggers redraw
    setPoints([...points, { x, y }]);
  };
  
  return (
    <div>
      <h2>Chart View</h2>
      <canvas
        ref={canvasRef}
        width={500}
        height={300}
        onClick={handleCanvasClick}
      />
    </div>
  );
}
```

### References
- Issue #142: "Chart Component State Inconsistencies"
- [React DOM Manipulation Best Practices](https://example.com/react-dom)
- Refactoring PR #156: "Fix Canvas Component"

### Cross-References
- Related Mistake: Chart Rendering Inconsistencies
- Related Learning: React Component Lifecycle
- Related Pattern: Ref Forwarding Pattern

---

## Anti-Pattern: Nested Callback Hell
**ID:** 2025-03-05-03  
**Pattern Name:** Nested Callback Hell  
**Category:** Asynchronous Programming

### Type
Anti-Pattern

### Problem
Deeply nested callbacks create code that is difficult to read, debug, and maintain. This "pyramid of doom" structure makes error handling inconsistent and obscures the logical flow of operations.

### Context
This anti-pattern tends to emerge when:
- Multiple asynchronous operations need to be executed in sequence
- Error handling is implemented inconsistently
- Developers are unfamiliar with modern async patterns
- Code evolves organically without refactoring

### Solution/Structure to Avoid
Avoid deeply nested callbacks and inconsistent error handling:

```javascript
// Anti-pattern example to avoid
function processUserOrder(userId, orderId, callback) {
  getUser(userId, (err, user) => {
    if (err) {
      console.error('Error fetching user:', err);
      return callback(err);
    }
    
    getOrder(orderId, (err, order) => {
      if (err) {
        console.error('Error fetching order:', err);
        return callback(err);
      }
      
      validateOrder(order, (err, isValid) => {
        if (err) {
          console.error('Error validating order:', err);
          return callback(err);
        }
        
        if (!isValid) {
          return callback(new Error('Invalid order'));
        }
        
        processPayment(user.paymentDetails, order.amount, (err, paymentResult) => {
          if (err) {
            console.error('Payment processing error:', err);
            return callback(err);
          }
          
          updateOrderStatus(order.id, 'paid', (err) => {
            if (err) {
              console.error('Error updating order status:', err);
              // Inconsistent error handling - payment already processed!
              return callback(err);
            }
            
            sendConfirmationEmail(user.email, order, (err) => {
              if (err) {
                // Just log, don't return error - inconsistent!
                console.error('Error sending email:', err);
              }
              
              // Final callback with success
              callback(null, {
                status: 'success',
                orderId: order.id,
                paymentId: paymentResult.id
              });
            });
          });
        });
      });
    });
  });
}
```

### Consequences
- Code becomes difficult to read and understand
- Error handling is inconsistent and prone to bugs
- Logic flow is obscured by nesting
- Difficult to maintain or extend
- Error stack traces become less useful
- Impossible to handle multiple concurrent operations

### Prevention Strategy
1. **Use Promises**:
   - Convert callback-based functions to return promises
   - Use Promise chaining to flatten the structure
   - Implement consistent error handling with .catch()

2. **Use Async/Await**:
   - Further simplify asynchronous code with async/await syntax
   - Use try/catch blocks for error handling
   - Maintain clear logical flow

3. **Implement Control Flow Patterns**:
   - For complex operations, use a state machine approach
   - Consider using libraries for complex flows (e.g., Redux-Saga)
   - Decompose operations into smaller, manageable functions

```javascript
// Better approach using async/await
async function processUserOrder(userId, orderId) {
  try {
    // Sequential operations with clear error handling
    const user = await getUser(userId);
    const order = await getOrder(orderId);
    
    const isValid = await validateOrder(order);
    if (!isValid) {
      throw new Error('Invalid order');
    }
    
    const paymentResult = await processPayment(user.paymentDetails, order.amount);
    await updateOrderStatus(order.id, 'paid');
    
    // Non-critical operation that shouldn't block the flow
    try {
      await sendConfirmationEmail(user.email, order);
    } catch (emailError) {
      // Log but continue, explicitly showing this is non-critical
      console.error('Error sending email:', emailError);
      // Could trigger monitoring or retry logic
    }
    
    return {
      status: 'success',
      orderId: order.id,
      paymentId: paymentResult.id
    };
  } catch (error) {
    // Centralized error handling
    console.error('Order processing failed:', error);
    
    // Handle specific errors with appropriate responses
    if (error.code === 'PAYMENT_FAILED') {
      await updateOrderStatus(orderId, 'payment_failed');
    }
    
    throw error; // Re-throw for caller to handle
  }
}
```

### References
- Issue #118: "Order Processing Error Handling"
- Refactoring PR #125: "Modernize Async Code"
- [JavaScript Asynchronous Programming Guide](https://example.com/async-js)

### Cross-References
- Related Mistake: Payment Processing Race Condition
- Related Learning: Modern JavaScript Async Patterns
- Related Pattern: Promise Chain Pattern
