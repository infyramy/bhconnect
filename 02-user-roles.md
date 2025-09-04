# 👥 User Roles & Permissions - BrightHill Connect

**Auto-Billing System, Configurable Admin Accounts, One-by-One Photo Attendance**  

## 🏛 1. Central Admin (HQ Management)

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for monitoring
- **Access Level:** Network-wide across all branches

### Core Responsibilities
- Create branches (auto-generates Principal accounts)
- Network-wide user management and analytics
- HQ configurable packages and billing configuration
- Network-wide announcements (All Network, All Teachers, All Parents, Specific Branch)
- System oversight and audit logs review

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Branch Management** | Full CRUD | Create, edit, delete branches |
| **User Management** | Full CRUD | Manage all user roles across network |
| **Financial Oversight** | Read/Report | View all branch finances, generate reports |
| **System Settings** | Full Control | Branding, app configuration, role permissions |
| **Analytics** | Full Access | Network-wide performance metrics |

### Key Features
- **Branch Creation** - Auto-generates Principal account for each new branch
- **HQ Configurable Packages** - Set programme types with configurable amounts
- **Billing Configuration** - Configure notification (25th) and due dates (1st)
- **Network Announcements** - Target all network, teachers, parents, or specific branches
- **Principal Assignment** - Reassign principal role to different admin accounts

---


## 👩‍🏫 2. Teachers Role (Web Admin) - Similar to Principal but Limited

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for basic functions
- **Access Level:** Assigned classes and students only

### Core Responsibilities
- Student management for assigned classes (similar to Principal)
- Attendance management with photo verification (same as Principal)
- Academic assessment and grading (same as Principal)
- Parent messaging and communication (same as Principal)
- Limited to assigned classes only

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Student Records** | Read/Edit | View and update assigned students only (like Principal) |
| **Attendance Management** | Full CRUD | Same attendance features as Principal |
| **Academic Assessment** | Create/Edit | Same grading system as Principal |
| **Parent Communication** | Create/Reply | Same messaging system as Principal |
| **Financial Functions** | ❌ None | Cannot access billing or payment features |

### Features Same as Principal
- **Attendance Management:** Mark attendance, photo capture, edit approval
- **Academic Assessment:** Grade entry, progress reports, assessment history
- **Messages:** Parent communication, message history, announcements
- **Dashboard:** Class overview, attendance summary, today's alerts

### Dashboard Features (Same as Principal)
- **Assigned Classes Overview** - Current class assignments and student counts (cards: view-only class info with student counts)
- **Photo Attendance Summary** - Daily attendance with photo requirements (alerts: pending attendance, grade submissions)
- **Today's Summary** - Key metrics and alerts for assigned classes (buttons: rapid attendance, grade entry shortcuts)
- **Recent Activity** - Feed of recent posts, messages, notifications

### Access Restrictions
- **Class Limitation:** Only assigned classes visible (not all branch classes)
- **No Financial Access:** Cannot create bills or manage payments
- **No User Management:** Cannot manage other teachers or staff
- **No Branch Settings:** Cannot modify branch-level configurations
- **Student Scope:** Limited to students in assigned classes only

---

## 🏫 3. Branch Principal

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for remote access
- **Access Level:** Single branch with full operational control

### Core Responsibilities
- Student enrollment (auto-generates Registration + Monthly invoices from enrollment to year-end)
- Teacher and class management
- Create configurable admin accounts with page-level permissions
- Handle parent messages (or delegate to admin with Message Permission)
- Branch-specific announcements to teachers/parents

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Student Management** | Full CRUD | Branch students only |
| **Teacher Management** | Full CRUD | Branch teachers only |
| **Class Organization** | Full CRUD | Class creation and student assignment |
| **Communications** | Create/Edit | Announcements, parent messaging |
| **Billing & Invoices** | Create/Manage | Student billing, add additional items (no parent approval) |
| **Admin Account Creation** | Full CRUD | Create admin accounts with granular page permissions |
| **Parent Messages** | Handle/Reply | Receive and respond to parent messages |
| **Branch Announcements** | Create/Send | Target branch users, teachers, or parents |

### Student Enrollment Flow
1. **Student Registration** (Principal/Admin with Student Management Access)
   - Add student details and select package type
   - System auto-generates: Registration fee + monthly invoices from enrollment month to year-end
   - Parent receives access code via SMS/Email
   - Parent sets up mobile account with automatic child linking

### Key Features
- **Student Management** - Add students with auto-invoice generation (Registration + Monthly from enrollment to year-end)
- **Admin Account Creation** - Create admin accounts with granular page permissions (Student, Teacher, Parent, Billing, Reports, Message Permission)
- **Billing & Invoices** - Add additional items to invoices (no parent approval, no spending limits)
- **Parent Communication** - Handle parent messages or delegate to admin with Message Permission
- **Branch Announcements** - Send targeted announcements to branch teachers/parents

---

## 👩‍🏫 4. Teacher (Mobile App)

### Platform Access
- **Primary:** Mobile Application (React Native)
- **Secondary:** Tablet-optimized interface
- **Access Level:** Assigned classes and students only

### Core Responsibilities
- One-by-one photo attendance (mandatory for present students)
- Text classroom updates with student tagging
- Student progress tracking and grading
- Reply to parent messages (no initiation)
- Branch communication with principal/admin

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Attendance** | Create/Edit | Mark attendance for assigned classes |
| **Student Updates** | Create/Edit/Delete | Post text classroom activities (no photos) |
| **Progress Tracking** | Create/Edit | Enter exam-tied grades (Midterm, Final, Assessment) |
| **Communication** | Reply Only | Reply to parent messages, two-way with principal/admin |
| **Text Posting** | Upload/Tag | Text updates with student tagging (no approval required) |

### Daily Workflow
1. **Morning Setup (Home Tab)**
   - View today's assigned classes
   - Quick action shortcuts
   - Check recent notifications

2. **Class Activities (Classroom Tab)**
   - Select assigned classroom
   - Quick Action: Attendance (Present/Absent marking)
   - Feed: Post text updates with student tagging
   - View classroom summary and metrics

3. **Assessment Management (Classroom Quick Actions)**
   - Quick Action: Grade Mark
   - Select exam type (Midterm, Final, etc.)
   - Choose student and enter grades
   - Save grades tied to exam and student

### Mobile Features (4 Bottom Tab Navigation)
- **Home Tab** `/home` - Today's assigned classes overview (dashboard screen with cards)
- **Classroom Tab** `/classroom` - Select assigned classroom → Summary/Feed/Quick Actions (multi-screen flow with floating action buttons)
- **Messages Tab** `/messages` - Communication with parents and principal (chat interface with tabbed message center)
- **Profile Tab** `/profile` - Account settings and information (settings screen)

### Key Teacher Restrictions
- **Classroom Access:** Only admin-assigned classrooms visible
- **Attendance Options:** Present/Absent with mandatory photo capture
- **Photo Requirements:** Must snap individual student photos during attendance
- **Edit Approval:** Past attendance changes require admin approval
- **Grade Linking:** All assessments tied to specific exam types
- **Photo Storage:** All photos submitted to backend storage API

---

## 👨‍👩‍👧‍👦 5. Parent

### Platform Access
- **Primary:** Mobile Application (React Native)
- **Access Level:** Own children only
- **Account Setup:** Token-based activation after child registration

### Core Responsibilities
- Monitor child's attendance and progress
- Communication with branch (Principal/Admin with Message Permission)
- Billing notifications (25th) and Billplz payments
- View child-specific classroom updates
- Profile and linked children management

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Child Monitoring** | Read-Only | View child's attendance, progress, activities |
| **Communication** | Create/Reply | Message branch only (Principal/Admin replies, max 3 exchanges) |
| **Payments** | Execute/View | Billplz payments, auto-notifications, payment history |
| **Child Updates** | View/Upvote | Child-tagged text updates (no commenting) |
| **Profile Management** | Edit | Update personal and child information |

### Account Activation Process
1. **Initial Registration** (Done by Principal/Admin)
   - Parent details entered
   - Child information added
   - Unique access token generated

2. **Parent Activation**
   - Parent receives invitation (SMS/Email)
   - Downloads mobile app
   - Enters token to activate account
   - Sets up password and profile
   - Automatically sees linked children

### Dashboard Features (`/dashboard` - Card-Based Dashboard)
- **Child Overview** - Swipeable cards for multiple children with attendance status, latest updates, child info
- **Notifications Center** - Billing, announcements, messages with badges
- **Payment Reminders** - Due dates, overdue alerts with amounts
- **Announcements Card** - Principal/HQ announcements

---

## 🔐 Security & Access Control

### Authentication Levels
- **Multi-Factor Authentication** for Admin and Principal roles
- **Token-Based Activation** for parent accounts
- **Session Management** with automatic timeout
- **Role-Based Permissions** with strict access controls

### Data Privacy
- **Parent Access** limited to own children only
- **Teacher Access** limited to assigned classes
- **Branch Isolation** for principals (cannot access other branches)
- **Audit Trail** for all user activities and data changes

### Account Management
- **Deactivation Process** for departed users
- **Role Transition** procedures (e.g., teacher to principal)
- **Emergency Access** protocols for critical situations
- **Data Retention** policies for inactive accounts

---

## 📊 Permission Matrix Summary

| Feature | Central Admin | Branch Principal | Teachers (Web) | Teacher (Mobile) | Parent |
|---------|---------------|------------------|----------------|------------------|---------|
| Branch Management | ✅ Create + Auto-Principal | ❌ None | ❌ None | ❌ None | ❌ None |
| Student Records | ✅ All Branches | ✅ Own Branch | ✅ Assigned Classes | 👁 Assigned Classes | 👁 Own Children |
| Teacher Management | ✅ All Branches | ✅ Own Branch | ❌ None | ❌ None | ❌ None |
| Attendance | 👁 All | 👁 Branch | ✅ One-by-One Photos | ✅ One-by-One Photos | 👁 Child |
| Communications | ✅ Network Announcements | ✅ Branch Announcements | ✅ Reply to Parents | ✅ Reply to Parents | ✅ Message Branch Only |
| Billing & Invoices | 👁 All + Config | ✅ Branch + Additional Items | ❌ None | ❌ None | 👁 Own + Billplz |
| Admin Account Creation | ✅ Network-wide | ✅ Branch + Permissions | ❌ None | ❌ None | ❌ None |
| Message Permission | ✅ All | ✅ Handle Parents | ❌ None | ❌ None | ✅ Send to Branch |
| Reports & Analytics | ✅ Network-wide + Audit | ✅ Branch-level | 👁 Class-level | 👁 Class-level | 👁 Child-level |

**Legend:**
- ✅ Full CRUD (Create, Read, Update, Delete)
- 👁 Read-Only Access
- ❌ No Access

---

## 🔧 New Admin Account System

### Configurable Admin Permissions (Created by Branch Principal)
| Page Category | Permission Levels | Description |
|---------------|------------------|-------------|
| **Student Management** | View, Add, Edit | Access to student records and enrollment |
| **Teacher Management** | View, Add, Edit, Assign Classes | Teacher accounts and class assignments |
| **Parent Management** | View, Communication | Parent accounts and message handling |
| **Billing Access** | View Invoices, Add Additional Items | Invoice management (no parent approval) |
| **Reports Access** | Attendance, Billing, Performance | Various report generation |
| **Message Permission** | Handle Parent Messages | Can receive and reply to parent messages |

### Admin Account Rules
- **Created by:** Branch Principal only
- **Scope:** Branch-specific (cannot access other branches)
- **Granular:** Page-category level permissions
- **Message Handling:** Parent messages go to Principal OR Admin with Message Permission
- **Flexibility:** Principal can create specialized roles (e.g., Billing Admin, Student Admin, etc.)

---

**Implementation Notes:** 
- Role permissions enforced at API level with frontend validation
- Admin accounts inherit branch restrictions
- Message Permission required for parent communication handling
- HQ auto-creates Principal accounts when creating branches