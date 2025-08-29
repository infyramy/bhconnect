# 💼 Business Logic - BrightHill Connect

**Purpose:** Simple business rules for development team  
**Goal:** Clear requirements that are easy to implement  
**Keep it Simple:** Avoid complex features, focus on essential needs

---

## 💰 Simple Fee Structure

### Monthly Fees (Keep it Simple)
- **Monthly Fee:** RM560 per student (includes tuition and meals)
- **Registration Fee:** RM1280 one-time payment for new students
- **Due Date:** 5th of every month
- **Late Fee:** RM10 after 7 days grace period

### Payment Rules
- **Method:** Bank transfer or cash payment at school
- **Proof Required:** Parents upload receipt photo
- **Approval:** Principal manually approves payments
- **New Students:** Pro-rate fees based on enrollment date

### Implementation Notes
- Start with **fixed amounts** - don't build complex configuration
- **Single due date** for all fees - 5th of month
- **Manual approval process** - no automatic payment processing
- Add **family discounts later** if needed (Phase 2)

---

## 📝 Simple Assessment System

### Two Assessments Per Year
- **Mid-Year Assessment:** December (40% weight)
- **Final Assessment:** May (60% weight)

### Five Subject Areas
1. **Reading/Literacy** - Letters, words, story comprehension
2. **Numbers/Math** - Counting, basic math, number recognition  
3. **Social Skills** - Playing with others, sharing, following rules
4. **Physical Skills** - Running, jumping, coordination, fine motor
5. **Creative Expression** - Art, music, imagination, creativity

### Simple Grading (No Complex Scales)
- **Excellent** - Child exceeds expectations
- **Good** - Child meets expectations  
- **Satisfactory** - Child is progressing well
- **Needs Support** - Child needs extra help

### Teacher Process
1. Select student from class list (names only - no photos)
2. Rate each of the 5 subjects
3. Add optional comments
4. Save assessment
5. System generates parent report

### Keep It Simple
- **Fixed subject areas** - don't make them configurable initially
- **Descriptive grading only** - avoid number grades for preschoolers
- **Visual reports** - parents see progress in easy-to-understand format
- **Student names** - help teachers identify students quickly

---

## 🔔 Simple Reminder System

### Payment Reminders (Essential)
- **7 days before due date:** "Fee due in 1 week"
- **3 days before due date:** "Fee due in 3 days" 
- **1 day before due date:** "Fee due tomorrow"
- **1 day after due date:** "Payment overdue"
- **7 days after due date:** "Late fee will apply"

### Attendance Alerts
- **10:00 AM daily:** Check if child not marked present
- **Send notification:** "Haven't recorded [child name]'s attendance"
- **Parent can reply:** Quick absence notification

### Assessment Reminders  
- **2 weeks before:** "Assessment period starting soon"
- **3 days before:** "Assessment this week"

### Simple Implementation
- **Fixed message templates** - don't make them customizable initially
- **Push notifications only** - add SMS/email later if needed
- **Child-specific** - parents only get reminders for their children

### Development Priority
- **Start with payment reminders** - most important for school cash flow
- **Add attendance alerts** - helps teachers and parents
- **Assessment reminders later** - less critical, can be Phase 2

---

## 🧾 Simple Invoicing System (No Payment Gateway)

### Invoice Generation Flow
```javascript
// Simple Invoice System
{
  invoiceGeneration: {
    schedule: "monthly", // auto-generate on 1st of month
    dueDate: 5, // 5th of each month
    method: "automatic",
    
    // Invoice Structure
    template: {
      header: {
        branchInfo: true,
        invoiceNumber: "auto_generated", // format: BH-{BRANCH}-{YEAR}-{MONTH}-{STUDENT_ID}
        issueDate: "auto",
        dueDate: "configurable"
      },
      
      items: [
        {
          description: "Monthly Tuition - {MONTH} {YEAR}",
          amount: "from_fee_structure",
          quantity: 1
        }
      ],
      
      footer: {
        paymentInstructions: "configurable_per_branch",
        bankDetails: "optional",
        contactInfo: true
      }
    }
  },
  
  // Payment Proof System
  paymentProof: {
    enabled: true,
    allowedFormats: ["jpg", "png", "pdf"],
    maxFileSize: "5MB",
    requireApproval: true,
    approvalWorkflow: "principal_approval"
  }
}
```

### Invoice Management Features
- **Auto-Generation:** Monthly invoices created automatically
- **Proof Upload:** Parents can upload payment receipts
- **Manual Verification:** Principal approves payment proofs
- **Payment Tracking:** Simple paid/unpaid status tracking
- **Custom Instructions:** Branch-specific payment instructions

---

## 📱 Feed System (Child-Specific Updates)

### Smart Feed Configuration
```javascript
// Child-Specific Feed System
{
  feedLogic: {
    parentView: "child_specific_only", // parents only see posts about their child
    teacherPosting: {
      studentTagging: "required", // must tag students in posts
      classWideOption: false, // no class-wide posts to parents
      mediaRequired: true // encourage photo/video sharing
    },
    
    postTypes: [
      {
        type: "daily_activity",
        requiresTags: true,
        allowMedia: true,
        visibility: "tagged_parents_only"
      },
      {
        type: "achievement",
        requiresTags: true,
        allowMedia: true,
        visibility: "tagged_parents_only"
      },
      {
        type: "learning_moment",
        requiresTags: true,
        allowMedia: true,
        visibility: "tagged_parents_only"
      }
    ]
  },
  
  // Content Guidelines
  contentGuidelines: {
    encouragePersonalization: true,
    suggestDailyPosts: true,
    textOnly: true, // no photo/video sharing
    maxTextLength: 500
  }
}
```

### Feed Features
- **Child-Specific:** Parents only see posts tagged with their child
- **Teacher-Friendly:** Simple tagging interface with student names (no photos)
- **Text Updates:** Simple text posting for classroom activities (no photo sharing)
- **Personal Touch:** Each post feels personal to the parent
- **Daily Engagement:** Encourage regular updates from teachers

---

## BrightHill Messaging System (Malaysian Context)

### Email-Style Messaging Configuration
```javascript
// Email-Style Messaging (No WebSocket)
{
  messagingSystem: {
    type: "email_style", // no real-time chat
    refreshMethod: "pull_to_refresh", // manual refresh
    structure: {
      inbox: "chronological",
      threading: true, // group related messages
      folders: ["inbox", "sent", "important"],
      searchEnabled: true
    },
    
    messageTypes: [
      {
        type: "teacher_to_parent",
        subject_required: true,
        attachments_allowed: true,
        read_receipts: true
      },
      {
        type: "principal_to_parent",
        subject_required: true,
        priority_levels: ["normal", "important", "urgent"],
        attachments_allowed: true
      },
      {
        type: "parent_to_teacher",
        subject_required: true,
        attachments_allowed: true,
        auto_forward_to_principal: false,
        initiation_allowed: true
      },
      {
        type: "teacher_to_parent", 
        subject_required: true,
        attachments_allowed: true,
        initiation_allowed: false,
        reply_only: true
      }
    ]
  },
  
  // Notification Settings
  notifications: {
    newMessage: {
      push_notification: true,
      email_notification: false, // avoid email loops
      badge_count: true
    },
    messageRead: {
      read_receipts: true,
      sender_notification: false
    }
  }
}
```

### BrightHill Messaging Features
- **Familiar Interface:** Like email - subject lines, threading, folders
- **No Real-Time:** Avoids WebSocket complexity, uses pull-to-refresh
- **Professional:** Formal communication structure suitable for school environment
- **Simple Messaging:** Basic text messaging only (no attachments except payment receipts)
- **Message Limits:** Parent-principal max 3 reply exchanges per inquiry
- **Direction Control:** Parents initiate inquiries, teachers reply only
- **Malaysian English:** Support for local terminology and context

---

## 🎯 Kid-Friendly Design Guidelines

### Design Principles
```javascript
{
  colorScheme: {
    primary: "#4A90E2", // friendly blue
    secondary: "#7ED321", // success green
    accent: "#F5A623", // warning orange
    background: "#F8F9FA", // light, clean background
    childFriendly: ["#FFB84D", "#FF6B9D", "#4ECDC4", "#95E1D3"] // bright, happy colors
  },
  
  typography: {
    families: ["Inter", "Poppins"], // clean, readable fonts
    sizes: {
      headings: "larger_than_standard", // easy reading
      body: "16px_minimum", // accessibility standard
      child_content: "18px_minimum" // larger for child-related content
    }
  },
  
  iconography: {
    style: "rounded", // soft, friendly shapes
    childElements: "illustrated", // cartoon-like for children's areas
    parentElements: "clean_minimal", // professional for adults
    size: "24px_minimum" // easy touch targets
  },
  
  layout: {
    spacing: "generous", // plenty of whitespace
    buttons: "48px_minimum", // easy touch
    childContent: "card_based", // visually separated
    navigation: "simple_clear" // minimal cognitive load
  }
}
```

---

## 🔧 Technical Implementation Notes

### ShadCN Vue Integration
```javascript
// Web App Components (Already Generated)
{
  existingComponents: {
    ui: "shadcn-vue", // already implemented
    forms: "vue_compatible",
    tables: "data_tables_ready",
    modals: "dialog_system_ready"
  },
  
  customizations: {
    colorPalette: "kid_friendly_override",
    borderRadius: "increased_for_friendliness",
    shadowEffects: "soft_playful",
    animations: "gentle_transitions"
  },
  
  newComponents: [
    "StudentTagging", // for teacher posts
    "FeeCalculator", // pro-rating system
    "ExamMarking", // simple grading interface
    "InvoiceGenerator", // PDF generation
    "PaymentProofUpload" // image upload with approval
  ]
}
```

### Database Schema Updates
```sql
-- Fee Structure Table
CREATE TABLE fee_structures (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    branch_id UUID NOT NULL REFERENCES branches(id),
    fee_type VARCHAR(50) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    frequency VARCHAR(20) NOT NULL,
    due_day INTEGER,
    is_required BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Exams and Assessments
CREATE TABLE exams (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    exam_type VARCHAR(50) NOT NULL,
    class_id UUID NOT NULL REFERENCES classes(id),
    scheduled_date DATE NOT NULL,
    subjects TEXT[], -- array of subjects
    grading_scale VARCHAR(20) DEFAULT 'descriptive',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Student Marks
CREATE TABLE student_marks (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    exam_id UUID NOT NULL REFERENCES exams(id),
    student_id UUID NOT NULL REFERENCES students(id),
    teacher_id UUID NOT NULL REFERENCES users(id),
    subject VARCHAR(100) NOT NULL,
    grade VARCHAR(20), -- grade value
    comments TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(exam_id, student_id, subject)
);

-- Invoices
CREATE TABLE invoices (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    invoice_number VARCHAR(50) UNIQUE NOT NULL,
    student_id UUID NOT NULL REFERENCES students(id),
    parent_id UUID NOT NULL REFERENCES users(id),
    total_amount DECIMAL(10,2) NOT NULL,
    due_date DATE NOT NULL,
    status VARCHAR(20) DEFAULT 'pending',
    items JSONB NOT NULL, -- invoice line items
    payment_proof_url TEXT,
    approved_at TIMESTAMP,
    approved_by UUID REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Reminders Log
CREATE TABLE reminder_logs (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID NOT NULL REFERENCES users(id),
    reminder_type VARCHAR(50) NOT NULL,
    message_content TEXT NOT NULL,
    sent_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    read_at TIMESTAMP,
    related_id UUID -- can reference invoice, exam, etc.
);
```

---

## 📋 Implementation Priority

### Phase 1 (Essential Features)
1. **Teacher 4-Tab Navigation** - Home, Classroom, Messages, Profile
2. **Classroom Assignment System** - Admin assigns classrooms to teachers
3. **Attendance System** - Present/Absent only with edit approval
4. **Fee Structure Setup** - Basic monthly tuition with configurable amounts
5. **Simple Invoicing** - Auto-generated monthly invoices
6. **Payment Proof Upload** - Parents upload payment receipts
7. **Basic Reminders** - Fee due notifications
8. **Child-Specific Feed** - Teacher posts with student tagging

### Phase 2 (Enhanced Features)  
1. **Exam-Linked Grading** - Grades tied to specific exam types (Midterm, Final)
2. **Attendance Edit Approval** - Admin approval workflow for past attendance changes
3. **Pro-rated Billing** - Mid-month enrollment calculations
4. **Advanced Reminders** - Multiple reminder types and schedules
5. **Email-Style Messaging** - Formal communication system
6. **Reporting Dashboard** - Basic analytics and reports

### Phase 3 (Optional Enhancements)
1. **Family Discounts** - Multiple children fee reductions
2. **Advanced Grading** - Detailed assessment categories
3. **Custom Templates** - Personalized messages and reports
4. **Analytics Dashboard** - Advanced insights and trends
5. **Integration Options** - Third-party tool connections

---

### Updated Teacher Mobile App Structure

#### 4 Bottom Tab Navigation System
```javascript
// Teacher App Core Rules
{
  navigation: {
    type: "bottom_tabs",
    count: 4,
    tabs: ["Home", "Classroom", "Messages", "Profile"]
  },
  
  classroomAccess: {
    restriction: "admin_assigned_only",
    visibility: "assigned_classrooms_only",
    quickActions: ["attendance", "grade_mark"]
  },
  
  attendanceRules: {
    options: ["present", "absent"], // no late option
    editApproval: {
      required: true,
      scope: "past_records_only",
      approver: "admin"
    }
  },
  
  gradingSystem: {
    examTypes: ["midterm", "final", "assessment1", "assessment2"],
    linkage: "exam_student_tied",
    workflow: "classroom -> exam -> student -> grade"
  }
}
```

**Next Steps:**
1. ✅ Updated documentation with new teacher app structure
2. ✅ Created updated sitemaps reflecting 4-tab navigation
3. Design simple, kid-friendly UI mockups for 4-tab system
4. Plan database schema for classroom assignments and edit approvals
5. Create development timeline with new teacher workflow phases