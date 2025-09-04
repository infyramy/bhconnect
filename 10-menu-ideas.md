# Complete Menu Hierarchy & Navigation Structure

## 1. HQ ADMIN WEB APPLICATION

### Dashboard `/dashboard`
**Type**: Single Page with Widgets
**Components**: Analytics cards, charts, filters by date/branch
**Actions**: 
- Branch selector dropdown (modal: branch list with search)
- Analytics widgets (student count, revenue, teacher performance)
- Performance metrics (based on: attendance rates, payment completion, active users)

### Branch Management `/branches`
**Type**: Main Page + Modals
**Path**: `/branches`
**Components**: DataTable with filters, search, pagination
**Actions**:
- **Branch List** (main page: table with search, filter by status/region)
- **Add Branch** (modal: form with auto-principal creation)
- **Edit Branch** (modal: branch details form)
- **Branch Settings** (modal: select principal from admin list, branch config)
- **View Performance** (side panel: analytics for selected branch)

### User Management `/users`
**Type**: Tabbed Page + Modals
**Path**: `/users` (with tabs: admins, teachers, parents, students)
**Components**: DataTables per tab, search, filters

#### Admin Tab `/users?tab=admins`
- **Admin List** (main view: table with role badges)
- **Create Network Admin** (modal: form + global permissions checkboxes)
- **Edit Admin** (modal: details + permissions)

#### Teacher Tab `/users?tab=teachers`  
- **Teacher List** (main view: table with branch filter, performance metrics)
- **Add Teacher** (modal: basic info + branch assignment)
- **View Performance** (side panel: attendance completion, engagement metrics)

#### Parent Tab `/users?tab=parents`
- **Parent List** (main view: table with children count, payment status)
- **View Analytics** (side panel: payment history, engagement stats)

#### Student Tab `/users?tab=students`
- **Student List** (main view: table with branch/class filters)
- **View Analytics** (side panel: attendance, grade trends)

### Package Configuration `/packages`
**Type**: Single Page with Inline Editing
**Path**: `/packages`
**Components**: Cards for each package type, inline edit forms
**Actions**:
- **Programme Types** (cards: Full Day, Half Day, Custom with toggle states)
- **Set Amounts** (inline edit: price fields per package)
- **Billing Dates** (form: notification date, due date settings)

### Notifications & Announcements `/communications`
**Type**: Main Page + Modals
**Path**: `/communications`
**Components**: Tabs for create/history, rich text editor

#### Create Announcement
- **New Announcement** (page: rich text editor, target selection, schedule)
- Target options: Radio buttons (All Network, All Teachers, All Parents, Specific Branch)
- **Schedule** (optional: date/time picker)

#### History & Templates
- **History** (table: sent announcements with filters)
- **Templates** (list: reusable announcement templates)

### System Settings `/settings`
**Type**: Tabbed Page
**Path**: `/settings`
**Components**: Form sections, toggle switches

#### Global Settings
- **Notification Settings** (toggles: email, push, SMS preferences)
- **Billing Configuration** (form: payment gateway, invoice templates)

#### Audit & Reports  
- **Audit Logs** (table: all billing activities with filters by date/branch/user)
- **System Reports** (cards: exportable reports - revenue, user activity, performance)

---

## 2. BRANCH PRINCIPAL WEB APPLICATION

### Dashboard `/dashboard`
**Type**: Single Page with Widgets  
**Path**: `/dashboard`
**Components**: Branch-specific analytics, today's summary cards
**Actions**:
- **Branch Overview** (metrics: total students, teachers, today's attendance)
- **Teacher Activity** (list: recent teacher actions, attendance completion)
- **Today's Summary** (cards: key alerts, pending tasks, recent activities)

### Student Management `/students`
**Type**: Main Page + Modals/Side Panels
**Path**: `/students`
**Components**: DataTable, search, class filters

#### Student Operations
- **Student List** (main view: table with class assignment, status badges)
- **Add Student** (modal: form + package selection → auto-generates invoices)
- **Edit Student** (modal: student details, class assignment)
- **View Profile** (side panel: complete student info, parent details, billing history)

#### Class Management  
- **Class List** (sub-page: `/students/classes` - table of classes)
- **Create Class** (modal: class details, capacity, schedule)
- **Edit Class** (modal: class info, assigned students/teachers)
- **Assign Students** (modal: drag-drop interface or checkboxes)

### Teacher Management `/teachers`
**Type**: Main Page + Modals
**Path**: `/teachers`
**Components**: DataTable, performance indicators

#### Teacher Operations
- **Teacher List** (main view: table with class assignments, performance scores)
- **Add Teacher** (modal: teacher details + class assignment checkboxes)
- **Edit Teacher** (modal: teacher info, reassign classes)
- **View Performance** (side panel: attendance completion %, engagement metrics, parent feedback)

#### Class Assignments
- **Assignment Matrix** (page: grid showing teacher-class assignments)
- **Bulk Reassign** (modal: drag-drop or checkbox interface)

### Parent Management `/parents`
**Type**: Main Page + Modals  
**Path**: `/parents`
**Components**: DataTable, communication panel

#### Parent Operations
- **Parent List** (main view: table with linked children, contact status)
- **Edit Parent** (modal: contact details, link/unlink children)
- **Generate Access Code** (modal: parent account setup with QR code)

#### Communication
- **Parent Messages** (side panel: message threads, reply interface)
- **Message History** (table: all parent communications with search)

### Admin Account Management `/admins`
**Type**: Main Page + Modals
**Path**: `/admins` 
**Components**: DataTable, permission matrix

#### Admin Operations
- **Admin List** (main view: table with permission badges)
- **Create Admin** (modal: details + granular permission checkboxes)
  - Student Management Access
  - Teacher Management Access  
  - Parent Management Access
  - Billing Access
  - Reports Access
  - Message Permission
- **Edit Permissions** (modal: permission matrix with toggles)

### Billing & Invoices `/billing`
**Type**: Tabbed Page + Modals
**Path**: `/billing`
**Components**: Tables, charts, payment status indicators

#### Invoice Management
- **Student Billing** (main view: table per student with payment status)
- **Add Additional Items** (modal: select student, add items to current invoice)
- **Payment Monitoring** (dashboard: outstanding vs paid with charts)

#### Reports & Analytics
- **Invoice Reports** (table: exportable billing data with filters)
- **Payment Analytics** (charts: revenue trends, payment method breakdown)

### Reports `/reports`
**Type**: Dashboard with Export Options
**Path**: `/reports`
**Components**: Charts, tables, export buttons

#### Report Types
- **Attendance Reports** (charts: class attendance trends, student patterns)
- **Billing Analytics** (metrics: revenue, outstanding payments, payment methods)
- **Branch Performance** (dashboard: overall branch metrics vs network average)

### Notifications `/notifications`
**Type**: Main Page + Modals
**Path**: `/notifications`

#### Branch Communications
- **Create Announcement** (modal: rich text editor, target selection within branch)
- **Message Management** (page: parent inquiry queue with reply interface)
- **Announcement History** (table: sent branch announcements)

---

## 3. TEACHER WEB APPLICATION

### Dashboard `/dashboard`
**Type**: Single Page with Quick Actions
**Path**: `/dashboard`
**Components**: Today's schedule, quick action buttons, activity feed

#### Dashboard Elements
- **Assigned Classes** (cards: view-only class info with student counts)
- **Today's Summary** (alerts: pending attendance, grade submissions)
- **Quick Actions** (buttons: rapid attendance, grade entry shortcuts)
- **Recent Activity** (feed: recent posts, messages, notifications)

### Student Management `/students`
**Type**: Filtered Views (Only Assigned Classes)
**Path**: `/students`
**Components**: DataTable with class filters

#### Student Operations  
- **Student List** (main view: only assigned students with class grouping)
- **View Profile** (side panel: academic progress, notes, parent contact)
- **Progress Tracking** (page: grade trends, attendance patterns per student)
- **Student Notes** (modal: add/edit observations and notes)

### Attendance `/attendance`
**Type**: Process-Driven Pages
**Path**: `/attendance`
**Components**: Step-by-step interface, photo capture, review system

#### Attendance Process
- **Select Class** (page: class cards with student counts)
- **Daily Attendance** (page: student grid, one-by-one photo capture)
  - Present/Absent toggle per student
  - Photo capture modal for present students
  - Review page with thumbnails
  - Submit all photos to API
- **Attendance History** (table: past records with edit request buttons)
- **Photo Management** (gallery: stored attendance photos with dates)

### Grading & Assessment `/grades`
**Type**: Multi-Step Process
**Path**: `/grades`
**Components**: Selection dropdowns, grade input forms, history views

#### Grading Process
- **Grade Entry** (process page):
  - Step 1: Exam selection (Midterm, Final, Assessment)
  - Step 2: Student selection from assigned classes  
  - Step 3: Subject grading (5 areas: Reading, Numbers, Social, Physical, Creative)
  - Step 4: Review and save (tied to exam & student)
- **Progress Reports** (page: generate, preview, print reports)
- **Grade History** (table: past grades with comparison charts)

### Communication `/messages`
**Type**: Message Center Interface
**Path**: `/messages`
**Components**: Chat interface, announcement feed

#### Communication Features
- **Message Threads** (page: conversation view)
  - Parent Messages (reply-only, no initiation)
  - Principal/Admin Messages (two-way communication)
- **Announcements** (feed: branch & HQ notifications)
- **Message History** (archive: sent/received with search)

### Classroom Feed `/classroom`
**Type**: Social Feed Interface  
**Path**: `/classroom`
**Components**: Post composer, feed view, engagement metrics

#### Feed Management
- **Create Posts** (modal: text composer with student tagging)
- **Tag Students** (feature: child-specific posts with @ mentions)
- **Post Management** (actions: edit/delete own posts)
- **Parent Engagement** (metrics: view upvote counts, no direct interaction)

### Profile & Settings `/profile`
**Type**: Settings Page
**Path**: `/profile`
**Components**: Form sections, preference toggles

#### Profile Management
- **Teacher Info** (form: name, contact, photo upload)
- **Class Assignments** (read-only: current assignments)
- **Performance Metrics** (dashboard: attendance completion, engagement scores)
- **Settings** (preferences: notifications, app behavior)

---

## 4. TEACHER MOBILE APPLICATION

### Home `/home`
**Type**: Dashboard Screen with Cards
**Components**: Today's classes cards, quick action buttons, notification badges

#### Home Elements
- **Today's Classes** (cards: swipeable class list with student counts)
- **Quick Actions** (buttons: attendance shortcut, grade mark)
- **Notifications** (badge: announcements, messages count)
- **Activity Summary** (cards: recent activity overview)

### Classroom `/classroom`
**Type**: Multi-Screen Flow
**Navigation**: Tab-based with floating action buttons

#### Classroom Navigation
- **Select Classroom** (screen: admin-assigned classes only)
- **Dashboard** (screen: class overview with metrics)
- **Feed** (screen: create updates, tag students, view posts)

#### Quick Actions (Floating Action Buttons)
- **Attendance Flow**:
  - Screen 1: Student list (present/absent toggle)
  - Screen 2: Photo capture (one-by-one required)
  - Screen 3: Review (thumbnails, absent list)
  - Screen 4: Submit (API upload confirmation)
- **Grade Mark Flow**:
  - Screen 1: Exam selection
  - Screen 2: Student selection
  - Screen 3: Subject grading (5 areas with sliders/buttons)
  - Screen 4: Save confirmation

### Attendance History `/attendance-history`
**Type**: List Screen with Edit Requests
**Components**: List view, search, edit request modals

### Student Progress `/student-progress`
**Type**: Profile Screens
**Components**: Student cards, progress charts, notes

### Messages `/messages`
**Type**: Chat Interface
**Navigation**: Tabbed message center

#### Message Types
- **Parent Messages** (screen: reply-only threads)
- **Principal Messages** (screen: two-way communication)
- **Admin Messages** (screen: two-way communication)
- **Announcements** (screen: notification feed)
- **History** (screen: archived conversations)

### Profile `/profile`
**Type**: Settings Screen
**Components**: Profile form, preferences, logout

---

## 5. PARENT MOBILE APPLICATION

### Dashboard `/dashboard`
**Type**: Card-Based Dashboard
**Components**: Swipeable child cards, notification center, payment alerts

#### Dashboard Elements
- **Child Overview** (cards: swipeable for multiple children)
  - Today's attendance status (badge: present/absent/pending)
  - Latest classroom update summary
  - Child info (name, class, teacher with photos)
- **Notifications** (center: billing, announcements, messages with badges)
- **Payment Reminders** (alerts: due dates, overdue with amounts)
- **Announcements** (card: principal/HQ announcements)

### My Child `/child`
**Type**: Tab-Based Child Profile
**Navigation**: Child selector if multiple + tabs

#### Child Information Tabs
- **Attendance** (screen: simple list view, no calendar complexity)
- **Updates** (screen: teacher posts tagged to this child only)
  - View text-only updates
  - Upvote posts (no commenting allowed)
- **Progress** (screen: assessment results, grade reports)
- **Grades** (screen: midterm, final assessment grades with charts)

### Billing & Invoices `/billing`
**Type**: Payment-Focused Screens
**Navigation**: Tab-based billing center

#### Billing Features
- **Outstanding Invoices** (screen: list with due dates, amounts)
- **Payment Flow** (integrated Billplz):
  - Screen 1: Invoice details (monthly + additional items)
  - Screen 2: Payment method selection (FPX, e-wallets, cards)
  - Screen 3: Payment confirmation (automatic receipt)
  - Screen 4: Status confirmation (real-time updates)
- **Payment History** (screen: transaction records with search)
- **Notifications** (settings: 25th monthly alerts, overdue reminders)

### Messages `/messages`
**Type**: Communication Center
**Navigation**: Compose + history tabs

#### Messaging Features
- **Send Message** (screen: compose with subject/content required)
- **Branch Communication** (feature: sent to principal/admin with message permission)
- **Message Threading** (limitation: up to 3 exchanges per inquiry)
- **History** (screen: conversation archive with search)
- **Announcements** (screen: important HQ & branch notifications)

### Profile `/profile`  
**Type**: Settings & Account Management
**Navigation**: Section-based profile

#### Profile Sections
- **Parent Info** (section: personal details, contact, photo)
- **Linked Children** (section: current children with link/unlink actions)
  - View child details
  - Request additional child linking (admin verification required)
- **Settings** (section: notification preferences, app language)
- **Support** (section: contact branch, FAQ access)

---

## NAVIGATION PATHS & TECHNICAL DECISIONS

### Modal vs Page Decisions:

**Use Modals For**:
- Quick forms (add user, edit details)
- Confirmations (delete, submit)
- Photo capture workflows
- Simple selections (class assignment, permission toggles)
- Quick views (student profile summary)

**Use New Pages For**:
- Complex data entry (student enrollment)
- List views with filters/search (student list, teacher list)
- Multi-step processes (attendance workflow, grading)
- Dashboard/analytics views
- Report generation and viewing

### URL Structure Examples:
- HQ: `/hq/dashboard`, `/hq/branches`, `/hq/users?tab=teachers`
- Branch: `/branch/dashboard`, `/branch/students`, `/branch/billing`
- Teacher Web: `/teacher/dashboard`, `/teacher/attendance`, `/teacher/grades`
- Teacher Mobile: `/home`, `/classroom`, `/messages` (app navigation)
- Parent Mobile: `/dashboard`, `/child/{childId}`, `/billing` (app navigation)

### Data-Driven Analytics:
- **Attendance metrics**: Based on daily photo submissions
- **Payment analytics**: Based on invoice status and payment gateway data
- **Engagement scores**: Based on post interactions, message frequency
- **Performance metrics**: Based on grade submissions, attendance completion rates
- **User activity**: Based on login frequency, feature usage patterns

All metrics reference actual captured data points from the system's core functions.