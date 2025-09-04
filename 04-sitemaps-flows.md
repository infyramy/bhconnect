# System Sitemaps & User Flows

## Web Application Sitemaps

### HQ Admin Sitemap
```
Dashboard `/dashboard`
├── Branch Selector (modal: branch list with search)
├── Analytics Widgets (student count, revenue, teacher performance)
└── Performance Metrics (attendance rates, payment completion, active users)

Branch Management `/branches`
├── Branch List (main page: table with search, filter by status/region)
├── Add Branch (modal: form with auto-principal creation)
├── Edit Branch (modal: branch details form)
├── Branch Settings (modal: select principal from admin list, branch config)
└── View Performance (side panel: analytics for selected branch)

User Management `/users` (with tabs: admins, teachers, parents, students)
├── Admin Tab `/users?tab=admins`
│   ├── Admin List (main view: table with role badges)
│   ├── Create Network Admin (modal: form + global permissions checkboxes)
│   └── Edit Admin (modal: details + permissions)
├── Teacher Tab `/users?tab=teachers`
│   ├── Teacher List (main view: table with branch filter, performance metrics)
│   ├── Add Teacher (modal: basic info + branch assignment)
│   └── View Performance (side panel: attendance completion, engagement metrics)
├── Parent Tab `/users?tab=parents`
│   ├── Parent List (main view: table with children count, payment status)
│   └── View Analytics (side panel: payment history, engagement stats)
└── Student Tab `/users?tab=students`
    ├── Student List (main view: table with branch/class filters)
    └── View Analytics (side panel: attendance, grade trends)

Package Configuration `/packages`
├── Programme Types (cards: Full Day, Half Day, Custom with toggle states)
├── Set Amounts (inline edit: price fields per package)
└── Billing Dates (form: notification date, due date settings)

Notifications & Announcements `/communications`
├── Create Announcement
│   ├── New Announcement (page: rich text editor, target selection, schedule)
│   ├── Target Options (radio buttons: All Network, All Teachers, All Parents, Specific Branch)
│   └── Schedule (optional: date/time picker)
├── History (table: sent announcements with filters)
└── Templates (list: reusable announcement templates)

System Settings `/settings`
├── Global Settings
│   ├── Notification Settings (toggles: email, push, SMS preferences)
│   └── Billing Configuration (form: payment gateway, invoice templates)
└── Audit & Reports
    ├── Audit Logs (table: all billing activities with filters by date/branch/user)
    └── System Reports (cards: exportable reports - revenue, user activity, performance)
```

### Branch Principal Sitemap
```
Dashboard `/dashboard`
├── Branch Overview (metrics: total students, teachers, today's attendance)
├── Teacher Activity (list: recent teacher actions, attendance completion)
└── Today's Summary (cards: key alerts, pending tasks, recent activities)

Student Management `/students`
├── Student Operations
│   ├── Student List (main view: table with class assignment, status badges)
│   ├── Add Student (modal: form + package selection → auto-generates invoices)
│   ├── Edit Student (modal: student details, class assignment)
│   └── View Profile (side panel: complete student info, parent details, billing history)
└── Class Management
    ├── Class List (sub-page: `/students/classes` - table of classes)
    ├── Create Class (modal: class details, capacity, schedule)
    ├── Edit Class (modal: class info, assigned students/teachers)
    └── Assign Students (modal: drag-drop interface or checkboxes)

Teacher Management `/teachers`
├── Teacher Operations
│   ├── Teacher List (main view: table with class assignments, performance scores)
│   ├── Add Teacher (modal: teacher details + class assignment checkboxes)
│   ├── Edit Teacher (modal: teacher info, reassign classes)
│   └── View Performance (side panel: attendance completion %, engagement metrics, parent feedback)
└── Class Assignments
    ├── Assignment Matrix (page: grid showing teacher-class assignments)
    └── Bulk Reassign (modal: drag-drop or checkbox interface)

Parent Management `/parents`
├── Parent Operations
│   ├── Parent List (main view: table with linked children, contact status)
│   ├── Edit Parent (modal: contact details, link/unlink children)
│   └── Generate Access Code (modal: parent account setup with QR code)
└── Communication
    ├── Parent Messages (side panel: message threads, reply interface)
    └── Message History (table: all parent communications with search)

Admin Account Management `/admins`
├── Admin Operations
│   ├── Admin List (main view: table with permission badges)
│   ├── Create Admin (modal: details + granular permission checkboxes)
│   │   ├── Student Management Access
│   │   ├── Teacher Management Access
│   │   ├── Parent Management Access
│   │   ├── Billing Access
│   │   ├── Reports Access
│   │   └── Message Permission
│   └── Edit Permissions (modal: permission matrix with toggles)

Billing & Invoices `/billing`
├── Invoice Management
│   ├── Student Billing (main view: table per student with payment status)
│   ├── Add Additional Items (modal: select student, add items to current invoice)
│   └── Payment Monitoring (dashboard: outstanding vs paid with charts)
└── Reports & Analytics
    ├── Invoice Reports (table: exportable billing data with filters)
    └── Payment Analytics (charts: revenue trends, payment method breakdown)

Reports `/reports`
├── Attendance Reports (charts: class attendance trends, student patterns)
├── Billing Analytics (metrics: revenue, outstanding payments, payment methods)
└── Branch Performance (dashboard: overall branch metrics vs network average)

Notifications `/notifications`
├── Create Announcement (modal: rich text editor, target selection within branch)
├── Message Management (page: parent inquiry queue with reply interface)
└── Announcement History (table: sent branch announcements)
```

### Teacher Web Sitemap
```
Dashboard `/dashboard`
├── Assigned Classes (cards: view-only class info with student counts)
├── Today's Summary (alerts: pending attendance, grade submissions)
├── Quick Actions (buttons: rapid attendance, grade entry shortcuts)
└── Recent Activity (feed: recent posts, messages, notifications)

Student Management `/students` (Filtered Views - Only Assigned Classes)
├── Student List (main view: only assigned students with class grouping)
├── View Profile (side panel: academic progress, notes, parent contact)
├── Progress Tracking (page: grade trends, attendance patterns per student)
└── Student Notes (modal: add/edit observations and notes)

Attendance `/attendance` (Process-Driven Pages)
├── Select Class (page: class cards with student counts)
├── Daily Attendance (page: student grid, one-by-one photo capture)
│   ├── Present/Absent toggle per student
│   ├── Photo capture modal for present students
│   ├── Review page with thumbnails
│   └── Submit all photos to API
├── Attendance History (table: past records with edit request buttons)
└── Photo Management (gallery: stored attendance photos with dates)

Grading & Assessment `/grades` (Multi-Step Process)
├── Grade Entry (process page):
│   ├── Step 1: Exam selection (Midterm, Final, Assessment)
│   ├── Step 2: Student selection from assigned classes
│   ├── Step 3: Subject grading (5 areas: Reading, Numbers, Social, Physical, Creative)
│   └── Step 4: Review and save (tied to exam & student)
├── Progress Reports (page: generate, preview, print reports)
└── Grade History (table: past grades with comparison charts)

Communication `/messages` (Message Center Interface)
├── Message Threads (page: conversation view)
│   ├── Parent Messages (reply-only, no initiation)
│   └── Principal/Admin Messages (two-way communication)
├── Announcements (feed: branch & HQ notifications)
└── Message History (archive: sent/received with search)

Classroom Feed `/classroom` (Social Feed Interface)
├── Create Posts (modal: text composer with student tagging)
├── Tag Students (feature: child-specific posts with @ mentions)
├── Post Management (actions: edit/delete own posts)
└── Parent Engagement (metrics: view upvote counts, no direct interaction)

Profile & Settings `/profile`
├── Teacher Info (form: name, contact, photo upload)
├── Class Assignments (read-only: current assignments)
├── Performance Metrics (dashboard: attendance completion, engagement scores)
└── Settings (preferences: notifications, app behavior)
```

## Mobile Application Sitemaps

### Teacher Mobile Sitemap
```
Home `/home` (Dashboard Screen with Cards)
├── Today's Classes (cards: swipeable class list with student counts)
├── Quick Actions (buttons: attendance shortcut, grade mark)
├── Notifications (badge: announcements, messages count)
└── Activity Summary (cards: recent activity overview)

Classroom `/classroom` (Multi-Screen Flow - Tab-based with floating action buttons)
├── Select Classroom (screen: admin-assigned classes only)
├── Dashboard (screen: class overview with metrics)
├── Feed (screen: create updates, tag students, view posts)
└── Quick Actions (Floating Action Buttons)
    ├── Attendance Flow:
    │   ├── Screen 1: Student list (present/absent toggle)
    │   ├── Screen 2: Photo capture (one-by-one required)
    │   ├── Screen 3: Review (thumbnails, absent list)
    │   └── Screen 4: Submit (API upload confirmation)
    └── Grade Mark Flow:
        ├── Screen 1: Exam selection
        ├── Screen 2: Student selection
        ├── Screen 3: Subject grading (5 areas with sliders/buttons)
        └── Screen 4: Save confirmation

Attendance History `/attendance-history` (List Screen with Edit Requests)
├── List view with search
└── Edit request modals

Student Progress `/student-progress` (Profile Screens)
├── Student cards
├── Progress charts
└── Notes

Messages `/messages` (Chat Interface - Tabbed message center)
├── Parent Messages (screen: reply-only threads)
├── Principal Messages (screen: two-way communication)
├── Admin Messages (screen: two-way communication)
├── Announcements (screen: notification feed)
└── History (screen: archived conversations)

Profile `/profile` (Settings Screen)
├── Profile form
├── Preferences
└── Logout
```

### Parent Mobile Sitemap
```
Dashboard `/dashboard` (Card-Based Dashboard)
├── Child Overview (cards: swipeable for multiple children)
│   ├── Today's attendance status (badge: present/absent/pending)
│   ├── Latest classroom update summary
│   └── Child info (name, class, teacher with photos)
├── Notifications (center: billing, announcements, messages with badges)
├── Payment Reminders (alerts: due dates, overdue with amounts)
└── Announcements (card: principal/HQ announcements)

My Child `/child` (Tab-Based Child Profile - Child selector if multiple + tabs)
├── Attendance (screen: simple list view, no calendar complexity)
├── Updates (screen: teacher posts tagged to this child only)
│   ├── View text-only updates
│   └── Upvote posts (no commenting allowed)
├── Progress (screen: assessment results, grade reports)
└── Grades (screen: midterm, final assessment grades with charts)

Billing & Invoices `/billing` (Payment-Focused Screens - Tab-based billing center)
├── Outstanding Invoices (screen: list with due dates, amounts)
├── Payment Flow (integrated Billplz):
│   ├── Screen 1: Invoice details (monthly + additional items)
│   ├── Screen 2: Payment method selection (FPX, e-wallets, cards)
│   ├── Screen 3: Payment confirmation (automatic receipt)
│   └── Screen 4: Status confirmation (real-time updates)
├── Payment History (screen: transaction records with search)
└── Notifications (settings: 25th monthly alerts, overdue reminders)

Messages `/messages` (Communication Center - Compose + history tabs)
├── Send Message (screen: compose with subject/content required)
├── Branch Communication (feature: sent to principal/admin with message permission)
├── Message Threading (limitation: up to 3 exchanges per inquiry)
├── History (screen: conversation archive with search)
└── Announcements (screen: important HQ & branch notifications)

Profile `/profile` (Settings & Account Management - Section-based profile)
├── Parent Info (section: personal details, contact, photo)
├── Linked Children (section: current children with link/unlink actions)
│   ├── View child details
│   └── Request additional child linking (admin verification required)
├── Settings (section: notification preferences, app language)
└── Support (section: contact branch, FAQ access)
```

## Key User Flows

### HQ Branch Creation Flow
1. HQ creates new branch → Auto-generates Principal account
2. Principal account created with full branch permissions
3. HQ can later reassign principal role to different admin account via Branch Settings

### Branch Principal Admin Account Creation Flow
1. Principal goes to Admin Account Management → Create Admin Account
2. Set user details and select page category permissions:
   - Student Management Access (View, Add, Edit)
   - Teacher Management Access (View, Add, Edit, Assign Classes)
   - Parent Management Access (View, Communication)
   - Billing Access (View Invoices, Add Additional Items)
   - Reports Access (Attendance, Billing, Performance)
   - Message Permission (Handle Parent Messages)
3. Admin account activated with specific permissions only

### Teacher One-by-One Attendance Flow
1. Open Classroom → Select Class → Attendance
2. For each present student: Select → Snap photo → Save with thumbnail
3. Review all thumbnails and absent list
4. Final save sends all photos to API storage

### Parent Billing Notification Flow
1. Receive notification on 25th (HQ configured date)
2. Tap notification → View invoice (monthly + additional items)
3. Tap Pay → Redirect to Billplz
4. Complete payment → Automatic receipt and status update

### Student Enrollment Auto-Invoice Flow
1. Principal adds student → Select package → Fill details
2. System auto-generates: Registration fee + monthly invoices from enrollment month to year-end
3. Parent receives access code → Sets up account with linked student

### Additional Item Billing Flow
1. Principal/Admin selects student
2. Add items to current month invoice (before 25th) - No parent approval needed
3. Items added to existing monthly invoice
4. Parent receives combined invoice on notification date

### Parent Messaging Flow
1. Parent opens Messages → Send Message to Branch
2. Message sent to Branch (received by Principal OR Admin with Message Permission)
3. Branch Principal/Admin replies through web app
4. Parent receives reply in mobile app
5. Maximum 3 exchanges per message thread

### HQ Announcement Flow
1. HQ creates announcement → Select target audience:
   - All Network (Everyone)
   - All Teachers (Network-wide)
   - All Parents (Network-wide)
   - Specific Branch (Branch users only)
2. Announcement sent via push notification
3. Recipients receive in mobile app notifications

### Branch Announcement Flow
1. Branch Principal creates announcement → Select target:
   - All Branch Users
   - Branch Teachers only
   - Branch Parents only
2. Announcement sent to branch-related users only
3. Recipients receive in mobile app notifications

## System Business Rules

### Attendance
- Photo mandatory for present students only
- No backup methods for unclear photos
- One-by-one process required
- Past edits require admin approval

### Billing
- HQ configurable package amounts
- Additional items: no parent approval, no spending limits
- Auto-reminders for unpaid invoices after due date
- Audit logs for all billing activities

### Communication
- Classroom posts: text only, no approval required
- Parent messages: sent to branch (handled by Principal OR Admin with Message Permission)
- Branch Principal/Admin with permissions handles parent communication
- HQ and branch can create targeted announcements
- Message threading with maximum 3 exchanges per inquiry

### System Configuration
- HQ auto-creates principal accounts when creating branches
- Branch principals create admin accounts with specific page permissions
- HQ sets all package amounts and billing dates
- Billing system generates invoices during enrollment
- Admin accounts have granular permissions for page categories