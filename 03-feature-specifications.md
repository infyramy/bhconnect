# 🚀 Feature Specifications - BrightHill Connect

**Version:** 1.0  
**Last Updated:** 2025-08-21  

## 🔐 Authentication & Security

### Universal Authentication Features
| Feature | Web App | Mobile App | Description |
|---------|---------|------------|-------------|
| **Splash Screen** | ❌ | ✅ | App logo with loading animation |
| **Login** | ✅ | ✅ | Email/Username + Password |
| **Forgot Password** | ✅ | ✅ | Email-based password reset |
| **Reset Password** | ✅ | ✅ | Secure password reset flow |
| **Change Password** | ✅ | ✅ | From user profile settings |
| **Account Activation** | ✅ | ✅ | First-time setup with token |
| **Session Management** | ✅ | ✅ | Auto-logout, session expired handling |

### Security Specifications
- **Password Requirements:** Minimum 8 characters, alphanumeric + special characters
- **Session Timeout:** 2 hours of inactivity
- **Failed Login Attempts:** Account lockout after 5 failed attempts
- **Token Expiry:** Account activation tokens valid for 24 hours

---

## 👤 User Profile Management

### Profile Features
| Feature | Central Admin | Branch Principal | Configurable Admin | Teacher | Parent |
|---------|---------------|------------------|---------|---------|
| **Profile View** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Avatar Upload** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Contact Info Edit** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Notification Settings** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Language Settings** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Theme Mode** | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Role Information** | 👁 | 👁 | 👁 | 👁 | 👁 |

### Profile Data Structure
```javascript
{
  userId: "unique_id",
  role: "admin|principal|configurable_admin|teacher|parent",
  personalInfo: {
    firstName: "string",
    lastName: "string",
    email: "string",
    phone: "string",
    avatar: "image_url"
  },
  branchInfo: {
    branchId: "branch_id",
    branchName: "string"
  },
  preferences: {
    language: "en|ms",
    notifications: {
      push: boolean,
      email: boolean
    },
    theme: "light|dark"
  }
}
```

---

## 📊 Dashboard Specifications

### Central Admin Dashboard
**Platform:** Web Application

#### Main Dashboard Widgets
1. **Real-time Attendance Widget**
   - Network-wide attendance percentage
   - Today vs yesterday comparison
   - Branch-wise breakdown (top 5 performing)
   - Live updates every 15 minutes

2. **Financial Performance Widget**
   - Monthly revenue overview
   - Outstanding fees summary
   - Collection rate trends (30-day)
   - Top performing branches by revenue

3. **Student Activity Feed**
   - Recent enrollments across network
   - Student transfers between branches
   - Graduation/completion notifications
   - Real-time activity stream (last 50 items)

4. **Branch Quick Switch**
   - Dropdown/modal for branch selection
   - Search functionality for large networks
   - Favorite branches quick access
   - Branch performance indicators

#### Advanced Features
- **Detailed Attendance View:** Filterable table by branch and date range
- **Performance Analytics:** Comparative charts and trends
- **Alert System:** Notifications for issues requiring attention

### Branch Principal Dashboard
**Platform:** Web Application

#### Dashboard Components
1. **Branch Attendance Summary**
   - Today's attendance percentage
   - Class-wise breakdown
   - Absent students list with reasons
   - Weekly attendance trends

2. **Teacher Activity Overview**
   - Teachers logged in today
   - Attendance completion status
   - Recent classroom updates count
   - Teacher engagement metrics

3. **Recent Updates Feed**
   - Latest teacher posts
   - Parent messages
   - System notifications
   - Upcoming events/deadlines

4. **Fee Collection Overview**
   - Outstanding payments summary
   - Recent payments received
   - Overdue accounts requiring attention
   - Monthly collection targets

### Teacher Mobile App
**Platform:** Mobile Application (4 Bottom Tab Navigation)

#### Home Tab Features
1. **Today's Assigned Classes**
   - Admin-assigned classes only
   - Student count per class
   - Quick action shortcuts
   - Daily schedule overview

2. **Quick Actions Dashboard**
   - Attendance shortcuts
   - Recent announcements
   - Notification center
   - Activity summary

#### Classroom Tab Features
1. **Classroom Selection**
   - List of admin-assigned classrooms ONLY
   - Cannot access unassigned classrooms
   - Clear classroom identification

2. **Selected Classroom Dashboard**
   - **Summary:** Student overview, performance metrics
   - **Feed:** Text updates, student tagging, upvotes
   - **Quick Actions:** Attendance & Grade Mark buttons

3. **Attendance Quick Action**
   - Current day attendance for selected classroom
   - Present/Absent only (no Late option)
   - Past record editing requires approval

4. **Grade Mark Quick Action**
   - Exam selection (Midterm, Final, etc.)
   - Student selection from classroom
   - 5 subject areas with descriptive grading

#### Mobile-Optimized Features
- **Bottom Tab Navigation:** 4 main tabs for easy thumb access
- **Classroom-Centric:** All actions flow through classroom selection
- **Admin Restrictions:** Only assigned classrooms visible
- **Text Updates:** Simple text posting for classroom activities (no photos)
- **Student Names:** Clear display of student names for identification
- **Approval System:** Past attendance edits require admin approval
- **Offline Mode:** Basic functionality when connectivity is poor

### Parent Dashboard
**Platform:** Mobile Application

#### Dashboard Elements
1. **Child Attendance Today**
   - Check-in/out status with timestamps
   - Attendance streak indicator
   - Weekly attendance summary
   - Absence reason display

2. **Upcoming Events**
   - Next 3 events with dates
   - School calendar integration
   - Event reminder settings
   - RSVP functionality for applicable events

3. **Latest Classroom Updates**
   - Recent text classroom updates tagged to child
   - Teacher updates and announcements (text only)
   - Learning activity summaries
   - Simple upvote engagement (no comments)

#### Parent-Specific Features
- **Multiple Children:** Swipeable child cards if multiple enrolled
- **Payment Reminders:** Automated fee due notifications
- **Emergency Contacts:** Quick access to school contact information
- **Child Progress:** Weekly/monthly development summaries

---

## 📚 Student Management

### Student Record Structure
```javascript
{
  studentId: "unique_id",
  personalInfo: {
    firstName: "string",
    lastName: "string",
    dateOfBirth: "date",
    gender: "male|female",
    profilePhoto: "image_url",
    medicalInfo: {
      allergies: "string",
      medications: "string",
      emergencyContact: "string"
    }
  },
  academicInfo: {
    branchId: "string",
    classId: "string",
    enrollmentDate: "date",
    studentId: "string",
    status: "active|inactive|graduated"
  },
  parentInfo: {
    primaryParent: "parent_id",
    secondaryParent: "parent_id", // optional
    relationship: "father|mother|guardian"
  }
}
```

### Student Management Features

#### Central Admin Level
- **Network-wide Student Search:** Advanced filtering by branch, class, age, status
- **Student Transfer:** Between branches with history tracking
- **Bulk Operations:** Mass updates, imports, exports
- **Historical Records:** Complete academic journey tracking

#### Branch Principal Level
- **Student Enrollment:** Auto-generates registration + monthly invoices from enrollment month to year-end
- **Additional Items:** Add to existing invoices without parent approval, no spending limits
- **Class Assignment:** Assign students to classes
- **Admin Account Creation:** Create configurable admin accounts with page-level permissions
- **Parent Communication:** Handle parent messages or delegate to admin with Message Permission

#### Configurable Admin Level (Created by Principal)
- **Permission-Based Access:** Access based on assigned page categories
- **Student Management:** If granted - View, Add, Edit students in branch
- **Teacher Management:** If granted - View, Add, Edit teachers, assign classes
- **Parent Management:** If granted - View parent accounts, handle communications
- **Billing Access:** If granted - View invoices, add additional items
- **Message Permission:** If granted - Handle parent messages and replies
- **Reports Access:** If granted - Generate attendance, billing, performance reports

#### Teacher Level (Web & Mobile)
- **Class Student Lists:** View assigned students only (admin-assigned classes)
- **One-by-One Photo Attendance:** Mandatory photos for present students, no alternatives
- **Attendance Restrictions:** Edit past records requires admin approval
- **Text Classroom Updates:** Post text updates with student tagging (no approval required)
- **Parent Communication:** Reply only (cannot initiate), messages handled by branch

### One-by-One Photo Attendance System
#### Photo Requirements
- **Photo Mandatory:** Required for all present students
- **No Backup Methods:** Clear photo required, no alternatives
- **One-by-One Process:** Select present → snap photo → save with thumbnail
- **Mandatory for Present Students Only:** Absent students do not require photos

#### Photo Storage & Management
- **Backend Storage:** All photos uploaded to secure cloud storage
- **Administrative Access:** Photos available for admin review
- **Privacy Compliance:** Secure storage with access controls
- **Retention Policy:** Photos retained for academic record purposes
- **API Integration:** Photos submitted via dedicated upload API

#### Photo Attendance Workflow
1. **Teacher opens attendance screen**
2. **Camera interface activated automatically**
3. **Teacher takes photo of each student individually**
4. **Mark attendance status (Present/Absent) with photo**
5. **Submit attendance with all photos**
6. **Photos uploaded to backend storage**
7. **Confirmation of successful submission**

#### Parent Level
- **Child Profile View:** View child's information and progress
- **Attendance History:** Simple list view of attendance records
- **Academic Progress:** Grades, assessments, and development milestones
- **Child-Specific Updates:** Text classroom posts tagged to their child only
- **Communication:** Send messages to branch only (Principal/Admin with Message Permission replies)
- **Billing Notifications:** Receive auto-notifications on 25th, pay via Billplz

---

## 👨‍🏫 Teacher Management

### Teacher Profile Structure
```javascript
{
  teacherId: "unique_id",
  personalInfo: {
    firstName: "string",
    lastName: "string",
    email: "string",
    phone: "string",
    qualifications: "string",
    experience: "number"
  },
  employmentInfo: {
    branchId: "string",
    employeeId: "string",
    hireDate: "date",
    status: "active|inactive",
    subjects: ["array_of_subjects"],
    classesAssigned: ["array_of_class_ids"]
  },
  performance: {
    attendanceRate: "percentage",
    parentRatings: "average_rating",
    studentEngagement: "metrics"
  }
}
```

### Teacher Management Features

#### Central Admin Level
- **Network Teacher Directory:** All teachers across branches
- **Performance Analytics:** Teacher effectiveness metrics
- **Resource Allocation:** Optimal teacher-to-student ratios
- **Professional Development:** Training and certification tracking

#### Branch Principal Level
- **Teacher Onboarding:** New teacher registration and setup
- **Class Assignment:** Assign teachers to classes and subjects
- **Performance Monitoring:** Track teacher activity and engagement
- **Schedule Management:** Teaching schedules and substitute arrangements

---

## 📢 Communication System

### Message Types
1. **Direct Messages:** One-on-one conversations
2. **Broadcast Messages:** One-to-many communications
3. **Announcements:** Official school communications
4. **Emergency Alerts:** Urgent notifications with high priority

### Communication Features

#### Parent-Branch Communication (Updated Flow)
- **Parent Messages:** Parents can only message branch (not individual teachers)
- **Message Handling:** Branch Principal OR Admin with Message Permission handles replies
- **Message Threading:** Maximum 3 exchanges per inquiry
- **Email-Style Structure:** Subject lines required, no real-time chat
- **Pull-to-Refresh:** Manual refresh, no WebSocket complexity

#### Teacher Communication
- **Classroom Feed:** Text-only updates with student tagging (no approval required)
- **Parent Reply:** Teachers can only reply to parent messages (cannot initiate)
- **Branch Communication:** Two-way messaging with Principal/Admin
- **Child-Specific Posts:** Parents see only posts tagged with their child

#### Announcement System
- **HQ Announcements:** Target All Network, All Teachers, All Parents, or Specific Branch
- **Branch Announcements:** Target All Branch Users, Branch Teachers, or Branch Parents
- **Push Notifications:** Real-time delivery to mobile apps
- **Announcement History:** Track sent announcements and read receipts

#### Notification System
- **Push Notifications:** Real-time mobile alerts
- **Basic Notifications:** Simple notification system only
- **In-App Notifications:** System and user notifications
- **Notification Preferences:** User-configurable notification settings

---

## 💰 Auto-Billing & Billplz Payment System

### Billing & Invoice Features
| Feature | Central Admin | Branch Principal | Configurable Admin | Teachers | Parent |
|---------|---------------|------------------|-------------------|----------|--------|
| **View All Payments** | ✅ Network | ✅ Branch | 👁 Branch (if Billing Access) | ❌ | 👁 Own |
| **Create Student Bills** | ✅ | ✅ | ✅ (if Billing Access) | ❌ | ❌ |
| **Auto-Invoice Generation** | ✅ Config | ✅ Trigger | ✅ (if Billing Access) | ❌ | ❌ |
| **Additional Items** | ✅ | ✅ | ✅ (if Billing Access) | ❌ | ❌ |
| **Billplz Payment** | ❌ | ❌ | ❌ | ❌ | ✅ Execute |
| **Invoice Notifications** | 👁 All | 👁 Branch | 👁 Branch | ❌ | ✅ Receive |
| **Payment Reports** | ✅ Network + Audit | ✅ Branch | 👁 Branch (if Reports Access) | ❌ | 👁 Own |

### Fixed Fee Structure
```javascript
// Fixed Fee Amounts (HQ Configurable)
{
  tuition_full_day: { amount: 560.00, frequency: "monthly" },
  tuition_half_day: { amount: 400.00, frequency: "monthly" },
  registration: { amount: 1280.00, frequency: "one_time" },
  additional_items: { variable_amount: true, frequency: "as_needed" }
}
```

### Auto-Billing System Implementation
1. **HQ Configurable Packages**
   - All programme types (Full Day, Half Day, etc.) with configurable amounts
   - HQ sets notification date (25th) and due dates (1st)
   
2. **Auto-Invoice Generation**
   - Enrollment generates registration + monthly invoices from enrollment month to year-end
   - Additional items added without parent approval, no spending limits
   
3. **Auto-Notifications**
   - System sends notifications to parents for unpaid invoices after due date
   - All billing activities logged for HQ review

### Billplz Payment Integration
- **Malaysian Payment Methods:** FPX, e-wallets, cards via Billplz
- **Immediate Processing:** No manual verification required
- **Payment Confirmation:** Real-time status updates from Billplz
- **Receipt Generation:** Billplz provides automatic payment receipts
- **Status Tracking:** Automatic payment status monitoring

### Financial Reporting
- **Revenue Analytics:** Branch and network-wide revenue tracking
- **Collection Rates:** Payment efficiency metrics with auto-billing insights
- **Outstanding Balances:** Automated overdue accounts management
- **Financial Forecasting:** Revenue projections based on enrollment and auto-billing patterns

---

## 📅 Calendar & Events

### Event Management
```javascript
{
  eventId: "unique_id",
  eventInfo: {
    title: "string",
    description: "string",
    type: "holiday|activity|meeting|parent_day",
    date: "date",
    startTime: "time",
    endTime: "time",
    location: "string"
  },
  targeting: {
    audience: "all|branch|class|parents",
    branchIds: ["array"],
    classIds: ["array"]
  },
  metadata: {
    createdBy: "user_id",
    rsvpRequired: boolean,
    maxAttendees: number,
    attachments: ["file_urls"]
  }
}
```

### Calendar Features
- **Multi-View Calendar:** Month, week, day views
- **Event Categories:** Color-coded event types
- **RSVP Management:** Event registration and capacity control
- **Reminder System:** Automated event reminders
- **Recurring Events:** Weekly/monthly recurring events
- **Event Sync:** Integration with device calendars

---

## 📝 Simple Exam & Assessment System

### Configurable Exam Structure
```javascript
// Default Exam Types (Configurable)
{
  midYear: {
    name: "Mid-Year Assessment",
    frequency: "semester",
    weight: 40,
    subjects: ["literacy", "numeracy", "social", "motor", "creative"]
  },
  finalYear: {
    name: "Final Assessment", 
    frequency: "yearly",
    weight: 60,
    subjects: ["literacy", "numeracy", "social", "motor", "creative"]
  }
}
```

### Simple Grading System
- **Descriptive Grading:** Excellent → Good → Satisfactory → Needs Support
- **Optional Numeric:** A/B/C/D grades with percentage ranges
- **Subject Areas:** Literacy, Numeracy, Social Skills, Motor Skills, Creative
- **Teacher Comments:** Optional remarks for each subject
- **Progress Comparison:** Compare mid-year vs final results

### Assessment Features
- **Easy Marking Interface:** Teacher-friendly with student names
- **Batch Processing:** Mark entire class efficiently
- **Progress Tracking:** Visual progress indicators
- **Parent Reports:** Clear, visual assessment reports
- **Configurable Subjects:** Add/remove subjects per age group

---

## 🔔 Automated Reminder System

### Child-Specific Reminders
- **Fee Reminders:** 7 days, 3 days, 1 day before due date
- **Overdue Notices:** 1 day, 7 days after due date
- **Exam Notifications:** 2 weeks and 3 days before assessments
- **Absence Check:** If no attendance recorded by 10 AM
- **Custom Templates:** Personalized message templates

### Reminder Configuration
```javascript
// Configurable Reminder Schedule
{
  feeReminders: {
    schedule: [-7, -3, -1, +1, +7], // days relative to due date
    templates: "customizable_per_branch"
  },
  absenceCheck: {
    trigger: "10:00_AM",
    condition: "no_attendance_recorded"
  }
}
```

---

## 📊 Reports & Analytics

### Report Categories

#### Attendance Reports
- **Daily Attendance:** Branch and class-level attendance
- **Attendance Trends:** Historical patterns and insights
- **Absent Student Reports:** Detailed absence tracking
- **Teacher Attendance:** Staff attendance monitoring

#### Academic Reports
- **Student Progress:** Individual assessment results
- **Class Performance:** Overall class assessment summaries
- **Progress Comparison:** Mid-year vs final assessment trends
- **Parent Engagement:** Communication and participation metrics

#### Financial Reports
- **Revenue Reports:** Monthly and annual revenue analysis
- **Payment Collection:** Collection efficiency and trends
- **Outstanding Fees:** Overdue accounts and follow-up actions
- **Budget Analysis:** Expense vs revenue comparisons

#### Operational Reports
- **User Activity:** System usage and engagement metrics
- **Branch Performance:** Comparative branch analysis
- **Teacher Performance:** Teaching effectiveness metrics
- **Parent Satisfaction:** Feedback and rating reports

### Export Options
- **PDF Reports:** Formatted reports for printing and sharing
- **Excel Export:** Data export for further analysis
- **CSV Export:** Raw data for custom reporting
- **Email Reports:** Automated report delivery

---

## 🔧 Technical Specifications

### Performance Requirements
- **Page Load Time:** < 3 seconds for web, < 2 seconds for mobile
- **API Response Time:** < 500ms for standard operations
- **Receipt Upload:** < 30 seconds for payment receipts
- **Offline Functionality:** Basic read operations available offline

### Browser/Device Support
- **Web Browsers:** Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **Mobile Devices:** iOS 12+, Android 8+
- **Tablet Support:** Optimized for 10-12 inch tablets
- **Responsive Design:** Adapts to screen sizes 320px - 2560px

### Integration Requirements
- **Payment Gateways:** FPX, Stripe, PayPal
- **Notification Services:** Firebase Cloud Messaging, Apple Push Notifications
- **File Storage:** Cloud storage for media files and documents
- **Email Services:** SMTP integration for email notifications

---

**Next Steps:** 
1. Validate feature priorities with BrightHill stakeholders
2. Create detailed wireframes for each feature
3. Define API endpoints and data models
4. Establish development timeline and milestones