# Task 4 – REST API Integration Proof

## Task Objective
The goal of Task 4 was to integrate an external **Incentive REST API** into the
Midas Core transaction-processing workflow and correctly apply incentive-based
logic to user balances.

---

## What Was Implemented

### 1. Incentive API Setup
- Successfully ran the provided `transaction-incentive-api.jar` locally.
- API endpoint used:
  - `POST http://localhost:8080/incentive`
- The API accepts a JSON-serialized `Transaction` object and returns an
  `Incentive` object containing an incentive `amount`.

---

### 2. REST Client Integration
- Created an `Incentive` model to deserialize API responses.
- Implemented an `IncentiveClient` using Spring’s `RestTemplate`.
- Posted validated transactions to the Incentive API.
- Safely handled API responses (defaulting to `0` if no incentive is returned).

---

### 3. Transaction Processing Logic
- After validating a transaction:
  - Sender balance is reduced by the transaction amount.
  - Recipient balance is increased by:
    - transaction amount
    - incentive amount
- Incentives are **not deducted from the sender**.
- Incentive value is persisted along with the transaction.

---

### 4. Persistence Changes
- Extended `TransactionRecord` entity to include:
  - sender
  - recipient
  - transaction amount
  - incentive amount
- All valid transactions are stored in the H2 database using Spring Data JPA.

---

## Verification

### Test Executed
- `TaskFourTests`

### Debugging Method
- Kafka consumer was debugged during transaction processing.
- User balances were inspected after all transactions were processed.
- Verified balances using repository lookups during test execution.

---

## Final Result

### Wilbur’s Final Balance
- **Calculated value:** `3089.42`
- **Rounded down (as required):** **3089**

✅ **Submitted answer:** `3089`

---

## Conclusion
Task 4 was completed successfully.
The Midas Core service now integrates:
- Kafka-based transaction ingestion
- External REST API communication
- Incentive-based business logic
- Correct balance updates and persistence

This completes Task 4 of the Software Engineering Job Simulation.
