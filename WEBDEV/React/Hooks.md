useMemo = [function, dependecy_array]
- used for caching (memoization), for expensive computations
- used for computing and returning values
- basically, updates function whenever dependency_array changes
- if dependencies haven't changed, useMemo returns cached value from previous render
- returns memoized value
const expensiveFunctionResult = useMemo(() => ..., [data1, data2])
```
import React, { useState, useMemo } from 'react';

function ExpensiveCalculation({ list, filter }) {
  // State for toggling a simple UI element
  const [toggle, setToggle] = useState(false);
  
  // Expensive calculation - filtering and processing a list
  const filteredAndProcessedList = useMemo(() => {
    console.log("Expensive calculation running...");
    
    // Filter the list based on the filter criteria
    const filtered = list.filter(item => item.name.includes(filter));
    
    // Perform some expensive processing on each item
    return filtered.map(item => {
      // Simulating an expensive calculation
      let result = item;
      for (let i = 0; i < 10000; i++) {
        result = { ...result, score: (result.score * 1.01) };
      }
      return result;
    });
  }, [list, filter]); // Only recalculate when list or filter changes
  
  return (
    <div>
      <button onClick={() => setToggle(!toggle)}>
        Toggle: {toggle ? 'ON' : 'OFF'}
      </button>
      
      <h2>Processed Items ({filteredAndProcessedList.length})</h2>
      <ul>
        {filteredAndProcessedList.map(item => (
          <li key={item.id}>
            {item.name}: {item.score.toFixed(2)}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

<hr>

useEffect = [function, dependecy_array]
- function runs whenever dependency array changes
- no array means function runs after every render
- empty array means function runs after initial render
- used to perform side effects in functional components. 
- Side effects include data fetching, DOM manipulation, setting up subscriptions, or anything else that interacts with the "world outside your component."
- returns cleanup function

useEffect vs useMemo:
The `useEffect` hook is designed to handle side effects, not to compute and return values. For computed values:
- Use `useMemo` for expensive calculations
- Use `useCallback` for memoized functions
- Use `useState` and `useEffect` together for derived state

Event Listeners w/ useEffect:
```
useEffect(() => {
  const handleResize = () => {
    setWindowWidth(window.innerWidth);
  };
  
  window.addEventListener('resize', handleResize);
  
  return () => {
    window.removeEventListener('resize', handleResize);
  };
}, []);
```

If you placed an event listener outside the component or at the top level, it would:
1. Only be created once when the module loads, not when your component renders
2. Not have access to component state/props (or would reference outdated values)
3. Continue to exist even after your component unmounts

Generally any event listener attached to global objects (window, document) should follow this pattern. It's considered a best practice in React to:
1. Set up the listener in a useEffect
2. Clean it up in the return function
3. Include any dependencies the listener function uses

<hr>

