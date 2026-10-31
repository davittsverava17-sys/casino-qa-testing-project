# Jackpot System – QA Test Cases

## Project Information

| Field | Details |
|---|---|
| Project | Casino QA Testing Project |
| Feature | Progressive Jackpot |
| Games | Slots & Roulette |
| Test Type | Functional, Negative, Edge Cases |
| Jackpot Contribution | 5% of losing bets |
| Testing Tools | Postman, MySQL, Chrome DevTools |
| Status | Test Cases Documented |

---

## 1. Positive Test Cases

### TC-JP-001: Verify Jackpot Visibility in Slots

**Preconditions:**
- User is logged in.
- Slots game is available.

**Steps:**
1. Open the Slots game.
2. Locate the Progressive Jackpot panel.
3. Verify the displayed jackpot amount.

**Expected Result:**
- Jackpot panel is visible.
- Jackpot amount is displayed correctly.
 

**Priority:** High

**Status:** Not Run

---

### TC-JP-002: Verify Jackpot Visibility in Roulette

**Steps:**
1. Open the Roulette game.
2. Locate the Jackpot panel.
3. Verify the displayed amount.

**Expected Result:**
- Jackpot is displayed correctly in Roulette.
- Jackpot amount matches the backend value.

**Priority:** High

**Status:** Not Run

---

### TC-JP-003: Verify 5% Jackpot Contribution

**Preconditions:**
- Jackpot is initialized.
- User has sufficient balance.

**Steps:**
1. Record the current jackpot amount.
2. Place a losing bet of 1,000.
3. Wait for bet settlement.
4. Check the updated jackpot amount.

**Expected Result:**
- 50₾ is added to the jackpot.
- New jackpot amount equals the previous amount + 50.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-004: Verify Jackpot Accumulation After Multiple Losing Bets

**Steps:**
1. Record the initial jackpot.
2. Place three losing bets of 1,000 each.
3. Check the jackpot amount.

**Expected Result:**
- Total contribution is 150.
- Jackpot increases by the correct amount.

**Priority:** High

**Status:** Not Run

---

### TC-JP-005: Verify Jackpot Payout

**Preconditions:**
- Jackpot win condition is configured.
- User is eligible to win.

**Steps:**
1. Record the user's initial wallet balance.
2. Trigger a valid jackpot win.
3. Wait for settlement.
4. Check the wallet balance.

**Expected Result:**
- Jackpot prize is credited to the correct user.
- Wallet balance increases by the awarded amount.
- Payout is recorded successfully.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-006: Verify Jackpot Reset After Winning

**Steps:**
1. Record the jackpot amount before winning.
2. Trigger a jackpot win.
3. Check the jackpot amount after payout.

**Expected Result:**
- Jackpot resets to its configured initial value.
- The displayed amount matches the backend value.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-007: Verify WebSocket Jackpot Updates

**Steps:**
1. Open the game in the browser.
2. Open Chrome DevTools → Network → WS.
3. Place a losing bet.
4. Observe WebSocket messages.

**Expected Result:**
- WebSocket connection remains active.
- Jackpot update is received.
- Frontend displays the updated amount without page refresh.

**Priority:** High

**Status:** Not Run

---

## 2. Negative Test Cases

### TC-JP-008: Verify Winning Bets Do Not Increase Jackpot

**Steps:**
1. Record the initial jackpot.
2. Place a winning bet.
3. Check the jackpot amount.

**Expected Result:**
- No losing-bet contribution is added.
- Jackpot remains unchanged unless another configured rule applies.

**Priority:** High

**Status:** Not Run

---

### TC-JP-009: Verify Insufficient Wallet Balance

**Steps:**
1. Set or use a test account with insufficient funds.
2. Attempt to place a bet.
3. Check the API response and wallet balance.

**Expected Result:**
- Bet is rejected.
- No jackpot contribution is generated.
- Wallet balance remains unchanged.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-010: Verify Duplicate Bet Event

**Steps:**
1. Submit a bet with a unique eventId.
2. Submit the same request again using the same eventId.
3. Check the API response.

**Expected Result:**
- Duplicate event is rejected.
- Original bet is not processed twice.
- No duplicate jackpot contribution or payout occurs.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-011: Verify Invalid Bet Amount

**Steps:**
1. Submit a bet with amount = 0.
2. Submit a bet with a negative amount.
3. Check API responses.

**Expected Result:**
- Invalid amounts are rejected.
- Wallet and jackpot remain unchanged.

**Priority:** High

**Status:** Not Run

---

### TC-JP-012: Verify Unauthorized Jackpot Access

**Steps:**
1. Send a jackpot-related request without an authorization token.
2. Repeat with an invalid token.

**Expected Result:**
- Unauthorized requests are rejected.
- No wallet or jackpot changes occur.

**Priority:** High

**Status:** Not Run

---

### TC-JP-013: Verify Jackpot Payout Is Not Duplicated

**Steps:**
1. Trigger a valid jackpot win.
2. Submit the same payout event again.
3. Check wallet balance and transaction history.

**Expected Result:**
- Only one payout is credited.
- Duplicate payout is rejected.
- Wallet balance is not increased twice.

**Priority:** Critical

**Status:** Not Run

---

## 3. Edge Test Cases

### TC-JP-014: Verify Minimum Bet Contribution

**Steps:**
1. Place a losing bet using the minimum allowed amount.
2. Check the jackpot contribution.

**Expected Result:**
- Contribution equals 5% of the losing bet.
- Monetary rounding follows the configured currency precision.

**Priority:** Medium

**Status:** Not Run

---

### TC-JP-015: Verify Maximum Allowed Bet

**Steps:**
1. Place a losing bet using the maximum allowed amount.
2. Check the jackpot contribution.

**Expected Result:**
- Bet is processed within configured limits.
- Jackpot contribution is calculated correctly.

**Priority:** High

**Status:** Not Run

---

### TC-JP-016: Verify Concurrent Losing Bets

**Steps:**
1. Open multiple sessions or use concurrent API requests.
2. Submit multiple losing bets simultaneously.
3. Check the final jackpot amount.

**Expected Result:**
- All valid contributions are accounted for exactly once.
- No updates are lost.
- Final jackpot amount is correct.

**Priority:** Critical

**Status:** Not Run

---

### TC-JP-017: Verify WebSocket Reconnection

**Steps:**
1. Connect to the WebSocket.
2. Disconnect the network or close the connection.
3. Reconnect.
4. Check the latest jackpot amount.

**Expected Result:**
- WebSocket reconnects successfully if reconnection is supported.
- Client receives the latest jackpot value.
- No duplicate updates are processed.

**Priority:** Medium

**Status:** Not Run

---

### TC-JP-018: Verify Jackpot Amount After Server Restart

**Steps:**
1. Record the current jackpot amount.
2. Restart the backend server.
3. Reopen the game.
4. Check the jackpot amount.

**Expected Result:**
- Jackpot amount is restored from persistent storage.
- No unexpected reset or data loss occurs.

**Priority:** High

**Status:** Not Run

---

### TC-JP-019: Verify Jackpot Amount Formatting

**Steps:**
1. Open Slots and Roulette.
2. Check jackpot values with decimal amounts.
3. Compare frontend and backend values.

**Expected Result:**
- Amount is displayed in the correct currency format.
- No incorrect rounding or formatting occurs.
- Backend continues using numeric values.

**Priority:** Medium

**Status:** Not Run

---

### TC-JP-020: Verify Jackpot Consistency Between Frontend and Database

**Steps:**
1. Record the jackpot amount displayed in the frontend.
2. Query the corresponding jackpot value in the database.
3. Compare both values after a losing bet and after a jackpot win.

**Expected Result:**
- Frontend and database values are consistent.
- No stale or incorrect jackpot value is displayed.

**Priority:** Critical

**Status:** Not Run

---

## 4. Test Execution Summary

| Category | Test Cases |
|---|---:|
| Positive | 7 |
| Negative | 6 |
| Edge Cases | 7 |
| **Total** | **20** |

### Test Execution Status

- Not Run: 20
- Passed: 0
- Failed: 0
- Blocked: 0

*Test execution results must be updated after actual execution.*

## 5. QA Notes

- All financial calculations must be verified against backend and database values.
- Duplicate events must not result in duplicate payouts.
- Jackpot contributions must be calculated only according to configured business rules.
- WebSocket updates must reflect the latest jackpot state.
- All payout operations must be traceable through transaction records.
