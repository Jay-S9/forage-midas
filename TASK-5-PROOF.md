# JPMorgan Chase – Advanced Software Engineering (Forage)

## Task 5: REST API Controller – Completion Proof

### Objective
Expose a REST API endpoint that allows users to query their account balance.

### Implementation Summary
- Created a Spring REST controller exposing a `GET /balance` endpoint
- Accepted `userId` as a request parameter
- Returned a JSON-serialized `Balance` object
- Defaulted to balance `0` when a user does not exist
- Configured Spring Boot application to run on port **33400**
- Ensured REST API runs alongside Kafka consumer and database logic

### System Integration
- REST Controller integrated into existing Spring Boot service
- Coexists with:
  - Kafka message consumer
  - H2 in-memory database
  - External Incentive REST API

### Verification Output

---begin output ---
Balance {amount=0.0}
Balance {amount=1326.98}
Balance {amount=2567.52}
Balance {amount=2740.33}
Balance {amount=140.96999}
Balance {amount=10.419973}
Balance {amount=845.49005}
Balance {amount=657.49}
Balance {amount=99.189995}
Balance {amount=3434.0002}
Balance {amount=2157.1902}
Balance {amount=779421.3}
Balance {amount=0.0}
---end output ---

### Notes
This task completes the Midas Core system by exposing user-facing balance data through a REST API, demonstrating full-stack backend integration across messaging, persistence, and HTTP interfaces.
