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

7. Invalid Amount

Verifies that the API rejects a BET request with an invalid amount, such as a zero or negative value, and returns the expected error response.

![Invalid Amount](screenshots/postman/07-invalid-Amount.PNG)

8. WIN Processing

Verifies that a WIN request is processed successfully and returns the expected API response. Postman test scripts are used to validate the HTTP status code and response data.

![WIN Processing](screenshots/postman/09-win-processing.png)

9. LOSS Processing

Verifies that a LOSS transaction is processed correctly and that the API returns the expected response. The test checks the transaction result and helps validate the expected behavior of the betting flow.

![LOSS Processing](screenshots/postman/10-loss-processing.png)








## Kafka Event Testing

Kafka testing was performed to verify event publishing, message content, and duplicate event handling in the casino API.

### Test Scenarios

- Verified that the `bets` Kafka topic exists.
- Consumed and inspected `BET_PLACED` events using the Kafka Console Consumer.
- Checked event fields, including `eventId`, `betId`, `userId`, `gameId`, and `amount`.
- Sent a duplicate BET request using an already processed `eventId`.
- Verified that the API rejected the duplicate request with `409 Conflict` and returned `Event already processed`.
- Queried the MySQL `bets` table to verify that the tested `eventId` had only one record.

### Screenshots

**1. Kafka Topic Verification**

![Kafka Topics](screenshots/kafka/01-kafka-topics.png)

**2. Kafka Consumer — BET_PLACED Event**

![Kafka Consumer BET Event](screenshots/kafka/02-kafka-consumer-bet-event.png)

**3. Duplicate Event Rejection — HTTP 409**

![Duplicate Event Rejection](screenshots/kafka/03-duplicate-event-rejected.png)

**4. SQL Verification — Duplicate Prevention**

![SQL Duplicate Verification](screenshots/kafka/04-sql-duplicate-verification.png)





## Casino Frontend

The project includes a casino gaming interface with Blackjack, Roulette, and Slots. This section demonstrates the application UI used for functional testing.

### Frontend Screenshot

![Casino Frontend](screenshots/frontend/01-casino-frontend.png)



## Playwright E2E Testing

Playwright was used to automate end-to-end testing of the casino application across three browser projects: Chromium, Firefox, and WebKit.

### Test Coverage

- Executed automated end-to-end tests across three browser engines.
- Verified the tested casino application flow.
- Reviewed test execution results and generated Playwright reports.
- Confirmed that the tested scenarios passed in the configured browser projects.

### Test Execution Report

The Playwright HTML report provides a detailed overview of test execution results, including test status, duration, and browser project.

![Playwright Test Report](screenshots/playwright/01-playwright-test-pass.png)



 ## Webhook Testing

Webhook testing was performed to verify secure event delivery from the Casino API to the Webhook Receiver.

### Test Coverage

- **Valid HMAC SHA-256 Signature:** Verified that a valid webhook signature is accepted.
- **Webhook Payload Validation:** Checked the received BET event payload, including `eventId`, `betId`, `userId`, `gameId`, `amount`, `result`, and `timestamp`.
- **Invalid Signature:** Verified that a request with an invalid signature is rejected with HTTP `401 Unauthorized`.

### Webhook Testing Screenshots

**1. Valid Signature Verification**

![Valid Webhook Signature](screenshots/webhook/01-webhook-signature-verification.png)

**2. Webhook Payload**

![Webhook Payload](screenshots/webhook/02-webhook-payload.png)

**3. Invalid Signature Rejection**

![Invalid Webhook Signature](screenshots/webhook/03-invalid-signature.png)



## WebSocket Testing

WebSocket testing was performed using the browser's Developer Tools to inspect real-time communication in the casino application.

### Test Coverage

- **WebSocket Connection:** Checked the WebSocket connection in the browser's Network panel.
- **Messages / Frames:** Inspected WebSocket messages to identify sent and received data.
- **Game Action Behavior:** Performed a game action and verified that a new WebSocket message appeared.
- **Real-Time Communication:** Observed message activity during interaction with the casino application.

### WebSocket Testing Screenshots

**1. WebSocket Connection**

![WebSocket Connection](screenshots/websocket/01-websocket-connection.png)

**2. WebSocket Messages / Frames**

![WebSocket Messages](screenshots/websocket/02-websocket-messages.png)

**3. WebSocket Message During Game Action**

![WebSocket Game Action](screenshots/websocket/03-websocket-game-action.png)

