# Mobile App Structure - BrightHill Connect

**Auto-Billing System, One-by-One Photo Attendance, HQ Configurable Packages**

## 📱 Mobile App Users
- **Teachers** - One-by-one photo attendance, text classroom updates
- **Parents** - Auto-billing notifications, Billplz payments, child updates

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

#### One-by-One Photo Attendance Flow (From Classroom Quick Action)
1. Teacher goes to **Classroom → Select Classroom → Quick Action: Attendance**
2. **Current Day Attendance** for selected classroom (today's date)
3. **Student List Display** - View all students in class
4. **One-by-One Process:** For each student wanting to mark present:
   - **Select Present** - Tap student name to mark present
   - **Snap Photo** - Take individual photo of that student
   - **Save Individual** - Photo saved with thumbnail and present mark
5. **Absent Students** - Students not marked present (no photo needed)
6. **Review Attendance** - See thumbnails for present students, absent list
7. **Final Save** - Click save to send all photos to storage via API
8. **API Upload** - All photos uploaded to backend storage
9. **Success Confirmation** - All attendance and photos saved successfully
10. **Past Records** - View/edit historical data
11. **Edit Approval Required** - Past attendance edits need admin approval

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

#### 3. PAYMENTS - Auto-Billing with Billplz Integration
**Purpose:** Auto-billing notification and payment management
- **Auto-Billing Notifications** (receive notifications on HQ configured date - 25th)
- **Invoice Details** (view monthly fee + additional items in single invoice)
- **Billplz Payment Integration** (immediate redirect to Billplz payment portal)
- **Payment History** (complete automatic transaction records)
- **Payment Status Tracking** (real-time Billplz confirmations)
- **Automatic Receipts** (Billplz provides instant payment confirmations)

**Auto-Billing Features:**
- **Notification-Triggered Payment** - payments triggered by system notifications on 25th
- **Combined Invoices** - monthly fee + additional items in single invoice
- **Malaysian Payment Methods** - FPX, e-wallets, cards via Billplz only
- **No Manual Uploads** - fully automated payment system
- **Package-Based Amounts** - RM560 full day, RM400 half day, RM1280 registration

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

3. **One-by-One Photo Attendance Flow**
   - "Select Classroom" from admin-assigned classes
   - Current day attendance for selected classroom
   - **One-by-One Process:** For each student:
     - Select student name to mark present
     - Camera interface opens automatically
     - Snap individual photo of that student
     - Save with thumbnail and present mark
   - **Absent Students:** Students not marked present (no photo needed)
   - Review all thumbnails for present students + absent list
   - "Final Save" sends all photos to API storage

#### Classroom Updates Flow (3-5 minutes)
4. **Text Classroom Updates Screen**
   - "Create Text Update" button
   - "Write Caption" text area (no photos)
   - "Tag Students" section:
     - List of student names from assigned classroom
     - Tap to select/deselect students
     - Selected students highlighted with checkmark
   - "Post Update" button (publishes immediately - no approval required)
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
   - **Attendance History:** Simple list view (no calendar)
   - **Classroom Updates:** Text-only updates tagged to this child
     - View teacher posts about this child
     - Upvote posts (no commenting allowed)
   - **Progress Reports:** Assessment results from exams
   - **Grades:** Midterm, Final assessment grades

#### Auto-Billing Notification Flow (On 25th)
3. **Auto-Billing Notification**
   - Parent receives notification on HQ configured date (25th)
   - Tap notification to view invoice details
   - Invoice displays monthly fee + any additional items in single invoice
   - **Billplz Payment Flow:**
     - "Pay" button redirects to Billplz payment portal
     - Select payment method (FPX, e-wallet, card)
     - Complete payment via Billplz gateway
     - Automatic payment confirmation and receipt
     - Return to app with payment status updated

### Message Flow - Email Style

#### Parent Messaging Branch Flow
1. **Messages Screen (Parent)**
   - "Send Message to Branch" button at top
   - **Compose Flow:**
     - "To:" field shows "Branch" (not individual teacher)
     - "Subject:" required text field
     - "Message:" text area
     - "Send to Branch" button
     - Message goes to Principal OR Admin with Message Permission

#### Branch Reply Flow
2. **Messages Screen (Branch Principal/Admin)**
   - Inbox showing parent messages with unread badges
   - **Reply Flow:**
     - Original message thread display
     - "Reply" text area at bottom
     - Subject line automatically prefixed with "Re:"
     - "Send Reply" button
     - **Thread Limit:** Maximum 3 exchanges per inquiry

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

### BrightHill Auto-Billing System
- **HQ Configurable Packages:** Full day, half day, or any programme type with HQ configurable amounts
- **Registration fee:** HQ configurable one-time payment
- **Auto-Billing:** Notifications on HQ configured date (25th), overdue on 1st of next month
- **Payment method:** Billplz integration only - FPX, e-wallets, cards
- **Additional items:** No parent approval, no spending limits
- **No manual uploads:** Fully automated payment system

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

### Auto-Notification System
- **Auto-billing notifications:** On HQ configured date (25th)
- **Payment reminders:** Automatic notifications for unpaid invoices after due date
- **Attendance alerts:** If child not marked present by 10 AM

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