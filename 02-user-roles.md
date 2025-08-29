# 👥 User Roles & Permissions - BrightHill Connect

**Version:** 2.0  
**Last Updated:** 2025-08-26  
**Updated:** Added Financial Staff and Teachers roles, Payment Gateway features  

## 🏛 1. Central Admin (HQ Management)

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for monitoring
- **Access Level:** Network-wide across all branches

### Core Responsibilities
- Strategic oversight of entire BrightHill network
- Branch performance monitoring and analytics
- System configuration and user management
- Financial oversight and reporting
- Branding consistency maintenance

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Branch Management** | Full CRUD | Create, edit, delete branches |
| **User Management** | Full CRUD | Manage all user roles across network |
| **Financial Oversight** | Read/Report | View all branch finances, generate reports |
| **System Settings** | Full Control | Branding, app configuration, role permissions |
| **Analytics** | Full Access | Network-wide performance metrics |

### Dashboard Features
- **Real-time Attendance Widget** - Live attendance across all branches
- **Financial Performance Overview** - Revenue, collection rates, outstanding fees
- **Network Activity Feed** - Recent activities across all branches
- **Branch Performance Comparison** - Comparative analytics between branches
- **User Activity Monitoring** - System usage and engagement metrics

---

## 💰 2. Financial Staff (Branch Level)

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for notifications
- **Access Level:** Single branch financial operations only

### Core Responsibilities
- Monthly billing and invoice creation for students
- Payment tracking and collection management
- Parent payment verification and approval
- Financial reporting for branch operations
- Outstanding fees follow-up and management

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Student Billing** | Full CRUD | Create monthly bills, manage invoices |
| **Payment Processing** | Create/Approve | Generate bills, verify payments |
| **Financial Reports** | Read/Generate | Branch revenue, collection rates |
| **Invoice Management** | Full CRUD | Create, edit, track student invoices |
| **Payment Gateway** | Execute/Monitor | Process payments, track transactions |

### Bill Creation Workflow
1. **Monthly Billing Process**
   - Staff go to billing system
   - Select students for monthly charges
   - Enter billing items (tuition, meals, activities) and amounts
   - Generate invoices automatically
   - Parents receive notifications on mobile app

2. **Payment Tracking**
   - Monitor incoming payments (gateway/manual)
   - Verify uploaded payment receipts
   - Update payment status (paid/pending/overdue)
   - Generate payment confirmations

### Dashboard Features
- **Outstanding Bills Overview** - Unpaid invoices by student
- **Payment Collection Summary** - Daily/monthly collection rates
- **Revenue Analytics** - Income trends and financial forecasting
- **Parent Payment Activity** - Recent payments and pending bills
- **Financial Alerts** - Overdue payments requiring follow-up

### Access Restrictions
- **Branch Limitation:** Only assigned branch financial data
- **Financial Focus:** Cannot modify academic or attendance records
- **No User Management:** Cannot create/modify user accounts
- **Payment Categories Only:** Limited to billing and payment functions

---

## 👩‍🏫 3. Teachers Role (Web Admin) - Similar to Principal but Limited

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
- **Assigned Classes Overview** - Current class assignments and student counts
- **Photo Attendance Summary** - Daily attendance with photo requirements  
- **Today's Summary** - Key metrics and alerts for assigned classes

### Access Restrictions
- **Class Limitation:** Only assigned classes visible (not all branch classes)
- **No Financial Access:** Cannot create bills or manage payments
- **No User Management:** Cannot manage other teachers or staff
- **No Branch Settings:** Cannot modify branch-level configurations
- **Student Scope:** Limited to students in assigned classes only

---

## 🏫 4. Branch Principal

### Platform Access
- **Primary:** Web Application (Vue/Nuxt)
- **Secondary:** Mobile app for remote access
- **Access Level:** Single branch with full operational control

### Core Responsibilities
- Daily branch operations management
- Student enrollment and record keeping
- Teacher recruitment and management
- Parent communication and relationship building
- Local financial management (fee collection)

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Student Management** | Full CRUD | Branch students only |
| **Teacher Management** | Full CRUD | Branch teachers only |
| **Class Organization** | Full CRUD | Class creation and student assignment |
| **Communications** | Create/Edit | Announcements, parent messaging |
| **Financial Tracking** | Read/Report | Branch fee collection and invoicing |

### Registration Workflow
1. **Student Registration**
   - Register parent account
   - Add child/student details
   - Generate parent access token/code
   - Parent uses token to activate mobile app
   - Automatic child-parent linking in system

### Dashboard Features
- **Branch Attendance Summary** - Daily attendance overview
- **Teacher Activity Overview** - Teacher engagement and productivity
- **Fee Collection Status** - Outstanding payments and collection rates
- **Recent Updates Feed** - Latest activities and communications
- **Class Management Panel** - Quick access to class operations

---

## 👩‍🏫 5. Teacher (Mobile App)

### Platform Access
- **Primary:** Mobile Application (React Native)
- **Secondary:** Tablet-optimized interface
- **Access Level:** Assigned classes and students only

### Core Responsibilities
- Daily attendance marking
- Classroom updates and activity sharing
- Student progress tracking
- Parent communication
- Educational content sharing

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Attendance** | Create/Edit | Mark attendance for assigned classes |
| **Student Updates** | Create/Edit/Delete | Post classroom activities with media |
| **Progress Tracking** | Create/Edit | Enter mid-term and final marks |
| **Communication** | Create/Reply | Message parents and principals |
| **Media Sharing** | Upload/Tag | Text updates with student tagging |

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
- **Home Tab** - Today's assigned classes overview
- **Classroom Tab** - Select assigned classroom → Summary/Feed/Quick Actions
- **Messages Tab** - Communication with parents and principal
- **Profile Tab** - Account settings and information

### Key Teacher Restrictions
- **Classroom Access:** Only admin-assigned classrooms visible
- **Attendance Options:** Present/Absent with mandatory photo capture
- **Photo Requirements:** Must snap individual student photos during attendance
- **Edit Approval:** Past attendance changes require admin approval
- **Grade Linking:** All assessments tied to specific exam types
- **Photo Storage:** All photos submitted to backend storage API

---

## 👨‍👩‍👧‍👦 6. Parent

### Platform Access
- **Primary:** Mobile Application (React Native)
- **Access Level:** Own children only
- **Account Setup:** Token-based activation after child registration

### Core Responsibilities
- Monitor child's attendance and progress
- Communication with teachers and school
- Fee payments and financial management
- Event and announcement awareness
- Profile maintenance

### Key Permissions
| Feature Category | Permissions | Details |
|------------------|-------------|---------|
| **Child Monitoring** | Read-Only | View child's attendance, progress, activities |
| **Communication** | Create/Reply | Message teachers and school administration |
| **Payments** | Execute/View | Make payments, view payment history |
| **Media Access** | View/Download | Child-tagged classroom updates |
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

### Dashboard Features
- **Child Attendance Status** - Today's attendance and weekly summary
- **Latest Updates** - Recent text classroom activities
- **Upcoming Events** - School calendar and important dates
- **Payment Center** - Bills, payment gateway, transaction history
- **Communication Center** - Messages from teachers and school
- **Bill Management** - View invoices, pay via payment gateway

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

| Feature | Central Admin | Branch Principal | Financial Staff | Teachers (Web) | Teacher (Mobile) | Parent |
|---------|---------------|------------------|-----------------|----------------|------------------|---------|
| Branch Management | ✅ Full | ❌ None | ❌ None | ❌ None | ❌ None | ❌ None |
| Student Records | ✅ All Branches | ✅ Own Branch | ❌ None | ✅ Assigned Classes | 👁 Assigned Classes | 👁 Own Children |
| Teacher Management | ✅ All Branches | ✅ Own Branch | ❌ None | ❌ None | ❌ None | ❌ None |
| Attendance | 👁 All | 👁 Branch | ❌ None | ✅ Classes + Photos | ✅ Classes + Photos | 👁 Child |
| Communications | ✅ All | ✅ Branch | ❌ None | ✅ Parents/Principal | ✅ Parents/Principal | ✅ Teachers/School |
| Financial Data | 👁 All | 👁 Branch | ✅ Branch Financial | ❌ None | ❌ None | ✅ Own Payments |
| Bill Creation | ❌ None | ✅ Branch | ✅ Branch | ❌ None | ❌ None | ❌ None |
| Payment Gateway | ❌ None | ✅ Branch | ✅ Branch | ❌ None | ❌ None | ✅ Own Payments |
| Reports & Analytics | ✅ Network-wide | ✅ Branch-level | ✅ Financial Reports | 👁 Class-level | 👁 Class-level | 👁 Child-level |

**Legend:**
- ✅ Full CRUD (Create, Read, Update, Delete)
- 👁 Read-Only Access
- ❌ No Access

---

**Next Review:** User role validation with BrightHill stakeholders  
**Implementation Notes:** Role permissions to be enforced at API level with frontend validation