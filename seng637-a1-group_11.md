>   **SENG 637 - Software Testing, Reliability, and Quality**

**Lab. Report \#1 – Introduction to Testing and Defect Tracking**

| Group: 11    |
|-----------------|
| Steven Au             |   
| Laurel Flanagan       |   
| Rhys Wickens          |   
| Austen Zhang          |   


**Table of Contents**
- [Introduction](#introduction)
- [High-level description of the exploratory testing plan](#high-level-description-of-the-exploratory-testing-plan)
- [Overall test plan](#overall-test-plan)
  - [Test types](#test-types)
  - [Scope of Testing](#scope-of-testing)
  - [Test Logistics](#test-logistics)
  - [Test Environment](#test-environment)
  - [Test Tasks and Schedule](#test-tasks-and-schedule)
  - [Test Deliverables](#test-deliverables)
- [Results and Discussion](#results-and-discussion)
- [Comparison of exploratory and manual functional testing](#comparison-of-exploratory-and-manual-functional-testing)
  - [Exploratory Testing](#exploratory-testing)
  - [Manual Scripted Testing](#manual-scripted-testing)
  - [Conclusion](#conclusion)
- [Notes and discussion of the peer reviews of defect reports](#notes-and-discussion-of-the-peer-reviews-of-defect-reports)
- [Additional Issues Found](#additional-issues-found)
- [How the pair testing was managed and team work/effort was divided](#how-the-pair-testing-was-managed-and-team-workeffort-was-divided)
- [Difficulties encountered, challenges overcome, and lessons learned](#difficulties-encountered-challenges-overcome-and-lessons-learned)
- [Comments/feedback on the lab and lab document itself](#commentsfeedback-on-the-lab-and-lab-document-itself)


# Introduction
The system we are testing is an ATM simulation system. The purpose of the system is to allow users to deposit, withdraw, query and transfer funds to/from their hypothetical bank accounts. This report outlines the full process of how we planned the tests on the system, the results of these tests, a comparison of the results across the testing methodologies, and a discussion of how we worked as a team and any challenges we overcame.  

We will first outline our test plan, including our exploratory, manual scripted, and regression test plans. We then performed the exploratory and manual scripted tests on V1.0 of the ATM system and recorded the bugs in Azure Devops. Next, we performed regression testing on the updated V1.1 of the ATM system to determine which of the bugs we identified in V1.0 were fixed. We noted these changes within Azure Devops as well. Next, we discussed the benefits and drawbacks of each testing methodology and how we worked as a team to complete each test thoroughly. Lastly, we explored the different challenges we dealt with and overcame during the testing process.

Our team had recently been introduced to exploratory and manual functional testing prior to this project, so had minimal experience in performing in depth testing on a new system. We learned about the different approaches to testing and how each form of testing can help pinpoint and eliminate bugs of a software system in different ways. We were all using Azure Devops, the defect tracking system, for the first time. We had also never performed pair testing prior to this project. This project gave us practical experience in testing a software system, that we can build on throughout our career as software developers.  

# High-level description of the exploratory testing plan
**Scope of Testing**
The exploratory test plan will involve:
- The exploratory testing phase will familiarize testers with the application. 
- Testers will start with exploring core system functionality, such as verifying that the system allows the Operator to start the system, and successfully access a valid account.
- Testers may explore unexpected behaviour, edge cases, and defects which are not covered by predefined manual functional tests.
- There will be a focus on high-risk areas, specifically debit card authentication, and transactions.
- Testing will be completed on the ATM System – Lab 1 Version 1.0 during this phase. 

**Priority 1: Core Functionalities** 

These are the fundamental features that ensure the ATM is serving its main purpose:
- Card Insertion and PIN Validation: This is the very first point of interaction, so test card insertion (valid/invalid) and PIN validation right away. If there are any issues here, they affect all subsequent tests.
- Withdrawal: Perform at least one transaction to check whether the machine correctly dispenses cash, handles network issues, and prints a receipt.
- Deposit: Test the deposit functionality. Focus on ensuring the amount is correctly entered and the system can handle a basic deposit scenario.
- Balance Inquiry: A quick balance check will provide insight into how the system responds and if the right data is displayed.
- Transfer Between Accounts: Perform at least one transaction to check whether a customer can transfer money between two accounts linked to the card. 

These core functionalities are where we are most likely to find issues that can break the system in real-world usage. Complete one to two transactions in each of these areas (withdrawal, deposit, balance inquiry, transfer between accounts).

**Priority 2: Edge Cases and Exceptional Paths** 
Use the remaining time to test scenarios that are more likely to break the system or expose subtle issues:
- PIN Failures: Test what happens if the PIN is incorrect once or twice (check if the system allows retry). Make sure the card is retained after 3 failed attempts.
- Cancel Transaction Midway: Start a withdrawal and press "Cancel" halfway through to see how the system handles aborting a transaction. 
- Deposit Timeout: Simulate not depositing the envelope after a deposit has been initiated, and check if the ATM behaves as expected (e.g., does it notify the user of a failed deposit after timeout?).


**Priority 3: Security and Error Handling Checks** 
- Error Messages: Trigger errors (e.g. insufficient funds, request withdrawal that is not a multiple of $20) and see if the error messages are informative and user-friendly.
- Security Checks: Verify that the ATM retains the card after multiple failed PIN attempts.

**Test Logistics**
- Perform testing in a pair "Pair Testing." The tests will be done in pairs, with one tester interfacing with the ATM system, the other recording and documenting. Both pairs of testers will spend approximately 30 minutes carrying out the exploratory testing. 
- Testers have the responsibility to report findings with clear steps to reproduce identified bugs. Additional information such as logs should be included in the documented findings.
- Testers should also record any observations, risks, or areas that might need more focus in later testing phases.
- After the two pairs complete exploratory testing, the defect reports from each pair will be reviewed and compared. 

# Overall test plan 
The purpose of the test plan is to provide an overview of the testing approach for the ATM simulation system, including the test types, scope of testing, and test logistics. 

## Test types 
The test approach consists of the following three test types:
- Exploratory Testing (Manual Non-scripted)
- Manual Scripted Testing 
- Regression Testing (Verification of Defect Fixes) 

## Scope of Testing 
The scope of testing is focused on the features and software system requirements as provided in Appendix B: High Level Requirements. It consists of testing the functionalities as defined in the requirements to check if the system matches the requirements. All types of testing included in the plan are black box testing, with use of the system interface and no access to the code. Items not listed in the requirements are not included in the test scope. The scope does not include any testing of hardware interfaces or communications interfaces. 

The Exploratory and Manual Scripted Testing phases will be performed on ATM System – Lab 1 Version 1.0. The Regression Testing phase will be performed on ATM System – Lab 1 Version 1.1. 

Scope of the Exploratory Testing phase is described in the section High-level description of the exploratory testing plan.
The scope specific to the Manual Scripted Testing phase includes completion of the basic test suite provided in Appendix C: SUT Use Cases. Any new defects that were not found during the exploratory phase will be recorded. Additionally, it will be noted if defects are found during both testing phases. 

The purpose of the Regression Testing of Version 1.1 is to review defects found in Version 1.0 to confirm if they have been addressed and ensure that the update does not introduce new errors that were not present in Version 1.0. The Regression Testing includes the retesting of all test cases for each of the defects noted based on the Exploratory Testing and Manual Scripted Testing phases. The status of the defects will be updated if they were resolved in Version 1.1, or they will be noted as still in progress. 

## Test Logistics 
Testing can begin as soon as all team members have reviewed the system requirements, familiarized themselves with the ATM system, downloaded the JAR files required to run the system, and the test plan has been developed. 

The Exploratory Testing phase will be carried out by each of the 2 pairs in Group 11 as described in the previous section. Laurel Flanagan and Rhys Wickens will carry out Exploratory Testing in a pair, and Steven Au and Austen Zhang will also complete the same procedure in a pair.

The Manual Scripted Testing will be completed as a group. One student “drives” the testing/operates the ATM system under test, one student determines the order of the test cases, one student verifies if the test passed or failed, one student reports defects for failed cases.  

The Regression Testing will also be completed as a group. One student “drives” the testing/operates the ATM system under test, one student specifies test cases that need to be checked again based on defect report, one student verifies if the test passed or failed, one student reports defects for failed cases.  

## Test Environment 
The test environment consists of the GUI for the ATM simulation system that can be accessed from the provided JAR files. 

## Test Tasks and Schedule 
Tasks required to complete the test plan and the estimated schedule for completion of these tasks is provided in the table below.

Table 1. Testing Task Schedule
| Task                                           | Completion Date   |
|------------------------------------------------|-------------------|
| Review System Requirements                    | January 24, 2025  |
| Familiarization with ATM System               | January 27, 2025  |
| Develop Test Plan                              | January 28, 2025  |
| Exploratory Testing Phase in Pairs            | January 29, 2025  |
| Compare Exploratory Testing Results           | January 30, 2025  |
| Manual Scripted Testing Phase in Group        | January 30, 2025  |
| Regression Testing Phase in Group             | January 30, 2025  |
| Reporting                                      | February 3, 2025  |

## Test Deliverables 
The before testing phase deliverables include: 
- Test plan
- Test cases for Manual Scripted Testing 

The during testing phase deliverables include: 
- Test data
- Error logs and messages from the system 

The after testing phase deliverables include: 
- Defect Report: Exploratory and Manual Scripted Testing
- Defect Report: Regression Testing
- Lab Report 


# Results and Discussion 
Defects that were found during exploratory and scripted testing phases can be found in the markdown file named “seng631-a1-scripted_testing_defect_report.md”. This report was exported from Azure as a csv file and parsed into markdown format. The following image shows the “Work Items” page in Azure, where defects were input by the test team.

** EMBED IMAGE FROM AZURE HERE**

Regression testing was performed on ATM System V1.1, following the outline “Steps to Reproduce” for defects identified in exploratory and manual scripted testing phases. Defects are not assigned a “Resolved” status unless the “Actual Outcome” requirement specified by the scripted testing is completely fulfilled. If a defect was found in exploratory testing and was not a Test Case in the manual scripted testing phase, then the status is set to “Resolved” if the defect is no longer occurring.

# Comparison of exploratory and manual functional testing
Both the exploratory testing and the manual scripted testing had its own benefits and drawbacks in terms of effectiveness and efficiency. While exploratory testing excels at uncovering unexpected defects through flexible, adaptive approaches, manual scripted testing provides structured, repeatable processes that ensure consistent coverage of predefined requirements. Together, they offer complementary strengths in identifying system bugs.

## Exploratory Testing 
In our exploratory testing, we approached the ATM system as new users, which initially resulted in a slower start as we needed time to understand how the system operated. However, once familiar with the relatively simple system, we found that exploratory testing allowed us to test most of the main functionalities. In a more complex system, we found that exploratory testing could rely heavily on the tester’s experience and domain knowledge, which can lead to variability in effectiveness. 

The approach granted us the freedom to be creative and rely on our intuition, enabling us to identify unexpected bugs that the scripted tests might have missed. The flexibility to adapt our testing based on system behaviour was important in uncovering edge cases and usability issues. However, the need to take detailed notes while identifying bugs was time-consuming, as we had to document defects promptly to ensure accuracy and traceability. This requirement added a layer of complexity to the process, making it somewhat less efficient compared to scripted testing in terms of immediate bug reporting.

## Manual Scripted Testing 
In contrast, manual scripted testing provided a more structured and systematic approach. By following predefined test cases with clear expected outcomes, we were able to maintain consistency and ensure comprehensive coverage of specific system requirements. This method proved to be highly efficient for quickly identifying bugs, as we could directly compare actual results with expected outcomes without the need for extensive notetaking.

While manual scripted testing was faster in terms of bug identification, it was somewhat limited in its ability to uncover unexpected issues. The rigid structure restricted our ability to deviate from the test scripts, potentially missing defects outside the predefined scenarios. However, the repeatability of these tests ensured reliability and made it easier to track regression issues over time.

## Conclusion 
Overall, both testing methods provided valuable insights into the ATM system's functionality. Exploratory testing allowed us to discover unforeseen defects through creative, adaptive exploration, while manual scripted testing offered efficiency and consistency in verifying known requirements. Combining both approaches enabled us to maximize defect detection and improve the system's overall quality.

See below the defect report of the bugs we found during the exploratory and manual scripted testing. We were able to find all the bugs in the exploratory testing that we found in the manual scripted testing. We also found a couple extra bugs in the exploratory testing that we did not find in the manual scripted testing, due to the flexibility and creativity allowed during the exploratory testing.

![Azure Bug Reporting Sample]([https://github.com/ensf-614-group11/seng637-a1-group11/blob/main/1_test_case_14_defect_report.png])


# Notes and discussion of the peer reviews of defect reports
While the two pairs each completed exploratory testing separately, after some discussion we discovered that many of the bugs we found were the same. These were:
-	Withdrawn amount incorrect
-	Deposited amount incorrect
-	Transfer amount between accounts is incorrect
-	Receipt shows opposite “to” and “from” fields during a transfer
-	Receipt showing Card 2 when Card 1 was used on transactions
-	Wrong options under balance inquiry for card 1 (Savings account does not show as an option for balance inquiry when using Card 1, even though it does have a savings account)

However, some of the bugs were different. For example, one group found that if you tried to access money market account with card 1 (which does not have a Money Market account), the system would give an “Unknown Error”, rather than displaying a message showing the user that card 1 does not have a Money Market account. On top of this $500 is ejected from the machine when this bug happens. The other group found a different error, where if card 3 was inserted into the machine, the machine would freeze after entering a PIN.

# Additional Issues Found 
Below is a table of additional issues that were noted during the Exploratory Testing phase. These are not considered bugs or defects, but if they were addressed, the ease of use of the system may be improved.

Table 2: ATM System Addtional Issues 
| #  | Issue Description                                                           | Steps to Reproduce                                                                                     | Severity | Version |
|----|-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|----------|---------|
| 1  | Unclear what button to press to eject debit card                            | 1. Startup ATM System<br>2. Insert debit card<br>3. Enter PIN<br>4. Unclear what button ejects card on interface. | Low      | V1.0    |
| 2  | UI is not intuitive. Account balance could be shown on UI before performing transactions. | 1. Startup ATM System<br>2. Insert debit card, enter PIN<br>3. Press 1 for ‘Withdrawal’<br>4. Press 1 for ‘Checking’<br>5. Account balance not shown after pressing ‘Checking’ | Low      | V1.0    |
| 3  | Logging is unclear, logging does not have timestamps                        | 1. Startup ATM System<br>2. Insert debit card, enter PIN<br>3. Press 1 for ‘Withdrawal’<br>4. Press 1 for ‘Checking’<br>5. Press 1 for $20 withdrawal<br>6. Log of transaction does not show timestamp | Low      | V1.0    |
| 4  | No option to provide operator with ATM state, like bills in ATM            | 1. Startup ATM System<br>2. No way to check how many bills are in ATM.                                | Low      | V1.0    |

# How the pair testing was managed and team work/effort was divided 
Exploratory testing was done in two pairs and separately. The findings for each pair were compiled on Azure DevOps as bugs. 

We then got together into a group of four to perform the manual scripted testing and regression testing, and subsequently updated the Azure DevOps to add new bugs and update old ones.

We then divided the defect report and lab report among the four team members.


# Difficulties encountered, challenges overcome, and lessons learned
Throughout the project, we encountered several challenges that required thoughtful solutions:
1.	Bug Tracking During Exploratory Testing: When we first began exploratory testing, we lacked a structured procedure for tracking the bugs we discovered. This made it difficult to accurately document the exact conditions under which bugs appeared, forcing us to retrace our steps to recreate them. We addressed this by systematically tracking the system’s state during testing, allowing us to quickly reproduce issues and document them with precise details.
2.	Consolidating Defect Reports from Multiple Teams: Another challenge arose when merging the lists of bugs identified by the two teams conducting exploratory testing. While both teams uncovered many of the same major defects, there were discrepancies regarding minor issues and whether they warranted inclusion in the defect report. To resolve this, we revisited the system’s outlined requirements, using them as a benchmark to determine which issues were relevant and needed to be documented. This ensured consistency and alignment with project goals.
3.	Navigating Azure DevOps for Bug Tracking: One of the challenges we encountered was learning how to effectively use Azure DevOps for bug tracking. Since it was our first time working with the platform, we had to research and explore its features to understand where and how to store detailed bug information. Additionally, we faced difficulties exporting the bug reports in a clear, readable format for inclusion in our project report. Through trial, error, and collaborative problem-solving, we became more proficient with the tool and streamlined our reporting process.
4.	Establishing an Efficient Manual Scripted Testing Procedure: During manual scripted testing, we initially struggled to establish an efficient workflow among the four team members. Without clearly defined roles, each person attempted to guide the testing process, leading to confusion and inefficiencies. We quickly resolved this issue by assigning specific roles to each team member, which improved coordination and allowed the testing to proceed smoothly and effectively.

# Comments/feedback on the lab and lab document itself
Overall, this project provided a valuable introduction to different software testing methodologies. We gained practical experience in approaching software testing, collaborating effectively as a team, and identifying and documenting software bugs. Additionally, working with bug tracking tools like Azure DevOps was beneficial, as it’s a platform we may encounter in our future careers.

One area for improvement in the lab would be enhancing the clarity of the lab documentation. At times, we found it challenging to understand the specific requirements and expectations for the lab. A more concise, well-structured document outlining the necessary steps and submission guidelines would help streamline the process and reduce confusion.

