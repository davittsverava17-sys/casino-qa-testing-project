 # Casino QA Testing Portfolio

## Project Overview

This project demonstrates practical QA testing skills through a casino gaming API testing environment. It focuses on API functionality, authentication, database validation, event processing, performance testing, and monitoring.

## Testing Areas

- **API Testing:** Postman, HTTP methods, status codes, request and response validation.
- **Authentication:** JWT access and refresh tokens, token expiration, and protected endpoints.
- **Database Testing:** MySQL queries, wallet balance validation, bets, and transactions.
- **Event Processing:** Kafka event verification and webhook signature validation.
- **Performance Testing:** k6 load testing, virtual users, response times, and error rates.
- **Monitoring:** Prometheus metrics and Grafana dashboards.
- **Functional Testing:** BET, WIN, LOSS, duplicate requests, and wallet balance consistency.
- **Test Design:** Positive and negative scenarios, boundary cases, and jackpot test cases.

## Tools & Technologies

Postman · JavaScript · Node.js · Express.js · MySQL · Apache Kafka · k6 · Prometheus · Grafana

## Key Testing Scenarios

- Verify successful and unsuccessful API requests.
- Validate JWT authentication and token refresh behavior.
- Check wallet balance changes after betting transactions.
- Verify duplicate event handling and HTTP 409 responses.
- Compare application behavior with database records and Kafka events.
- Analyze performance metrics and failed requests during load tests.
- Design test cases for casino gaming and jackpot functionality.

## Project Demo

Video demonstration: [https://drive.google.com/file/d/1P-t3lbt7eu69iDto6ipU2xGAqK1ePUWO/view?usp=sharing]

## Project Status

This portfolio is a work in progress. Test cases, API collections, test scripts, screenshots, and additional testing documentation will be added as the project develops.


## Postman API Testing — Test Evidence

The following screenshots demonstrate API testing scenarios executed using Postman.

### 1. Successful BET
Verifies that a valid BET request is processed successfully and returns HTTP 200.

![Successful BET](screenshots/postman/01-successful-bet.png)

### 2. Insufficient Balance
Verifies that a BET request is rejected when the user has insufficient funds.

![Insufficient Balance](screenshots/postman/02-insufficient-balance.png)

### 3. Invalid JWT
Verifies that an invalid or expired access token is rejected with HTTP 401.

![Invalid JWT](screenshots/postman/03-invalid-jwt.png)

### 4. User ID Mismatch
Verifies that a user cannot place a bet on behalf of another user.

![User ID Mismatch](screenshots/postman/04-user-id-mismatch.png)

### 5. Duplicate Event ID
Verifies that a repeated event ID is detected and rejected with HTTP 409.

![Duplicate Event ID](screenshots/postman/05-duplicate-event-id.png)

### 6. Invalid Game ID
Verifies that a request referencing a nonexistent game is rejected with HTTP 404.

![Invalid Game ID](screenshots/postman/06-invalid-game-id.png)
