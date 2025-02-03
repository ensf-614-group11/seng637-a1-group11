# **Defect Report** 
### **Group 11**
### **Contributors**: Steven Au, Laurel Flanagan, Rhys Wickens, Austen Zhang
---

## Defect ID: 1

### **Title:** Money Market Balance Inquiry Issue: "Unknown error" message with $500 withdraw displays when selecting money market under balance inquiry for card 1  
**Work Item Type:** Bug  
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression;  
**Priority:** 2  
**Severity:** 1 - Critical  

- **Version in which bug was found:** V1.0
- **Bug was found:** The bug was found in the exploratory testing.  
- **Use Case:** Inquiry  
- **Function being tested:** Balance inquiry for card 1 with access to checking and savings account.  
- **Initial state of system:** Selecting money market account to inquire about the balance.  

#### Expected Outcome:
GUI message indicating that the card holder does not have a Money Market account.  

#### Actual Outcome:
GUI displays message "Unknown Error", and $500 is ejected from the machine. System asks the user if they would like to do another transaction.  

#### Priority:
2 - High  
- **Reason:** Withdrawals should not be happening when inquiries are made. However, this error may only be experienced by a subset of customers. The pathway to get to this error is more specific.  

#### Severity:
1 - Critical  
- **Reason:** Critical severity ranking was assigned because although the issue does not seem to impact operations, the team will want to confirm that the error is isolated and does not trigger unintended withdrawals of $500 as indicated in the logging message. Withdrawals should not be happening when inquiries to the system are made.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 4 on interface number pad to access balance inquiry (option 4).  
7. Press 2 on interface number pad to access money market account (option 2).  
8. **ERROR:** "Unknown error" message appears on the GUI screen, $500 is ejected from the machine, and system shows account details from savings account. Logging message indicates a SUCCESS response for a withdrawal of $500 when an inquiry was made.  

#### Log:
```
Message:   INQUIRY  CARD# 1 TRANS# 1 FROM  1 NO TO NO AMOUNT
Response:  SUCCESS
Dispensed: $500.00
```

#### Receipt:
```
Fri Jan 31 14:15:49 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
INQUIRY FROM: SVGS

TOTAL BAL: $1000.00
AVAILABLE: $1000.00
```

### **Regression Testing:**
- **Regression Test Version:** V1.1
- **Regression Test Outcome:** Error from V1.0 is still present in V1.1 Error is found when following "Steps to Reproduce"
**Steps to Reproduce:** 
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 4 on interface number pad to access balance inquiry (option 4).  
7. Press 2 on interface number pad to access money market account (option 2).  
8. **ERROR:** "Unknown error" message appears on the GUI screen, $500 is ejected from the machine, and system shows account details from savings account. Logging message indicates a SUCCESS response for a withdrawal of $500 when an inquiry was made.

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  
- **Note:** Card number "1" should not have access to a Money Market account.  

**Found In:** 1.0  

---

## Defect ID: 2

### **Title:** System freezes when incorrect card # entered with incorrect PIN (i.e., Card #3 with PIN 42)  
**Work Item Type:** Bug  
**State:** Closed  
**Reason:** Fixed  
**Tags:** Exploratory; Regression;  
**Priority:** 2  
**Severity:** 2 - High  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found from exploratory testing.  
- **Use Case:** Invalid PIN Extension  
- **Function being tested:** System rejects an invalid card and PIN.  
- **Initial state of system:** System is requesting user to insert card.  

#### Expected Outcome:
After incorrect card is entered, system should display an error message indicating that the card number does not exist.  

#### Actual Outcome:
After incorrect card is entered, system asks for PIN. When PIN is entered, system freezes and does not display any message.  

#### Priority:
2 - High  
- **Reason:** This error is customer-facing and may cause inconveniences, but the issue does not impact customer accounts.  

#### Severity:
2 - High  
- **Reason:** High because the error does not have significant impact on the core functionality of the ATM system.  

### Steps to Reproduce:
1. System initial state: ATM System is off.  
2. Startup ATM System by pressing 'ON'.  
3. Operator adds bills to system (10).  
4. Insert debit card.  
5. Enter card #3 (invalid card).  
6. Enter an incorrect PIN, in this case, use 908.  
7. System freezes with no message. 'CANCEL' button does nothing, 'OFF' button does nothing.  

### Regression Testing:
- **Regression Test Version:** V1.1
- **Regression Test Outcome:** Bug is no longer present in V1.1. Error is no longer present when following "Steps to Reproduce"

### System Info:
- **Version in which bug was found:** V1.0  

**Found In:** 1.0  

---

## Defect ID: 3

### **Title:** Test Case #14: Withdrawn amount incorrect based on selection  
**Work Item Type:** Bug  
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression  
**Priority:** 1  
**Severity:** 1 - Critical  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  =
- **Test Case:** 14  
- **Use Case:** Withdrawal  
- **Function being tested:** System performs a legitimate withdrawal transaction properly.  
- **Initial state of system:** System is displaying the menu of withdrawal amounts.  

#### Expected Outcome:
Amount chosen is withdrawn, system prints a correct receipt showing withdrawal amount and balance correctly updated, system records transaction correctly in the log.  

#### Actual Outcome:
Amount withdrawn is not correct. Amount is actually the next available option on the menu of withdrawal amounts (e.g., inputting a request to withdraw $20 will withdraw $40, request for $40 will withdraw $60, etc.).  

#### Priority:
1 - Critical  
- **Reason:** "Withdrawal" queries are part of ATM core functionality.  

#### Severity:
1 - Critical  
- **Reason:** Issues with "withdrawal" queries impact business operations by introducing risk into accounting error. Additionally, there are major impacts to customer usability and experience.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Enter card number (choose card number 1).  
4. Enter correct PIN for card number 1.  
5. Press 1 on interface number pad to access withdrawal (option 1).  
6. Press 1 to request withdrawal from checking account (option 1).  
7. Select amount to withdraw. Choose an amount that the system currently has and which is not greater than the account balance.  
8. **ERROR:** Amount you clicked is not the amount that was withdrawn.  
   - **Note:** Error present for all accounts.  

#### Log:
```
Message:   WITHDRAW CARD# 1 TRANS# 7 FROM  0 NO TO $60.00
Response:  SUCCESS
Dispensed: $60.00
```

#### Receipt:
```
Thu Jan 30 10:53:14 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #7
WITHDRAWAL FROM: CHKG
AMOUNT: $60.00
TOTAL BAL: $40.00
AVAILABLE: $40.00
```

### **Regression Testing:**
**Regression Test Version:** V1.1  
**Regression Test Outcome:** Bug is fixed in V1.1 but the required "Expected Outcome" is still not fully met. The system correctly executes the transaction, withdrawal request successfully completes for the expected amount. However, the receipt still shows the wrong card number. The the dollar sign is also missing on the GUI for the $60 option (it was present previously).The fix does not meet the expectations of "Expected Outcome" to close this bug.  
**Steps to Reproduce:**  
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Enter card number (choose card number 1).  
4. Enter correct PIN for card number 1.  
5. Press 1 on interface number pad to access withdrawal (option 1).  
6. Press 1 to request withdrawal from checking account (option 1).  
7. Select amount to withdraw. Choose an amount that the system currently has and which is not greater than the account balance.  
8. **ERROR:** System correctly executes the transaction. However, the dollar sign is missing for the $60 option, and the receipt still shows the wrong card number (receipt shows card 2, when transaction was done using card number 1).

**Log:**
```
Message:   WITHDRAW CARD# 1 TRANS# 1 FROM  0 NO TO $40.00
Response:  SUCCESS
Dispensed: $40.00
```

**Receipt:**
```
Thu Jan 30 11:34:38 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
WITHDRAWAL FROM: CHKG
AMOUNT: $40.00
TOTAL BAL: $60.00
AVAILABLE: $60.00
```

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  

**Found In:** 1.0  

---

## Defect ID: 4

### **Title:** Test Case #22: System does not handle correctly depositing requested amount into account  
**Work Item Type:** Bug  
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression  
**Priority:** 1  
**Severity:** 1 - Critical  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Test Case:** 22  
- **Use Case:** Deposit  
- **Function being tested:** System performs a legitimate deposit transaction properly.  
- **Initial state of system:** System is requesting that the customer insert an envelope.  

#### Expected Outcome:
System accepts envelope; System prints a correct receipt showing amount and correct updated balance; System records transaction correctly in log (showing message to the bank, approval back, and acceptance of envelope).  

#### Actual Outcome:
The amount deposited is not correctly reflected in the updated balance. The updated balance is $10 less than deposited.  

#### Priority:
1 - Critical  
- **Reason:** "Deposit" queries are part of ATM core functionality. System is not functioning as designed. This is a common pathway of interaction for customers.  

#### Severity:
1 - Critical  
- **Reason:** Issues with deposit transactions impact business operations by introducing risk to accounting. Additionally, there are impacts to customer usability and experience. Errors in these areas will require additional staff hours allocated for customer service and accounting.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 2 on interface number pad to access deposit (option 2).  
7. Press 1 on interface number pad to request deposit to checking account (option 1).  
8. Enter amount to deposit.  
9. Click to insert envelope.  
10. **ERROR:** Total balance updated to $10 less than what was deposited (e.g., depositing $40 results in a balance increase of $30).  

#### Log:
```
INIT_DEP CARD# 1 TRANS# 3 NO FROM TO  0 $40.00
Response:  SUCCESS
Envelope:  received
Message:   COMP_DEP CARD# 1 TRANS# 3 NO FROM TO  0 $40.00
Response:  SUCCESS
```

#### Receipt:
```
Thu Jan 30 11:05:27 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #3
DEPOSIT TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $130.00
AVAILABLE: $100.00
```

### **Regression Testing:**
**Regression Test Version:** V1.1  
**Regression Test Outcome:** The transaction is processed but the updated balance does still not equal the expected value. The updated balance is now $0.10 less than the expected value.  
**Steps to Reproduce:**  
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 2 on interface number pad to access deposit (option 2).  
7. Press 1 on interface number pad to request deposit to checking account (option 1).  
8. Enter amount to deposit.  
9. Click to insert envelope.  
10. **ERROR:** Total balance updated to $0.10 less than what was deposited (e.g., depositing $40 results in a balance increase of $39.90).  

**Log:**
```
Message:   INIT_DEP CARD# 1 TRANS# 1 NO FROM TO  0 $40.00
Response:  SUCCESS
Envelope:  received
Message:   COMP_DEP CARD# 1 TRANS# 1 NO FROM TO  0 $40.00
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:37:59 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
DEPOSIT TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $139.90
AVAILABLE: $100.00
```

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  

**Found In:** 1.0  

---

## Defect ID: 5

### **Title:** Test Case #29: Receipt is incorrect after completing a successful transfer - to and from accounts shown backwards  
**Work Item Type:** Bug   
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression  
**Priority:** 2  
**Severity:** 3 - Medium  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Test Case:** 29  
- **Use Case:** Transfer  
- **Function being tested:** System performs a legitimate transfer transaction properly.  
- **Initial state of system:** System is displaying a request for the customer to type a dollar amount.  

#### Expected Outcome:
System prints a correct receipt showing amount and correct updated balance; System records transaction correctly in the log (showing both the message to the bank and the approval back).  

#### Actual Outcome:
System shows that money is being transferred to and from the wrong accounts (i.e., opposite of the selections for "to" and "from" made in the menu).  

#### Priority:
2 - High  
- **Reason:** The issue is customer-facing, and correctness of a "Transfer Inquiry" is part of the core functionality of ATM. Transfers are being completed as expected, but information is not showing up properly. Errors on receipts may cause confusion when customers interact with the system.  

#### Severity:
3 - Medium  
- **Reason:** The issues have lower impact on business operations. The issue appears to be isolated to the information returned to the customer, but the desired transaction is actually processed correctly.  

### Steps to Reproduce:
1. Turn system on, enter amount of bills in system.  
2. Click insert card, enter card number, enter correct PIN.  
3. Click Transfer (option 3).  
4. Click account to transfer from (e.g., savings).  
5. Click account to transfer to (e.g., checking).  
6. Enter amount to transfer (e.g., $20).  
7. **ERROR:** Display message is incorrect, says accounts "to" and "from" backwards of what was selected (e.g., CHKG to SVGS).  

#### Log:
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $39.50
Response:  SUCCESS
```

#### Receipt:
```
Thu Jan 30 11:11:59 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $39.50
TOTAL BAL: $1039.50
AVAILABLE: $1039.50
```

### **Regression Testing:**
**Regression Test Version:** V1.1  
**Regression Test Outcome:** This update fixes the receipt to show the correct amount of the transfer. However, the accounts to and from listed on the receipt and the card number are still incorrect.  
**Steps to Reproduce:** 
1. Turn system on, enter amount of bills in system.  
2. Click insert card, enter card number, enter correct PIN.  
3. Click Transfer (option 3).  
4. Click account to transfer from (e.g., savings).  
5. Click account to transfer to (e.g., checking).  
6. Enter amount to transfer (e.g., $20).  
7. **ERROR:** Display message is incorrect, says accounts "to" and "from" backwards of what was selected (e.g., CHKG to SVGS). The receipt is showing the wrong card number. A transfer inquiry for CARD 1 should be correctly indicated on the receipt.

**Log:**
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $40.00
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:40:02 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $1040.00
AVAILABLE: $1040.00
```

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  

**Found In:** 1.0  



### System Info:
- **Function being tested:** Transferring money.  
- **Initial state of system:** System asking for amount of money to transfer.  
- **Expected Outcome:** System shows that money is being transferred to and from the correct accounts.  
- **Actual Outcome:** System shows that money is being transferred from the wrong accounts.  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Status after regression:** The bug was still present in the regression testing.  

**Found In:** 1.0  

---

## Defect ID: 6

### **Title:** Test Case #29: Incorrect amount is transferred when making a transfer request  
**Work Item Type:** Bug   
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression   
**Priority:** 1  
**Severity:** 2 - High  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Test Case:** 29  
- **Use Case:** Transfer  
- **Function being tested:** System performs a legitimate transfer transaction properly.  
- **Initial state of system:** System is displaying a request for the customer to type a dollar amount.  

#### Expected Outcome:
System prints a correct receipt showing amount and correct updated balance; System records transaction correctly in the log (showing both the message to the bank and the approval back).  

#### Actual Outcome:
System does not transfer the specified amount. System transfers an amount which is $0.50 less than the requested transfer amount.  

#### Priority:
1 - Critical  
- **Reason:** "Transfer" queries are part of ATM core functionality. System is not functionally meeting requirements.  

#### Severity:
2 - High  
- **Reason:** Received ranking due to impact on business but should not result in an introduction of risk. Impacts customer usability and experience.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 3 on interface number pad to access transfer (option 2).  
7. Press 1 on interface number pad to request transfer from account (option 1).  
8. Press 2 on interface number pad to request transfer to savings account (option 2).  
9. Enter amount to transfer ($20.00).  
10. **ERROR:** Amount transferred and updated balance are incorrect - the amount shown is $0.50 less than what was requested to be transferred.  

#### Log:
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $39.50
Response:  SUCCESS
```

#### Receipt:
```
Thu Jan 30 11:11:59 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $39.50
TOTAL BAL: $1039.50
AVAILABLE: $1039.50
```

### **Regression Testing:**  
- **Regression Test Version:** V1.1  
- **Regression Test Outcome:** This update fixes the receipt to show the amount transferred correctly, but receipt is showing the incorrect card number. The amount transferred is now correct on the receipt. The card number is showing "2" when the card number should be "1"  
- **Steps to Reproduce:** 
1. Turn system on, enter amount of bills in system.  
2. Click insert card, enter card number, enter correct PIN.  
3. Click Transfer (option 3).  
4. Click account to transfer from (e.g., savings).  
5. Click account to transfer to (e.g., checking).  
6. Enter amount to transfer (e.g., $20).  
7. **ERROR:** The receipt is showing the wrong card number. A transfer inquiry for CARD 1 should be correctly indicated on the receipt.

**Log:**
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $40.00
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:40:02 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $1040.00
AVAILABLE: $1040.00
```

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  

**Found In:** 1.0 

---

## Defect ID: 7

### **Title:** Test Case #33: Wrong options under balance inquiry for card 1  
**Work Item Type:** Bug
**State:** Resolved  
**Reason:** Fixed  
**Tags:** Exploratory; Scripted; Regression;  
**Priority:** 1  
**Severity:** 1 - Critical  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Test Case:** 33  
- **Use Case:** Inquiry  
- **Function being tested:** System asks customer to choose an account to inquire about.  
- **Initial state of system:** Menu of transaction types is being displayed so that customer can select account to inquire about the balance.  

#### Expected Outcome:
System displays a menu of account types.  

#### Actual Outcome:
Savings account does not show as an option for balance inquiry when using Card 1. Checking and Money Market are shown, but Card 1 has access to Checking and Savings.  

#### Priority:
1 - Critical  
- **Reason:** "Inquiry" queries are part of ATM core functionality. System is not functionally meeting requirements. Issue will be experienced by users because balance inquiries are a common pathway of interaction.  

#### Severity:
1 - Critical  
- **Reason:** Impacts customer usability and experience. Issues displaying accounts may cause significant negative customer experience. Customers may worry an account is missing. Issue will cause additional staff hours for bank tellers and customer service.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 4 on interface number pad to access balance inquiry (option 4).  
7. **ERROR:** There is no option to select "Savings Account" for account 1. There is an option for Money Market for account 2, but it gives an error when selected.  

**Log:**
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $40.00
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:40:02 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $1040.00
AVAILABLE: $1040.00
```

### **Regression Testing:**
**Regression Test Version:** V1.1  
**Regression Test Outcome:** This update fixes the issue where "Savings" account was not showing up when making a balance inquiry.  

### System Info:
- **Version in which bug was found:** V1.0  
- **Tests were performed with debit card with card number "1".  
- **Note:** Card number "1" should not have access to a Money Market account.  

**Found In:** 1.0 

---

## Defect ID: 8

### **Title:** Test Case #34: Incorrect Receipt from Inquiry: Card Number is Wrong  
**Work Item Type:** Bug 
**State:** Active  
**Reason:** Approved  
**Tags:** Exploratory; Scripted; Regression  
**Priority:** 1  
**Severity:** 3 - Medium  

- **Version in which bug was found:** V1.0  
- **Bug was found:** The bug was found in both the exploratory testing and the scripted testing.  
- **Test Case:** 34  
- **Use Case:** Inquiry  
- **Function being tested:** System performs a legitimate inquiry transaction properly.  
- **Initial state of system:** System is displaying menu of account types.  

#### Expected Outcome:
System prints a correct receipt showing correct balance; System records transaction correctly in the log (showing both message to the bank and approval back).  

#### Actual Outcome:
The receipt is not correct. It shows Card 2 when the transaction was performed with Card 1.  

#### Priority:
1 - Critical  
- **Reason:** The system performing a legitimate inquiry transaction properly requires that the receipt is also correct. The system is not satisfying functional requirements.  

#### Severity:
3 - Medium  
- **Reason:** The system performs a transaction successfully, but the receipt is incorrect, so there is no risk to the accounting or customer accounts.  

### Steps to Reproduce:
1. Turn system on.  
2. Operator adds 10 $20 bills to ATM System.  
3. Insert debit card (card number 1).  
4. Enter card number (choose card number 1).  
5. Enter correct PIN for card number 1.  
6. Press 4 on interface number pad to access balance inquiry (option 4).  
7. Press 1 on interface number pad to select checking account (option 1).  
8. **ERROR:** The receipt provided displays Card #2 when the transaction was performed with Card #1.  

#### Receipt:
```
Thu Jan 30 10:39:28 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
INQUIRY FROM: CHKG

TOTAL BAL: $100.00
AVAILABLE: $100.00 
```

**Log:**
```
Message:   TRANSFER CARD# 1 TRANS# 1 FROM  0 TO  1 $40.00
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:40:02 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #1
TRANSFER FROM: SVGS TO: CHKG
AMOUNT: $40.00
TOTAL BAL: $1040.00
AVAILABLE: $1040.00
```

### **Regression Testing:**
**Regression Test Version:** V1.1  
**Regression Test Outcome:** The receipt is not correct. It shows Card 2 when the transaction was performed with Card 1. The balance shown was correct.  
**Steps to Reproduce:**  
1. Turn system on, enter amount of bills in system.  
2. Click insert card, enter card number, enter correct PIN.  
3. Click Transfer (option 3).  
4. Click account to transfer from (e.g., savings).  
5. Click account to transfer to (e.g., checking).  
6. Enter amount to transfer (e.g., $20).  
7. **ERROR:** The receipt is showing the wrong card number. A transfer inquiry for CARD 1 should be correctly indicated on the receipt.

**Log:**
```
Message:   INQUIRY  CARD# 1 TRANS# 1 FROM  2 NO TO NO AMOUNT
Response:  FAILURE Invalid account type
Message:   INQUIRY  CARD# 1 TRANS# 2 FROM  0 NO TO NO AMOUNT
Response:  SUCCESS
```

**Receipt:**
```
Thu Jan 30 11:43:17 MST 2025
First National Bank of Podunk
ATM #42 Gordon College
CARD 2 TRANS #2
INQUIRY FROM: CHKG

TOTAL BAL: $100.00
AVAILABLE: $100.00
```

### System Info:
- **Version in which bug was found:** V1.0  
- Tests were performed with debit card with card number "1".

**Found In:** 1.0

---
