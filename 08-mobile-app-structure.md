# Mobile App Structure - BrightHill Connect

**Purpose:** Planning document for 2-developer team  
**Goal:** Simple, kid-friendly, fast to build mobile app  
**Target:** Teachers & Parents daily use at BrightHill Preschool Network  
**Context:** 700 students across branches, 12 students per class, Malaysian environment

---

## Project Overview

### Core Principles
- **SIMPLE** - Minimal screens, clear navigation
- **KID-FRIENDLY** - Bright colors, large buttons, easy to understand
- **FAST TO BUILD** - Use standard components, avoid complex features
- **MEETS REQUIREMENTS** - All essential features covered

### BrightHill Context
- **Network Size:** 700+ students across multiple branches in Malaysia
- **Class Structure:** Maximum 12 students per class for optimal teacher-student ratio
- **Fee Structure:** RM560 monthly fees, RM1280 registration fee
- **Languages:** English with Malaysian context and terminology

### Mobile App Users
- **Teachers** - Daily attendance, post text updates, simple messaging
- **Parents** - View child updates, make payments, communicate with teachers

---

## 📱 App Structure

### Teacher App: 4 Bottom Tab Navigation
### Parent App: 5 Screens (Unchanged)

### 👩‍🏫 Teacher App (4 Main Bottom Tabs)

#### 1. HOME - Daily Overview
**Purpose:** Today's assigned classes and quick actions
- Current Class Overview (Today's assigned classes only)
- Quick Actions Dashboard (Attendance shortcuts, announcements)
- Recent Activity Summary (Latest updates and notifications)
- Daily Schedule (Current and upcoming classes)

Note: Focus on daily productivity and quick access

#### 2. CLASSROOM - Class Management Hub
**Purpose:** Comprehensive classroom management
- **Classroom Selection** (List of admin-assigned classrooms ONLY)
- **Selected Classroom Dashboard:**
  - **Summary** (Student overview, performance metrics, recent activity)
  - **Feed** (Create/edit text updates, tag students, view upvotes)
  - **Quick Actions:**
    - **Attendance** (Current day attendance marking)
    - **Grade Mark** (Assessment entry for exams)

**Key Rules:**
- Teachers only see classrooms assigned by admin
- Cannot access unassigned classrooms
- All actions restricted to assigned classrooms

#### 3. MESSAGES - Same Branch Communication
**Purpose:** Communicate within branch only
- Message Center with parent inquiries (reply only)
- Send messages to principal or admin (two-way)
- **Single person targeting** - no group messages
- Pull to refresh (no real-time chat)
- Basic text messaging only
- **Branch restriction:** Can only message people in same branch

Note: Teachers can reply to parents and send to principal/admin in same branch

#### 4. PROFILE - Account Management
**Purpose:** Personal settings and account info
- View Profile (Teacher name, contact info, assigned classes)
- Edit Profile (Update contact information)
- Settings (Notification preferences, app information)
- Logout (Sign out of teacher account)

### Detailed Classroom Flows

#### Photo Attendance Flow (From Classroom Quick Action)
1. Teacher goes to **Classroom → Select Classroom → Quick Action: Attendance**
2. **Current Day Attendance** for selected classroom (today's date)
3. **Camera Interface Activation** - Automatic camera mode
4. **Individual Student Photo Capture:**
   - Take photo of each student individually
   - Clear face visibility required
   - Failed photos must be retaken
5. **Mark Attendance with Photo** - Present/Absent with photo verification
6. **Add Remarks** - Optional notes for absent students
7. **Submit Attendance with Photos** - All photos uploaded to backend
8. **Upload Confirmation** - Verify all photos submitted successfully
9. **Past Records** - View/edit historical data
10. **Edit Approval Required** - Past attendance edits need admin approval

**Photo Requirements:**
- **Mandatory Photos:** Cannot save attendance without individual student photos
- **Quality Standards:** Clear, identifiable student faces required
- **Backend Storage:** All photos automatically uploaded to secure storage
- **Admin Access:** Photos available for administrative review

#### Grading Flow (From Classroom Quick Action)
1. Teacher goes to **Classroom → Select Classroom → Quick Action: Grade Mark**
2. **Exam Selection** - Choose exam type (Midterm, Final, etc.)
3. **Student Selection** - Choose student from classroom
4. **Subject Areas** - Rate in 5 areas: Reading, Numbers, Social, Physical, Creative
5. **Grade Entry** - Excellent/Good/Satisfactory/Needs Support
6. **Teacher Comments** - Optional notes for each subject
7. **Save Grades** - Tied to both exam type and student
8. **Grade History** - View previous assessments for comparison

### 👨‍👩‍👧‍👦 Parent App (5 Main Screens)

#### 1. HOME - Child Overview Dashboard
**Purpose:** Swipeable cards for each child
- Child Overview Cards (Swipeable - one card per child)
  - Child name and basic info (no photos)
  - Today's attendance status
  - Latest classroom update summary
- Principal Announcements Card (replaces week summary)
- Payment reminders for any child

#### 2. MY CHILD - Child Information
**Purpose:** Simple child information and classroom updates
- Child basic info (name, class, teacher - no photos)
- Attendance history (simple list view - no weekly calendar)
- Classroom Updates (text only classroom feed)
- Progress reports and grades from assessments
- Upvote classroom posts (no commenting allowed)

Note: Weekly calendar and media gallery removed - classroom specific updates only

#### 3. PAYMENTS - Billplz Integration & Manual Upload
**Purpose:** Payment management with Billplz and manual proof upload
- **Outstanding Bills** (view unpaid invoices with details)
- **Billplz Payment Integration** (pay online via Billplz - FPX, e-wallets, cards)
- **Payment History** (complete transaction records)
- **Payment Status Tracking** (Billplz confirmations and manual approvals)
- **Manual Payment Upload** (upload bank transfer/cash payment proofs)
- **Bill Details** (itemized invoices with fixed amounts)
- **Staff Verification** (manual approval process for uploaded proofs)

**Payment Features:**
- **Pay via Billplz** - redirected to secure Billplz payment portal
- **Malaysian Payment Methods** - FPX, e-wallets, cards via Billplz
- **Manual Payment Proof Upload** - for bank transfer/cash payments
- **Payment Status Tracking** - monitor Billplz and manual payment approvals
- **Fixed Amounts** - RM560 monthly, RM1280 registration

#### 4. MESSAGES - Simple Messaging
**Purpose:** Basic message system
- Create Message (title and content only)
- Send to principal/admin/staff
- View Previous Messages (simple list)
- Receive replies (can reply up to 3 exchanges per thread)

Note: No drafts, templates, search, filters, analytics, or email features. All inquiries are now called "messages"

#### 5. PROFILE - User Settings
**Purpose:** Basic user account management
- Current user details (parent info for edit/update - no family photo)
- Linked children info (view and update)
- Link other children (request verification by admin)
- Basic settings (notifications only)

Note: No family photo, only user-specific settings

---

## Complete User Flows with Components

### Teacher Daily Flow - Detailed Steps

#### Morning Attendance Flow (5-7 minutes)
1. **Login Screen**
   - Email/password fields
   - "Login" button
   - "Forgot Password" link

2. **Home Dashboard**
   - "Today's Classes" card showing class names and student counts
   - "Quick Actions" section with large buttons
   - "Mark Attendance" primary button (prominent)
   - Recent messages notification badge

3. **Mark Attendance Flow**
   - "Select Class" dropdown/picker
   - Student grid view with names only
   - For each student:
     - Student name (clear, readable)
     - Class and basic info
     - Three status buttons: "Present" (green), "Absent" (red), "Late" (orange)
     - Optional "Add Note" text field for absences
   - "Save Attendance" button at bottom
   - Confirmation toast: "Attendance saved for [Class Name]"

#### Classroom Updates Flow (3-5 minutes)
4. **Classroom Updates Screen**
   - "Take Photo" camera button (large, centered)
   - "Write Caption" text area
   - "Tag Students" section:
     - List of student names
     - Tap to select/deselect students
     - Selected students highlighted with checkmark
   - "Post Update" button (disabled until students tagged)
   - Success message: "Update shared with [X] parents"

### Parent Daily Flow - Detailed Steps

#### Morning Check Flow (2-3 minutes)
1. **Home Dashboard**
   - Child's name and basic info with today's attendance status
   - "Latest Updates" section showing recent tagged classroom posts
   - "Messages" section with unread count badge
   - "Payments" section with due date alerts

2. **My Child Screen**
   - Child profile header with name and basic info
   - Tabs: "Attendance", "Photos", "Progress", "Growth"
   - **Attendance Tab:** Calendar view with color-coded dates
   - **Photos Tab:** Grid of all tagged photos with upvote buttons
   - **Progress Tab:** Latest assessment reports
   - **Growth Tab:** Height/weight tracking charts

#### Payment Flow (When Due)
3. **Payments Screen**
   - "Outstanding Invoices" section at top
   - Invoice card showing:
     - Invoice number and date
     - Amount: "RM560" (large, bold)
     - Due date with countdown
     - "Upload Receipt" button
   - **Upload Receipt Flow:**
     - Camera capture or photo library selection
     - Preview uploaded image
     - "Submit for Approval" button
     - Status tracking: "Pending Approval" → "Approved"

### Message Flow - Email Style

#### Parent Initiating Message
1. **Messages Screen (Parent)**
   - "Compose New Message" button at top
   - **Compose Flow:**
     - "To:" field pre-filled with child's teacher
     - "Subject:" required text field
     - "Message:" text area
     - "Attach Photo" optional button
     - "Send" button

#### Teacher Reply Flow
2. **Messages Screen (Teacher)**
   - Inbox showing parent inquiries with unread badges
   - **Reply Flow:**
     - Original message thread display
     - "Reply" text area at bottom
     - Subject line automatically prefixed with "Re:"
     - "Send Reply" button

### CRUD Operations Required

#### Student Management (Admin/Principal Web)
- **Create:** Add new student form with parent linking
- **Read:** Student list with search and filters
- **Update:** Edit student information and class assignment
- **Delete:** Deactivate student (soft delete)

#### Attendance Management
- **Create:** Mark daily attendance with status and notes
- **Read:** View attendance records with filtering
- **Update:** Modify attendance status if needed
- **Delete:** Remove incorrect attendance entries

#### Payment Management
- **Create:** Generate monthly invoices automatically
- **Read:** View payment history and status
- **Update:** Approve uploaded receipt proofs
- **Delete:** Cancel incorrect invoices

#### Communication Management
- **Create:** Send new messages with subjects
- **Read:** View message threads and history
- **Update:** Mark messages as read/important
- **Delete:** Archive old message threads

### Important System Rules
- **Child-Specific Content:** Parents only see posts tagged with their child
- **Message Direction:** Parents inquire → Teachers reply
- **Photo Interaction:** Upvote only, no comments allowed
- **Attendance Timing:** Must be marked by 10 AM daily
- **Payment Verification:** All receipts require principal approval

---

## 💡 Development Priorities

### Phase 1 - Essential (Week 1-2)
- **Authentication** - Login for teachers/parents
- **Basic Navigation** - 5 screens each app
- **Attendance** - Mark present/absent with student names
- **Classroom Updates** - Post updates, tag students, notify parents

### Phase 2 - Core Features (Week 3-4)
- **Messaging** - Email-style communication
- **Payments** - Upload receipt photos, track status
- **Child Profile** - Attendance history, classroom updates

### Phase 3 - Polish (Week 5-6)
- **Assessments** - Simple grading system
- **Notifications** - Payment reminders, new photos
- **Settings** - Profiles, preferences

---

## 🎨 Design Requirements

### Visual Style
- **Colors:** Bright, cheerful but professional
- **Buttons:** Large, easy to tap (minimum 48px)
- **Text:** Clear, readable fonts (minimum 16px)
- **Names:** Student names clearly displayed for easy identification

### Kid-Friendly Elements
- **Rounded corners** on all buttons and cards
- **Bright color accents** (blues, greens, oranges)
- **Large icons** that are easy to understand
- **Consistent layout** - same pattern on every screen

### Mobile-First Principles
- **Thumb-friendly navigation** - tabs at bottom
- **Swipe gestures** - swipe right = present, swipe left = absent
- **Pull to refresh** - no auto-refresh, user controls updates
- **Offline ready** - work without internet, sync when connected

---

## 📋 Business Rules (Simple)

### BrightHill Fee Structure (Real Data)
- **Monthly fee:** RM560 per student (includes tuition and meals)
- **Registration fee:** RM1280 one-time payment for new students
- **Due date:** 5th of each month for monthly fees
- **Payment method:** Bank transfer preferred, upload receipt photo for verification
- **Late fee:** RM10 after 7 days grace period
- **Class capacity:** Maximum 12 students per class

### Assessment System
- **Two assessments per year:** Mid-year (December) and Final (May)
- **Five subject areas:** Reading, Numbers, Social Skills, Physical, Creative
- **Simple grading:** Excellent, Good, Satisfactory, Needs Support
- **Teacher comments:** Optional text for each subject

### Communication Rules (Updated System)
- **Email-style:** Subject lines required, no real-time chat
- **Child-specific:** Parents only see content about their child
- **Message Flow:** Parents send inquiries, teachers reply only
- **Classroom Feed:** Photo/text posts with upvote only (no comments)
- **Professional tone:** Malaysian English, templates for common messages

### Automated Reminder System
- **Fee reminders:** 7 days, 3 days, 1 day before due date
- **Overdue notices:** 1 day, 7 days after due date (with late fee warning)
- **Attendance alerts:** If child not marked present by 10 AM
- **Assessment reminders:** 2 weeks before assessment periods
- **Message notifications:** Push notification for new messages

---

## 🚀 Success Metrics

### For Teachers
- **Attendance completion:** 100% of classes marked daily
- **Photo sharing:** At least 1 post per day per class
- **Response time:** Reply to parent messages within 24 hours

### For Parents
- **App engagement:** Check app at least once daily
- **Payment success:** Pay fees on time (before due date)
- **Communication:** Respond to teacher messages when needed

### For School
- **Reduced paperwork:** 90% reduction in manual attendance sheets
- **Improved communication:** Replace WhatsApp with app messaging
- **Better payment tracking:** Automated fee collection monitoring

---

## 📱 Platform Strategy

### Mobile-First Approach
- **Primary users:** Teachers and parents use mobile daily
- **Secondary platform:** Web app for admin/principals only
- **Design priority:** Mobile experience must be perfect

### Offline Capability
- **Mark attendance** without internet
- **View photos** downloaded to phone
- **Write messages** and send when connected
- **Essential functions** work offline

---

## ⚡ Quick Reference for Developers

### Web App Developer Focus
- **Admin dashboard** with student/teacher management
- **Fee collection** tracking and invoice generation
- **Reports and analytics** for principals and HQ
- **User management** and system settings

### Mobile App Developer Focus  
- **Simple 5-screen navigation** for each user type
- **Text updates and posting** with student tagging
- **Basic messaging** system (email-style)
- **Payment receipt upload** functionality

### Shared Backend Needs
- **User authentication** for all platforms
- **Student and class data** management
- **File storage** for photos and receipts
- **Notification system** for reminders

---

**Key Success Factor:** Keep everything SIMPLE. If a feature seems complex, break it into smaller pieces or find a simpler solution. The goal is fast development and easy daily use.