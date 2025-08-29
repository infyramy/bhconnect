# Complete Final Sitemaps & Flows - BrightHill Connect

**Version:** 2.0  
**Last Updated:** 2025-08-22  
**Status:** Final Standardized Version  
**Context:** 700 students, RM560 monthly fees, RM1280 registration, Malaysian preschool network

---

## 🖥️ Web Application Complete Sitemap

### 📈 Central Admin Complete Sitemap
```
🏠 Dashboard
├── Branch Selection (REQUIRED: Select branch before accessing any data)
├── Analytics Overview (Selected branch metrics and KPIs)
└── Performance Widgets (Real-time data for selected branch)

🏢 Branch Management
├── Branch List (Search, filter, and manage all branches)
├── Add New Branch (Create branch with principal assignment)
├── Edit Branch Details (Update branch information and capacity)
├── Branch Performance (Attendance trends and financial overview)
└── Branch Comparison (Multi-branch performance analysis)

👥 User Management
├── Principal Management
│   ├── Principal List (All branch principals with activity status)
│   ├── Add New Principal (Create account with branch assignment)
│   ├── Edit Principal (Update details and change assignments)
│   └── Activity Logs (Track principal system usage)
├── Financial Staff Management
│   ├── Financial Staff List (All financial staff with branch assignments)
│   ├── Add New Financial Staff (Create account with billing permissions)
│   ├── Edit Financial Staff (Update details and branch assignment)
│   └── Financial Activity Logs (Track billing and payment activities)
└── Teacher Management
    ├── Teacher List (All teachers across network with search)
    ├── Add New Teacher (Create account and assign to branch)
    ├── Edit Teacher (Update information and class assignments)
    └── Performance Metrics (Attendance accuracy and communication)

📢 Communications
├── Network Announcements (Create and manage system-wide messages)
└── Message Center (Direct communication with principals)

📊 Student Performance (Branch Selection Required)
├── Academic Reports (Performance data for selected branch)
├── Assessment Analytics (Trends and patterns by class)
├── Progress Tracking (Individual student development)
└── Comparative Analysis (Performance across time periods)

📋 Reports & Analytics
├── Attendance Reports (Daily, weekly, monthly for selected branch)
├── Financial Reports (RM560 collections and RM1280 registrations)
├── User Activity Reports (Teacher and parent engagement)
└── Performance Dashboard (Network-wide KPIs and trends)

⚙️ System Settings
└── Security Settings (Password policies and session management)
```

### 💰 Financial Staff Complete Sitemap
```
🏠 Dashboard
├── Financial Overview (Outstanding bills, payment collection rates)
├── Recent Transactions (Daily payment activities and approvals)
└── Payment Alerts (Overdue accounts and payment reminders)

👨‍🎓 Student Billing Management (Manual Only)
├── Create Student Bills
│   ├── Select Students (Individual selection for manual billing)
│   ├── Add Line Items (Tuition, meals, activities, late fees)
│   ├── Set Amounts (Fixed: RM560 monthly, RM1280 registration)
│   ├── Generate Invoice (Manual invoice creation)
│   └── Send Notification (Notify parents via mobile app)
├── Payment Processing
│   ├── Billplz Integration (Monitor Billplz payment processing)
│   ├── Manual Payment Verification (Approve uploaded receipts)
│   ├── Payment Status Updates (Mark payments as received)
│   └── Payment Confirmations (Send approval notifications)

📊 Financial Reports & Analytics
├── Revenue Tracking (Daily, weekly, monthly income reports)
├── Collection Efficiency (Payment success rates and trends)
├── Outstanding Balances (Overdue accounts requiring follow-up)
└── Payment Method Analysis (Gateway vs manual payment breakdown)

💳 Billplz Payment Management
├── Transaction Monitoring (Real-time Billplz payment status)
├── Failed Payment Recovery (Handle declined Billplz transactions)
├── Payment History (View all Billplz transactions)
└── Billplz Integration Settings (Configure Billplz connection)
```

### 👩‍🏫 Teachers Role (Web Admin) Complete Sitemap
```
🏠 Dashboard
├── Assigned Classes Overview (Current class assignments and student counts)
├── Photo Attendance Summary (Daily attendance with photo requirements)
└── Today's Summary (Key metrics and alerts for assigned classes)

👨‍🎓 Student Management (Limited to Assigned Classes)
├── Student List (Search & filter students from assigned classes only)
├── View Student Profile (Academic information for assigned students)
├── Student Attendance History (View attendance patterns)
└── Student Academic Progress (View and update progress reports)

📸 Attendance Management (Same as Principal)
├── Mark Daily Attendance (Present/absent with photo capture)
├── View Attendance Reports (Daily, weekly attendance for assigned classes)
├── Photo Upload Management (Handle attendance photo uploads)
└── Edit Attendance (Past records with approval required)

📚 Academic Assessment (Same as Principal)
├── Grade Entry (Mid-term and final examinations for assigned students)
├── Progress Reports (Enter academic assessments and notes)
├── Assessment History (View previous assessments and trends)
└── Academic Analytics (Class performance metrics)

💬 Messages (Same as Principal)
├── Parent Messages (Direct communication with parents of assigned students)
├── Principal Messages (Communication with branch principal)
├── Message History (All sent and received messages)
└── Send Announcements (To parents of assigned students only)
```

### 🏫 Branch Principal Complete Sitemap
```
🏠 Dashboard
├── Branch Overview (Student count, attendance, fee collection status)
├── Teacher Activity (Daily posts, attendance completion rates)
└── Today's Summary (Key metrics and alerts for current day)

👨‍🎓 Student Management
├── Student List
│   ├── Search & Filter (By class, status, payment status)
│   ├── Add Student & Link Parent (Create record with parent connection)
│   └── Edit Student Profile (Update information and class assignment)
├── Class Management
│   ├── Class List (Current classes with enrollment and teachers)
│   ├── Create New Class (Set capacity limit of 12 students maximum)
│   ├── Assign Students to Classes (Move between classes)
│   └── Assign Teachers to Classes (Set primary teacher per class)
└── Student Analytics
    ├── Attendance Patterns (Individual and class attendance trends)
    └── Performance Metrics (Assessment results and progress)

👨‍🏫 Teacher Management
├── Teacher List (All teachers assigned to this branch)
├── Add New Teacher (Create account and set class assignments)
├── Edit Teacher Profile (Update contact and qualification details)
├── Class Assignments (Manage teacher-class relationships)
└── Teacher Performance (Activity metrics and parent feedback)

💰 Payment Management (Manual Invoice Creation)
├── Create Student Bills
│   ├── Select Students (Individual or multiple selection)
│   ├── Add Billing Items (Tuition RM560, Registration RM1280, etc.)
│   ├── Enter Custom Amounts (Flexible pricing per item)
│   ├── Generate Invoice (Manual invoice creation only)
│   └── Send Notification (Notify parents via mobile app)
├── Payment Tracking
│   ├── Payment Overview (All payment statuses by student)
│   ├── Review Payment Receipts (Verify uploaded payment proofs)
│   ├── Approve Payment Proofs (Update status with approval notes)
│   ├── Overdue Accounts (Late payments tracking)
│   └── Payment History (Complete payment records per student)
└── Financial Reports
    ├── Revenue Analysis (Monthly income and seasonal patterns)
    └── Collection Trends (Payment success rates)

📢 Communications
├── Branch Announcements
│   ├── Announcement List (Branch and network announcements)
│   ├── Create Announcement (Target specific classes or all parents)
│   └── Engagement Statistics (View rates and parent responses)
└── Parent Messages Center
    ├── All Parent Messages (New, In Progress, Closed status)
    ├── Message Details (View message content and reply history)
    ├── Reply to Parent (Max 3 replies per message thread)
    ├── Message History (Archive of completed messages)
    └── Send Message to Staff (Direct communication with teachers/admin)

📅 Calendar & Events
├── View Toggle (Calendar Mode OR List Mode)
├── Event Management
│   ├── Create Event
│   │   ├── Event Title (Short descriptive name)
│   │   ├── Event Type (Academic/Religious/Operational/Activity/Community)
│   │   ├── Description (Details, agenda, special notes)
│   │   ├── Date & Time (Start, end, all-day toggle)
│   │   ├── Location (School hall, field, external venue)
│   │   └── Notification Settings (Push now/1 day reminder/don't send)
│   ├── Edit Event (Update all event details and settings)
│   └── Delete Event (Remove event with confirmation)
└── Event Details View (Full information display when selected)

📊 Reports & Analytics
├── Branch Performance (Overall metrics and KPIs for branch)
├── Attendance Reports (Daily, weekly, monthly patterns)
└── Financial Summary (RM560 collection rates and balances)
```

---

## 📱 Mobile Application Complete Sitemap

### 👩‍🏫 Teacher App Complete Sitemap
```
🏠 Home
├── Current Class Overview (Today's assigned classes)
├── Quick Actions Dashboard (Attendance shortcuts, announcements)
├── Recent Activity Summary (Latest updates and notifications)
└── Daily Schedule (Current and upcoming classes)

🏫 Classroom
├── Classroom Selection (List of admin-assigned classrooms only)
├── Selected Classroom Dashboard
│   ├── Summary
│   │   ├── Student Overview (Total students, attendance rates)
│   │   ├── Performance Metrics (Assessment progress)
│   │   └── Recent Activity (Latest posts and updates)
│   ├── Feed
│   │   ├── Create Text Update (Write classroom activity description)
│   │   ├── Tag Students (Select which students to include in post)
│   │   ├── Posted Updates History (View previous posts)
│   │   ├── Edit Updates (Modify existing posts and student tags)
│   │   └── View Upvotes (See parent engagement with posts)
│   └── Quick Actions
│       ├── Attendance (Current day attendance marking)
│       └── Grade Mark (Assessment entry for exams)

📸 Photo Attendance (From Classroom Quick Action)
├── Current Day Attendance (Today's date, selected classroom)
├── Camera Interface Activation (Automatic photo capture mode)
├── Individual Student Photo Capture
│   ├── Take Photo (One photo per student required)
│   ├── Clear Face Visibility (Quality check for identification)
│   ├── Failed Photo Retry (Re-take if upload fails)
│   └── Photo Upload Confirmation (Verify successful submission)
├── Mark Attendance with Photos (Present/Absent with photo verification)
├── Add Remarks (Optional notes for absent students)
├── Submit Attendance with Photos (All photos uploaded to backend)
├── Upload Status Verification (Confirm all photos submitted successfully)
├── Past Attendance Records (View/edit historical data)
└── Edit Approval Required (Past edits need admin approval)

📊 Grade Mark (From Classroom Quick Action)
├── Exam Selection (Choose exam type: Midterm, Final, etc.)
├── Student Selection (Choose student from classroom)
├── Subject Areas (Reading, Numbers, Social, Physical, Creative)
├── Grade Entry (Excellent/Good/Satisfactory/Needs Support)
├── Teacher Comments (Optional notes for each subject)
├── Save Grades (Confirm and submit assessment)
└── Grade History (View previous assessments for comparison)

💬 Messages
├── Message Center
│   ├── Parent Messages (Reply to parent inquiries only)
│   ├── Principal Messages (Two-way communication with principal)
│   └── Announcements (View branch and school announcements)
├── Send Message (To principal or reply to parent)
├── Message Search (Find by sender, date, or subject)
└── Message History (All sent and received messages)

👤 Profile
├── View Profile (Teacher name, contact info, assigned classes)
├── Edit Profile (Update contact information)
├── Settings
│   ├── Notification Preferences (Push notification settings)
│   └── App Information (Version, help, terms of service)
└── Logout (Sign out of teacher account)
```

### 👨‍👩‍👧‍👦 Parent App Complete Sitemap
```
🏠 Dashboard
├── Child Overview Cards (Swipeable cards - one per child)
│   ├── Child Basic Information (Name, class, teacher)
│   ├── Today's Attendance Status (Present/Absent with time)
│   └── Latest Classroom Update (Most recent tagged post summary)
├── Principal Announcements (School-wide and branch announcements)
└── Payment Reminders (Outstanding fees and due dates)

👶 My Child
├── Child Basic Information (Name, class, teacher details)
├── Attendance History (Simple list view of daily attendance)
├── Classroom Updates (Select classroom to view full activity feed)
├── Progress Reports (Mid-year and final assessment results)
├── Grade History (Previous assessment results and trends)
└── Upvote Posts (Engage with classroom updates - no comments)

💰 Payments (Billplz Integration)
├── Outstanding Bills (Itemized invoices with payment options)
├── Billplz Payment Integration
│   ├── Pay via Billplz (Online banking, e-wallets, cards)
│   ├── Billplz Payment Portal (Secure payment processing)
│   ├── Payment Confirmation (Real-time Billplz status updates)
│   └── Billplz Receipts (Automatic receipt from Billplz)
├── Manual Payment Upload
│   ├── Upload Receipt (Submit manual payment proof)
│   ├── Payment Status Tracking (Pending/Approved status)
│   └── Staff Verification (Manual approval notifications)
├── Payment History (Complete transaction records)
└── Bill Details (Itemized invoice breakdown with due dates)

💬 Messages
├── Create New Message (Send message to principal/staff with title and content)
├── Message History (All previous messages and replies)
├── Reply to Messages (Respond after staff replies - max 3 exchanges)
└── Important Messages (Starred or urgent communications)

📅 Calendar & Events
├── View Toggle (Calendar Mode OR List Mode)
├── Event Details (Full information for selected events)
└── Event Reminders (Automatic notifications for upcoming events)

👤 Profile
├── Parent Information (Current user details for editing)
├── Linked Children (View and update child information)
├── Link Additional Child (Request to link other children - admin verification)
├── Settings
│   ├── Notification Preferences (Payment reminders and updates)
│   └── App Information (Version, help, contact information)
└── Logout (Sign out of parent account)
```

---

## 🔄 Complete User Flows

### Flow 1: Teacher Daily Attendance
**Page Flow:** Home → Classroom → Select Classroom → Quick Actions: Attendance → Mark → Save
1. **Home Page** - View today's assigned classes
2. **Classroom Tab** - Access classroom management
3. **Select Classroom** - Choose from admin-assigned classrooms only
4. **Quick Actions** - Tap Attendance button
5. **Attendance Page** - Current day attendance for selected classroom
6. **Student List** - Display all students with names (no photos)
7. **Mark Status** - Tap Present/Absent for each student (no Late option)
8. **Add Remarks** - Optional notes for absent students
9. **Save Attendance** - Confirm and submit record
10. **Confirmation** - Success message and return to classroom dashboard

### Flow 2: Teacher Classroom Update
**Page Flow:** Home → Classroom → Select Classroom → Feed → Create Update → Tag Students → Post
1. **Home Page** - Access classroom navigation
2. **Classroom Tab** - Select classroom management
3. **Select Classroom** - Choose from assigned classrooms
4. **Feed Section** - Access classroom feed
5. **Create Update** - Text entry for activity description
6. **Tag Students** - Select students from class list
7. **Preview Post** - Review content and tagged students
8. **Post Update** - Submit to tagged students' parents
9. **Confirmation** - Success message with parent count

### Flow 3: Parent View Child Updates
**Page Flow:** Dashboard → My Child → Classroom Updates → View Details → Upvote
1. **Dashboard Page** - Swipe to child's overview card
2. **My Child Page** - Access full child information
3. **Classroom Updates** - View feed of tagged activities
4. **Update Details** - Read full content and view engagement
5. **Upvote Action** - Show appreciation for post (no comments)
6. **Return to Feed** - Continue viewing other updates

### Flow 4: Parent Payment Process
**Page Flow:** Dashboard → Payments → Upload Receipt → Submit → Confirmation
1. **Dashboard Page** - View payment reminder notification
2. **Payments Page** - See what is due and payment history
3. **Upload Receipt** - Take photo or select from gallery
4. **Payment Details** - Confirm amount and payment method
5. **Submit for Approval** - Send to principal for verification
6. **Confirmation** - Receipt uploaded successfully message
7. **Status Tracking** - Monitor approval status

### Flow 5: Principal Student Registration
**Page Flow:** Dashboard → Student Management → Add Student → Parent Linking → Save
1. **Dashboard Page** - Access management features
2. **Student Management** - Navigate to student records
3. **Add New Student** - Enter student basic information
4. **Parent Information** - Enter parent contact details
5. **Link Parent Account** - Create parent login credentials
6. **Class Assignment** - Select appropriate class (max 12 students)
7. **Save Record** - Confirm and create student profile
8. **Generate Token** - Provide parent with app access code

### Flow 6: Principal Payment Approval
**Page Flow:** Dashboard → Payment Management → Review Receipts → Approve → Update Status
1. **Dashboard Page** - View pending payment notifications
2. **Payment Management** - Access fee collection tools
3. **Review Receipts** - View uploaded payment proofs
4. **Verify Payment** - Check receipt details and amounts
5. **Approve/Reject** - Make verification decision
6. **Add Notes** - Include approval comments
7. **Update Status** - Change payment status to approved
8. **Notify Parent** - Automatic confirmation to parent

### Flow 7: Teacher Grading Flow
**Page Flow:** Home → Classroom → Select Classroom → Quick Actions: Grade Mark → Select Exam → Select Student → Grade
1. **Home Page** - Access classroom navigation
2. **Classroom Tab** - Select classroom management
3. **Select Classroom** - Choose from assigned classrooms
4. **Quick Actions** - Tap Grade Mark button
5. **Exam Selection** - Choose exam type (Midterm, Final, etc.)
6. **Student Selection** - Choose student from classroom list
7. **Subject Grading** - Rate each of 5 subjects
8. **Grade Entry** - Select grade level for each subject
9. **Add Comments** - Optional teacher notes
10. **Save Grades** - Confirm and submit assessment
11. **Confirmation** - Success message and grade saved

### Flow 8: Teacher Photo Attendance Flow (Enhanced)
**Page Flow:** Home → Classroom → Select Classroom → Quick Actions: Attendance → Camera → Photo Capture → Submit
1. **Home Page** - Access classroom navigation
2. **Classroom Tab** - Select classroom management
3. **Select Classroom** - Choose from assigned classrooms
4. **Quick Actions** - Tap Attendance button
5. **Camera Activation** - Automatic camera interface launch
6. **Individual Photo Capture** - Take photo of each student
7. **Photo Quality Check** - Verify clear face visibility
8. **Attendance Status** - Mark Present/Absent with photo
9. **Photo Upload** - All photos uploaded to backend storage
10. **Upload Confirmation** - Verify successful photo submission
11. **Submit Attendance** - Finalize attendance with photos
12. **Success Notification** - Confirmation of complete submission

### Flow 9: Financial Staff Manual Billing Creation Flow
**Page Flow:** Dashboard → Create Bill → Select Student → Add Items → Generate → Send
1. **Dashboard** - View outstanding bills and payment status
2. **Create Student Bill** - Access manual billing system
3. **Select Student** - Choose individual student for billing
4. **Add Line Items** - Enter tuition, meals, activities, fees
5. **Set Amounts** - Use fixed amounts (RM560 monthly, RM1280 registration)
6. **Generate Invoice** - Create invoice manually
7. **Review Invoice** - Verify invoice details and accuracy
8. **Send Notification** - Notify parents via mobile app
9. **Track Status** - Monitor payment status manually

### Flow 10: Parent Billplz Payment Flow
**Page Flow:** Dashboard → Payments → Select Bill → Pay via Billplz → Confirmation
1. **Dashboard** - View payment alerts and outstanding bills
2. **Payments Screen** - See itemized invoices with due dates
3. **Select Invoice** - Choose specific bill to pay
4. **Payment Options** - Choose between Billplz or manual upload
5. **Billplz Payment** - Redirected to Billplz payment portal
6. **Payment Method** - Select bank/e-wallet/card via Billplz
7. **Process Payment** - Complete payment via Billplz gateway
8. **Payment Confirmation** - Return to app with payment status
9. **Billplz Receipt** - Automatic receipt from Billplz
10. **Status Update** - Bill marked as paid in system

### Flow 11: Teacher Attendance Edit Flow (Approval Required)
**Page Flow:** Home → Classroom → Select Classroom → Quick Actions: Attendance → Past Records → Edit → Submit for Approval
1. **Home Page** - Access classroom navigation
2. **Classroom Tab** - Select classroom management
3. **Select Classroom** - Choose from assigned classrooms
4. **Quick Actions** - Tap Attendance button
5. **Past Records** - View historical attendance data
6. **Select Date** - Choose date to edit
7. **Edit Attendance** - Modify student attendance status
8. **Add Edit Reason** - Required explanation for change
9. **Submit for Approval** - Send edit request to admin
10. **Pending Status** - Edit marked as pending approval
11. **Notification** - Receive approval/rejection notification

---

## 📋 Standardization Notes

### Naming Conventions
- **Consistent Terminology:** "Student" (not "child" in admin context), "Parent" (not "guardian")
- **Action Verbs:** Create, Edit, View, Delete, Add, Remove, Update, Manage
- **Status Labels:** Active, Inactive, Pending, Approved, Rejected, Completed
- **Malaysian Context:** RM currency, Malaysian English terminology

### Interface Standards
- **Navigation:** Clear breadcrumbs and back buttons on all pages
- **Forms:** Required fields marked, validation messages, save/cancel options
- **Lists:** Search, filter, sort options where applicable
- **Notifications:** Success, error, warning, info message types
- **Loading States:** Progress indicators for all data operations

### Business Rules Applied
- **No Child Photos:** Only names and basic information throughout system
- **Payment Amounts:** RM560 monthly, RM1280 registration consistently
- **Class Limits:** Maximum 12 students per class enforced
- **Message Limits:** Parent-principal max 3 reply exchanges
- **Branch Restrictions:** All users operate within assigned branch only
- **Teacher Classroom Access:** Teachers only see admin-assigned classrooms
- **Attendance Restrictions:** Present/Absent only (no Late option)
- **Edit Approval:** Past attendance edits require admin approval
- **Grade Exam Linking:** All grades tied to specific exam types
- **Settings Simplified:** Basic notifications only, no theme or advanced options

### Technical Requirements
- **Responsive Design:** Mobile-first for parent/teacher, desktop-optimized for admin/principal
- **Offline Capability:** Core functions work without internet connection
- **Data Sync:** Automatic synchronization when connection restored
- **Security:** Role-based access control, secure authentication
- **Performance:** Fast loading, efficient data handling for 700+ students

---

**Final Status:** All sitemaps and flows are standardized and synchronized across platforms. Ready for development implementation.