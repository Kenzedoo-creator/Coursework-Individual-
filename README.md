# Coursework-Individual-
COMP5047 Coursework repository  
Mckenzie miller-fensome - 19316140
Subsystem - 3)	USU Operation System: a web-based application to run on desktop or tablet computer for USU officers to manage the USU federation of student unions and realise its functions. 
Week 4 Use Case Diagram Completed 
begin activity model for a specific use case
begin work on the indiviudal Architectual design 
Created framework for activity model and architectural model 
Approve Union Membership - Activity Diagram

Process Flow:
1. USU Officer: Login → Access Pending Applications
2. System: Display application queue
3. Officer: Select application for review
4. System: Show complete application details
   - Union basic data
   - Representative information
   - Supporting documents
5. Officer: Validate information completeness
   → [If incomplete] Request additional information
   → [If complete] Proceed to verification
6. Validation Service: Auto-verify university data
7. Officer: Make decision
   → [If Approve] 
      - System: Create tenant account
      - System: Activate officer accounts
      - System: Generate welcome package
      - System: Notify union representatives
   → [If Reject]
      - Officer: Provide rejection reasons
      - System: Notify union with reasons
8. System: Update membership database
9. Officer: Return to dashboard

USU Operation System - Component Diagram
=========================================

Provided Services (Interfaces):
- UnionManagementService
  ↳ approveMembership(application)
  ↳ updateUnionData(unionId, newData)
  ↳ terminateMembership(unionId)

- ValidationService
  ↳ verifyUniversityData(unionData)
  ↳ validateOfficerCredentials(officerInfo)

- NotificationService
  ↳ sendApprovalNotification(unionContacts)
  ↳ sendRejectionNotification(unionContacts, reasons)

Required Services (Dependencies):
- TenantService (from common components)
- UserManagementService (from common components)
- EmailService (from infrastructure)
- DatabaseService (from infrastructure)

Components:
- UnionManagementComponent
- ApplicationReviewComponent
- DataValidationComponent
- NotificationOrchestrator
