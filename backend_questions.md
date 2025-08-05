### Concurrency: Go vs Node.js (Advanced)

**Question:**         
In a backend service, you need to process multiple independent tasks concurrently, ensuring that all tasks complete before sending the final response.  
How would you i  mplement this in:

1. **Go** using goroutines and channels  
2. **Node.js** using async/await and `Promise.all`

**Answer Outline:**

- **Go:**
  - Use goroutines to sp  awn concurrent tasks.
  - Communicate results or errors through channels.
  - Use `sync.WaitGroup` to wait for all tasks to finish.
  - Example:
    ```go   
    var wg sync.WaitGroup  
    for _, task := range tasks {
        wg.Add(1)
        go func(t Task) {
            defer wg.Done()
            processTask(t)
        }(task)
    }
    wg.Wait()  
    ```

- **Node.js:**
  - Wrap each async task in a Promise.
  - Use `Promise.all` to run them concurrently.
  - Handle errors via `try/catch` or Promise rejection handling.
  - Example:
    ```javascript
    await Promise.all(tasks.map(async task => {
        await processTask(task);vv
    }));
    ```

**Rationale:**  
- Compares Go’s concurrency primitives (goroutines, channels, WaitGroup) and Node.js’s event-loop approach (Promises, async/await).  
- Emphasizes differences in runtime behavior, error propagation, debugging complexity, and memory usage.

---

