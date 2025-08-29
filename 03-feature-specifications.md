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
| Feature | Central Admin | Branch Principal | Teacher | Parent |
|---------|---------------|------------------|---------|---------|
| **Profile View** | ✅ | ✅ | ✅ | ✅ |
| **Avatar Upload** | ✅ | ✅ | ✅ | ✅ |
| **Contact Info Edit** | ✅ | ✅ | ✅ | ✅ |
| **Notification Settings** | ✅ | ✅ | ✅ | ✅ |
| **Language Settings** | ✅ | ✅ | ✅ | ✅ |
| **Theme Mode** | ❌ | ❌ | ❌ | ❌ |
| **Role Information** | 👁 | 👁 | 👁 | 👁 |

### Profile Data Structure
```javascript
{
  userId: "unique_id",
  role: "admin|principal|teacher|parent",
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
- **Student Registration:** New student enrollment with parent account creation
- **Class Assignment:** Assign/reassign students to appropriate classes
- **Student Profiles:** Detailed view with academic and personal information
- **Parent Linking:** Generate and manage parent access tokens

#### Teacher Level (Web & Mobile)
- **Class Student Lists:** View assigned students with names (no photos)
- **Photo Attendance System:** Mark attendance with mandatory student photos
- **Attendance Tracking:** Mark present/absent with photo verification
- **Progress Notes:** Add observations and developmental notes
- **Parent Communication:** Direct messaging about student progress

### Photo Attendance System
#### Photo Capture Requirements
- **Individual Student Photos:** One photo per student during attendance
- **Clear Face Visibility:** Ensure student face is clearly visible
- **Photo Quality Standards:** Minimum resolution for identification
- **Failed Upload Retry:** Re-take photos if upload fails
- **Mandatory Requirement:** Cannot save attendance without photos

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
- **Child Profile View:** Comprehensive view of child's information (no photos)
- **Attendance History:** Historical attendance records with patterns
- **Academic Progress:** Grades, assessments, and development milestones
- **Tagged Updates:** Text classroom posts tagged to their child

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

#### Email-Style Messaging (No WebSocket)
- **Professional Structure:** Subject lines, threading, folders (Inbox/Sent/Important)
- **Pull-to-Refresh:** Manual refresh instead of real-time updates
- **Thread Management:** Group related messages together
- **Attachment Support:** Photos, documents, voice notes
- **Read Receipts:** Know when messages are opened
- **Search Function:** Find messages by sender, subject, or content

#### Child-Specific Feed System
- **Tagged Posts Only:** Parents see only posts tagged with their child
- **Teacher Posting:** Must tag specific students in classroom updates
- **No Class-Wide Posts:** All posts are child-specific
- **Media-Rich:** Encourage photos/videos of daily activities
- **Personal Touch:** Each update feels personal to the parent

#### Announcement System
- **Target Audience Selection:** All users, specific branches, classes, or roles
- **Rich Content:** Text, images, videos, documents
- **Schedule Publishing:** Immediate or scheduled announcements
- **Read Receipts:** Track who has viewed announcements

#### Notification System
- **Push Notifications:** Real-time mobile alerts
- **Basic Notifications:** Simple notification system only
- **In-App Notifications:** System and user notifications
- **Notification Preferences:** User-configurable notification settings

---

## 💰 Manual Billing & Billplz Payment System

### Payment Features
| Feature | Central Admin | Branch Principal | Financial Staff | Teachers (Web) | Teacher (Mobile) | Parent |
|---------|---------------|------------------|-----------------|----------------|------------------|---------|
| **View All Payments** | ✅ Network | ✅ Branch | ✅ Branch | ❌ | ❌ | 👁 Own |
| **Create Student Bills** | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Manual Invoice Generation** | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Billplz Payment Processing** | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ |
| **Upload Payment Proof** | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| **Approve Payment Proof** | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Payment Reports** | ✅ Network | ✅ Branch | ✅ Branch | ❌ | ❌ | 👁 Own |

### Fixed Fee Structure
```javascript
// Fixed Fee Amounts (No Configuration)
{
  tuition: { amount: 560.00, frequency: "monthly" },
  registration: { amount: 1280.00, frequency: "one_time" },
  activities: { amount: 50.00, frequency: "optional" },
  meals: { amount: "included_in_tuition" }
}
```

### Manual Billing & Billplz Payment Flow
1. **Manual Bill Creation System**
   - **Financial Staff/Principal:** Manually create student bills
   - **Select Student:** Choose individual student for billing
   - **Add Line Items:** Fixed amounts - RM560 tuition, RM1280 registration
   - **Generate Invoice:** Manually create invoice
   - **Parent Notification:** Send notification to mobile app

2. **Billplz Payment Integration**
   - **Mobile App Integration:** Parents redirected to Billplz
   - **Malaysian Payment Methods:** FPX, e-wallets, cards via Billplz
   - **Backend Integration:** Mobile → Backend → Billplz
   - **Payment Confirmation:** Return from Billplz with status
   - **Receipt Generation:** Billplz provides payment receipts

3. **Dual Payment Options**
   - **Billplz Online:** Secure payment via Billplz gateway
   - **Manual Upload:** Bank transfer/cash with uploaded proof
   - **Staff Verification:** Manual approval of payment proofs
   - **Status Tracking:** Manual payment status monitoring

4. **Manual Payment Tracking**
   - **Manual Updates:** Staff manually update payment status
   - **Proof Verification:** Staff approval for uploaded receipts
   - **Payment History:** Transaction records maintained
   - **No Automated Flow:** All processes require manual intervention

### Financial Reporting
- **Revenue Analytics:** Branch and network-wide revenue tracking
- **Collection Rates:** Payment efficiency metrics
- **Outstanding Balances:** Overdue accounts management
- **Financial Forecasting:** Revenue projections based on enrollment

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