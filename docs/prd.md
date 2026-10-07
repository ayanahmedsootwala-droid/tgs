# Requirements Document

## 1. Application Overview

- **Application Name**: The Grooming Studio TGS - Salon Management System
- **Application Description**: A mobile-responsive salon operating and CRM web system localized for Pakistan (PKR / Rs.) for The Grooming Studio TGS. The system incorporates database anti-theft data protection for non-owner users, real-time date handling, granular role permissions, a streamlined POS billing workflow (Services catalog -> Client selection -> Active invoice checkout), itemized barber-service attribution, accounting receipt-style ledger and sync views, receipt reference lookup, client digital punch card loyalty, daily expense budget quota monitoring, automated 11:59 PM day-end closing, an attendance-adjusted auto-payroll engine (calculated over all days of the month with owner-managed late penalty waivers), and an owner-exclusive v13 source code package exporter (tgs_salon_source_code_v13.zip and tgs_salon_source_code.zip).

## 2. User & Usage Scenarios

- **Target Users**:
  - **Salon Owner**: Full administrator controlling user approvals, granular role permissions, database anti-theft protections, client WhatsApp messaging permissions, manual attendance record modifications (late minutes, status, waiver flags), payroll configuration and penalty rules, daily expense budget quotas, client stamp corrections, business analytics, consolidated financial ledgers, and v13 source code exports.
  - **Salon Manager**: Operational supervisor managing daily POS billing, client CRM profiles (with restricted communication/anti-theft limits), expense logging within quota, staff attendance validation, marketing campaign generation, and billing history lookups.
  - **Cashier / Billing Staff**: Front-desk operator executing checkouts via the restructured workflow, searching receipt references, logging expenses within quota, and printing standard slips (without client loyalty metadata).
  - **Worker / Barber / Stylist**: Service provider clocking attendance, viewing assigned service attribution, commission breakdowns, tips, and individual performance summaries.

- **Core Scenarios**:
  - **Streamlined POS Checkout Flow**: Cashiers select services from the categorized catalog first, then search or quickly add a client underneath the catalog, and finally review the active invoice entry below before completing checkout.
  - **Anti-Theft CRM & Report Security**: Non-owner roles operate under strict anti-theft restrictions where direct client WhatsApp messaging from CRM is disabled and client loyalty punch card data is omitted from non-owner WhatsApp business reports and slips.
  - **Owner Attendance & Penalty Override**: The Owner manually adjusts attendance records, edits clock-in/out times, adjusts late arrival minutes, and marks late penalties as waived/paid off.
  - **Monthly Auto-Payroll Computation**: The system calculates daily wage rates based on total days in the specific month (no standard day off) and applies owner-configured late penalty rules.
  - **Daily Expense Logging with Quota Tracking**: Operators log petty cash expenses against the real-time daily budget quota, flagging any excess amounts.
  - **Receipt Reference Quick Lookup**: Staff query receipt reference numbers (e.g., TGS-261007-7504) to review line-item breakdowns, barber assignments, and trigger reprints.

## 3. Page Structure & Functional Specifications

### Page Structure Tree

- The Grooming Studio TGS
  - Authentication & Security
    - Login Screen (Email & Password)
    - Sign Up / Registration Page
    - Pending Approval Screen
  - Global Layout & Navigation Shell
    - Dynamic Header (Real-Time Date Indicator, Online/Offline Status, User Identity, Role Badge)
    - Mobile-Optimized Navigation Dock & Tab Shell
  - POS / Billing & Lookup
    - Section 1: Pinned Fast Services & Categorized Service Catalog (Top)
    - Section 2: Client Selector & Search Bar (Middle - Placed under Services and over Invoice; includes Quick Plus '+' Add Client Modal)
    - Section 3: Active Invoice & Billing Entry (Bottom - Line-Item Barber Attribution, Price Adjustment, Payment Selector, Notes, PKR Checkout Button)
    - Receipt Reference Quick Lookup Search Bar
    - Itemized Accounting-Style Receipt Modal & Print Action
  - Daily Sync Report & Automated Day Closing
    - Accounting Receipt-Style Sales Feed (Itemized Services Paired with Assigned Barbers)
    - 11:59 PM Auto-Closing Timer & Archive (Manual closing and opening cash float removed for staff)
    - WhatsApp Business Report & Slip Generator (Client loyalty metrics excluded for non-owner roles)
  - Client Directory CRM & Punch Card Studio
    - Client Directory (Middle 5 Digits Masked for Non-Owner Roles, Direct WhatsApp Button Disabled for Non-Owner Roles)
    - Client Profile Modal (Lifetime Spend, AOV, Punch Card Status - Owner Only for Sensitive Contact Actions)
    - Detailed Service Visit History (Date, Service Item, Assigned Barber)
    - Digital Stamp Card Management Hub (Stamp Logs, Owner Stamp Edit/Remove Tools)
    - Client Add / Edit Modal
  - Marketing & Campaigns Hub (Owner & Manager)
    - Client Segmentation Filters
    - WhatsApp Campaign Template Selector
    - Broadcast Activity Log
  - Real-Time Sales & Expense Tracker
    - Dynamic Date Selector & Real-Time Sales Stream
    - Daily Expense Quota Tracker (Daily Limit, Remaining Balance, Exceeded Expense Flag)
    - Petty Cash Expense Logger
  - Staff Attendance
    - Staff Clock-In / Clock-Out Interface
    - Daily Attendance Sheet & Monthly Logs
    - Owner Manual Attendance Editor (Edit Status, Clock In/Out Timestamps, Late Arrival Minutes, Paid Off / Waived Toggle)
  - Staff Commission & Salary Calculator (Owner & Manager)
    - Monthly Auto-Payroll Engine (Base Salary / Days of Specific Month, Late Penalty Deductions, Attendance Adjustments)
    - Owner Late Penalty Configuration Tool (Thresholds, Penalty Rates, Waive / Paid Off Controls)
    - Commission Rate Override Tool (Owner Only)
    - Printable & WhatsApp-Shareable Staff Pay Slip Generator
  - Business Analytics & Business Intelligence (Owner Only)
    - Revenue Trend Lines & AOV Tracker
    - Peak Hours Heatmap Matrix
    - Barber Contribution & Service Margins
  - Owner Financial Ledger & CapEx Hub (Owner Only)
    - Cash vs Online Reconciliation Summary
    - Consolidated Revenue, Operational Expenses, Staff Payouts, Net Profit
    - Capital Expenditure (CapEx) Logger & Persistent Overheads
  - Source Code Export (Owner Only)
    - Version 13 Package Downloader (tgs_salon_source_code_v13.zip and tgs_salon_source_code.zip)
  - Owner Settings & Permissions (Owner Only)
    - Granular Role Permission Toggles
    - Anti-Theft Protection Settings
    - Staff Attendance & Feature Access Toggles

### Functional Specifications

#### 3.1 Restructured POS Billing Flow
- **Sequential Layout Order**:
  1. **Top Section**: Service Catalog & Quick Add buttons for services.
  2. **Middle Section**: Client Selection bar (search by client name or phone number) with an integrated Quick Plus '+' button to register a new client without leaving the flow.
  3. **Bottom Section**: Active Invoice area displaying selected service items, line-item barber dropdown assignments, pricing adjustments, payment method options (Cash, Online Transfer, Wallet, Split), and Final Checkout.
- **Receipt Reference Lookup**: Search input retrieves transaction breakdowns (e.g., TGS-261007-7504) with reprint functionality.

#### 3.2 Anti-Theft Database & Communication Protection
- **Client WhatsApp Action Lockdown**: The direct WhatsApp message button in the Client Directory is active exclusively for the Owner role. For all non-owner roles (Manager, Cashier, Staff), the button is disabled and hidden.
- **Loyalty Omission on Non-Owner Reports & Slips**: Loyalty punch card stamp totals and loyalty tier metadata are removed from WhatsApp Business Reports and printed customer slips generated by non-owner roles.
- **Phone Number Masking**: Middle 5 digits remain masked (03001****67) for non-owner accounts across CRM lists and segment views.

#### 3.3 Owner-Exclusive Manual Attendance Management
- **Attendance Record Modification**: The Owner can manually edit any staff member's attendance record for any given date.
- **Editable Attributes**: Status (Present, Late, Absent, Half Day), Clock-In time, Clock-Out time, Late Arrival minutes.
- **Penalty Waiver Action**: Owner can toggle a Late Penalty Waiver flag to mark specific late arrivals as 'Paid Off / Waived', excluding them from payroll deductions.

#### 3.4 Auto-Payroll Engine & Late Penalty Rules
- **Full Month Calendar Calculation**: Base salary daily rate is computed as `Daily Rate = Monthly Base Salary / Total Calendar Days in Current Month` (e.g., divided by 30, 31, 28, or 29 depending on the specific month).
- **Working Days Model**: Operates on a continuous calendar basis (all days counted, no standard day off assumptions unless marked absent/leave).
- **Late Penalty System**: Owner configures late minute grace thresholds and deduction formulas. Late deductions are automatically factored into payroll unless flagged as Waived/Paid Off by the Owner.

#### 3.5 Version 13 Source Code Export
- **Owner v13 Bundle**: Provides instant download links for `tgs_salon_source_code_v13.zip` and `tgs_salon_source_code.zip` under the Source Code Export section.

## 4. Business Rules & Core Logic

1. **POS Sequential Ordering Rule**: POS checkout UI must render in the exact vertical sequence: Services Catalog -> Client Search/Add -> Active Invoice.
2. **Anti-Theft Enforcement Rule**: All non-owner roles are prohibited from sending direct WhatsApp messages from the CRM and cannot view client loyalty data in generated WhatsApp business reports or slips.
3. **Full Month Payroll Formula**:
   - `Daily Salary Rate = Base Salary / Days in Selected Month`
   - `Monthly Salary Payout = (Days Present * Daily Salary Rate) + Total Commissions + Tips - Active Late Penalties`
4. **Late Penalty Calculation**:
   - If `Late Minutes > Grace Threshold` and `Waiver Status = False`, apply configured late penalty deduction.
   - If `Waiver Status = True (Paid Off / Waived by Owner)`, penalty deduction is 0.
5. **Single Daily Stamp Limit**: Maximum 1 loyalty stamp awarded per client per calendar day, regardless of visit count.
6. **Expense Quota Calculation**:
   - `Remaining Quota = Daily Expense Limit - Total Standard Expenses Logged Today`
   - Excess amounts are recorded and flagged as `Exceeded Expense`.
7. **Automated Register Closing**: Ledger snapshot automatically locks at 11:59 PM daily without manual intervention.
8. **Receipt Reference Format**: Formatted as `TGS-YYMMDD-XXXX` upon checkout completion.

## 5. Exceptions & Edge Cases

| Scenario | Trigger / Condition | System Behavior |
|---|---|---|
| Non-Owner Attempts Client WhatsApp Messaging | Non-owner user attempts to initiate WhatsApp chat from Client Directory | Feature is disabled/hidden; action is blocked |
| Non-Owner Generates Business Report / Slip | Non-owner triggers WhatsApp business report or receipt slip | System strips loyalty stamp counts and loyalty balances from the output |
| Owner Waives Late Penalty | Owner marks a staff member's late attendance record as Waived/Paid Off | System recalculates payroll deductions immediately, setting the late penalty for that shift to zero |
| Variable Days in Month | Payroll calculated for February (28/29 days) vs March (31 days) vs April (30 days) | System automatically divides base salary by the exact number of days in that specific month |
| Checkout Without Client Selection | Operator adds services and attempts checkout without selecting or adding a client | Require client selection or quick walk-in selection before finalizing the active invoice |
| Expense Exceeds Daily Limit | Operator logs an expense exceeding remaining budget | Save expense with an Exceeded Expense tag and update ledger totals |
| Receipt Reference Query Missing | Non-existent reference code entered in search bar | Display clear reference not found notification |

## 6. Acceptance Criteria

1. On the POS checkout page, the Services catalog is rendered at the top, the Client search/add bar is rendered in the middle under services, and the Active Invoice is rendered below client selection.
2. Non-owner roles cannot send WhatsApp messages to clients from the Client Directory CRM.
3. WhatsApp Business Reports and customer slips generated by non-owner accounts do not include client loyalty or punch card data.
4. Salon Owner can manually edit staff attendance status, clock-in/out timestamps, late minutes, and toggle late penalty waivers (Paid Off / Waived).
5. Payroll engine divides monthly base salary by the exact number of days in the specific month and applies active late penalty rules to net pay.
6. Digital stamp loyalty awards a maximum of 1 stamp per client per calendar day with full timestamped logs.
7. Daily Expense Quota displays real-time remaining budget and flags expenses that exceed the daily limit.
8. Searching a valid receipt reference code (e.g., TGS-261007-7504) retrieves full itemized details with reprint support.
9. Owner Settings provides granular role permission toggles and unmasked client contact visibility for the Owner only.
10. The Owner Source Code Export tab provides verified download buttons for `tgs_salon_source_code_v13.zip` and `tgs_salon_source_code.zip`.

## 7. Out of Scope (Current MVP)

1. Public customer self-booking online web portal.
2. Direct bank automated clearing house (ACH) payment gateway integrations.
3. Biometric physical fingerprint hardware integrations.
4. Multi-branch inventory freight supply chain management.