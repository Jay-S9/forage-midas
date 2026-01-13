# JPMorgan Chase – Advanced Software Engineering (Forage)

## Task 3: H2 Integration – Completion Proof

### Objective
Integrate an in-memory SQL database (H2) with Spring Boot using JPA, validate Kafka-driven transactions, and persist valid financial records while maintaining correct user balances.

---

### Key Implementations

- Integrated **H2 in-memory database** via Spring Boot
- Used **Spring Data JPA** for persistence
- Created `TransactionRecord` entity with:
  - many-to-one relationship to sender (`UserRecord`)
  - many-to-one relationship to recipient (`UserRecord`)
- Implemented transactional consistency using `@Transactional`
- Validated transactions:
  - sender exists
  - recipient exists
  - sender has sufficient balance
- Discarded invalid transactions safely
- Updated sender & recipient balances atomically
- Persisted valid transactions

---

### System Flow (High Level)

Kafka Transaction  
→ Kafka Listener  
→ Validation Logic  
→ Balance Updates  
→ JPA Persistence (H2)

---

### Verification Method

- Executed `TaskThreeTests`
- Used debugger to inspect live JPA state
- Observed balance changes after all Kafka transactions
- Recorded final balance of **waldorf** user

---

### Task 3 Verification Output

**Final Waldorf Balance (rounded down):**

444


---

### Notes
This task demonstrates real-world backend concepts:
- event-driven processing
- transactional integrity
- relational data modeling
- database-backed financial validation

All logic verified through debugger-based inspection as required by the task.
