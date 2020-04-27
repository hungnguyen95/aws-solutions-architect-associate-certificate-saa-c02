# 4. AWS Step Functions

- Build serverless visual workflow to orchestrate your Lambda functions
- Represent flow as a JSON **state machine**
- Features: sequence, parallel, conditions, timeouts, error handling…
- Can also integrate with EC2, ECS, On premise servers, API Gateway
- Maximum execution time of 1 year
- Possibility to implement human approval feature
- Use cases:
    - Order fulfillment
    - Data processing
    - Web applications
    - Any workflow

---

# Visual workflow in Step Functions

![4%20AWS%20Step%20Functions/Untitled.png](4%20AWS%20Step%20Functions/Untitled.png)

---

# AWS SWF – Simple Workflow Service

- Coordinate work amongst applications
- Code runs on EC2 (not serverless)
- 1 year max runtime
- Concept of “activity step” and “decision step”
- Has built-in “human intervention” step
- Example: order fulfilment from web to warehouse to delivery
- **Step Functions is recommended to be used for new applications, except:**
    - If you need external signals to intervene in the processes
    - If you need child processes that return values to parent processes