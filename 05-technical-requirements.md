# ⚙️ Technical Requirements - BrightHill Connect

**Auto-Billing System, One-by-One Photo Attendance, Configurable Admin Accounts**

## 🏗 System Architecture

**Web App (Vue/Nuxt)** → **Mobile App (React Native)** → **Backend (Node.js/Express/TypeScript)** → **Database (MariaDB)**

---

## 🌐 Frontend Technologies

### Web Application (Admin/Principal)
```javascript
// Technology Stack
{
  "framework": "Vue.js 3.x",
  "metaFramework": "Nuxt.js 3.x",
  "stateManagement": "Pinia",
  "uiFramework": "ShadCN Vue + Tailwind CSS",
  "buildTool": "Vite",
  "typescript": "TypeScript 4.9+",
  "authentication": "Nuxt Auth",
  "charts": "Chart.js / D3.js",
  "dateHandling": "Day.js",
  "formValidation": "VeeValidate",
  "httpClient": "Axios / $fetch"
}
```

#### Web App Architecture
```
src/
├── components/
│   ├── common/
│   ├── admin/
│   ├── principal/
│   └── shared/
├── pages/
│   ├── admin/
│   ├── principal/
│   └── auth/
├── layouts/
├── middleware/
├── plugins/
├── stores/
├── utils/
├── types/
└── assets/
```

### Mobile Application (Teacher/Parent)
```javascript
// Technology Stack
{
  "framework": "React Native 0.72+",
  "navigation": "React Navigation 6.x",
  "stateManagement": "Redux Toolkit / Zustand",
  "uiLibrary": "NativeBase / React Native Elements",
  "forms": "React Hook Form",
  "camera": "React Native Camera / Expo Camera",
  "pushNotifications": "Firebase Cloud Messaging",
  "asyncStorage": "AsyncStorage",
  "networking": "Axios / React Query",
  "animations": "React Native Reanimated 3.x",
  "biometric": "React Native Biometrics"
}
```

#### Mobile App Architecture
```
src/
├── components/
│   ├── common/
│   ├── teacher/
│   ├── parent/
│   └── shared/
├── screens/
│   ├── auth/
│   ├── teacher/
│   ├── parent/
│   └── shared/
├── navigation/
├── services/
├── stores/
├── utils/
├── types/
├── hooks/
└── assets/
```

---

## 🖥 Backend Technologies

### Core Backend Stack
```javascript
// Technology Recommendations
{
  "runtime": "Node.js 18+ LTS",
  "framework": "Express.js 4.x ",
  "language": "TypeScript 4.9+",
  "authentication": "JWT + Refresh Tokens",
  "validation": "Zod",
  "orm": "prisma",
  "database": "MariaDB 10.11+ (Primary)",
  "cache": "Redis 6.x",
  "fileStorage": "DigitalOcean Spaces",
  "email": "useplunk.com",
  "notifications": "Firebase Admin SDK",
  "monitoring": "Grafana + Prometheus"
}
```

### Backend Architecture
```
backend/
├── src/
│   ├── controllers/
│   │   ├── auth.controller.ts
│   │   ├── user.controller.ts
│   │   ├── student.controller.ts
│   │   ├── attendance.controller.ts
│   │   ├── payment.controller.ts
│   │   └── communication.controller.ts
│   ├── middleware/
│   │   ├── auth.middleware.ts
│   │   ├── validation.middleware.ts
│   │   ├── upload.middleware.ts
│   │   └── rateLimit.middleware.ts
│   ├── models/
│   ├── services/
│   ├── routes/
│   ├── utils/
│   └── types/
├── config/
├── migrations/
├── seeds/
└── tests/
```

---

## 🗄 Database Design

### Primary Database (MariaDB)
```sql
-- Core Tables Structure

-- Users table (all user types including new roles)
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role VARCHAR(20) NOT NULL CHECK (role IN ('admin', 'principal', 'configurable_admin', 'teacher_web', 'teacher_mobile', 'parent')),
    admin_permissions JSONB, -- for configurable_admin role: page permissions
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20),
    avatar_url TEXT,
    status VARCHAR(20) DEFAULT 'active',
    branch_id UUID REFERENCES branches(id),
    assigned_classes UUID[], -- for teachers
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Branches table
CREATE TABLE branches (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    address TEXT,
    phone VARCHAR(20),
    email VARCHAR(255),
    principal_id UUID REFERENCES users(id),
    capacity INTEGER,
    status VARCHAR(20) DEFAULT 'active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Students table
CREATE TABLE students (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    student_id VARCHAR(50) UNIQUE NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    date_of_birth DATE NOT NULL,
    gender VARCHAR(10),
    photo_url TEXT,
    branch_id UUID NOT NULL REFERENCES branches(id),
    class_id UUID REFERENCES classes(id),
    primary_parent_id UUID REFERENCES users(id),
    secondary_parent_id UUID REFERENCES users(id),
    enrollment_date DATE DEFAULT CURRENT_DATE,
    status VARCHAR(20) DEFAULT 'active',
    medical_info JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Classes table
CREATE TABLE classes (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(100) NOT NULL,
    branch_id UUID NOT NULL REFERENCES branches(id),
    teacher_id UUID REFERENCES users(id),
    capacity INTEGER,
    age_group VARCHAR(20),
    academic_year VARCHAR(10),
    status VARCHAR(20) DEFAULT 'active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Attendance table (one-by-one photo support)
CREATE TABLE attendance (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    student_id UUID NOT NULL REFERENCES students(id),
    class_id UUID NOT NULL REFERENCES classes(id),
    teacher_id UUID NOT NULL REFERENCES users(id),
    date DATE NOT NULL,
    status VARCHAR(20) NOT NULL CHECK (status IN ('present', 'absent', 'late')),
    check_in_time TIME,
    check_out_time TIME,
    photo_url TEXT, -- individual student photo for attendance verification
    photo_uploaded BOOLEAN DEFAULT FALSE,
    photo_upload_status VARCHAR(20) DEFAULT 'pending', -- pending, uploaded, failed
    photo_thumbnail_url TEXT, -- thumbnail for quick review
    remarks TEXT,
    edit_requested BOOLEAN DEFAULT FALSE,
    edit_reason TEXT,
    edit_approved_by UUID REFERENCES users(id),
    edit_approved_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(student_id, date)
);

-- Auto-Generated Student Bills
CREATE TABLE student_bills (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    student_id UUID NOT NULL REFERENCES students(id),
    parent_id UUID NOT NULL REFERENCES users(id),
    auto_generated BOOLEAN DEFAULT TRUE, -- automatically generated by system
    bill_number VARCHAR(50) UNIQUE NOT NULL,
    billing_month VARCHAR(7) NOT NULL, -- YYYY-MM format
    invoice_type VARCHAR(20) NOT NULL CHECK (invoice_type IN ('registration', 'monthly', 'additional')),
    package_type VARCHAR(20) CHECK (package_type IN ('full_day', 'half_day')),
    line_items JSONB NOT NULL, -- array of {description, amount, quantity}
    total_amount DECIMAL(10,2) NOT NULL,
    notification_date DATE NOT NULL, -- HQ configured notification date (25th)
    due_date DATE NOT NULL, -- configurable overdue date (1st of next month)
    status VARCHAR(20) DEFAULT 'pending' CHECK (status IN ('pending', 'notified', 'paid', 'overdue', 'cancelled')),
    additional_items_added BOOLEAN DEFAULT FALSE,
    late_enrollment BOOLEAN DEFAULT FALSE,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Auto-Billing Payments (Billplz only)
CREATE TABLE payments (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    bill_id UUID NOT NULL REFERENCES student_bills(id),
    parent_id UUID NOT NULL REFERENCES users(id),
    amount DECIMAL(10,2) NOT NULL,
    payment_method VARCHAR(50) DEFAULT 'billplz', -- auto-billing via Billplz only
    billplz_bill_id VARCHAR(255) NOT NULL, -- Billplz bill ID
    billplz_transaction_id VARCHAR(255), -- Billplz transaction ID
    billplz_status VARCHAR(50), -- paid, failed, pending, cancelled
    billplz_url TEXT, -- Billplz payment URL
    billplz_receipt_url TEXT, -- Billplz automatic receipts
    paid_date TIMESTAMP,
    status VARCHAR(20) DEFAULT 'pending' CHECK (status IN ('pending', 'processing', 'completed', 'failed', 'refunded')),
    failure_reason TEXT,
    notification_sent_date TIMESTAMP, -- when parent was notified
    auto_processed BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Messages table (Updated for Branch Communication)
CREATE TABLE messages (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sender_id UUID NOT NULL REFERENCES users(id),
    recipient_id UUID NOT NULL REFERENCES users(id), -- branch (principal/admin with message permission)
    branch_id UUID NOT NULL REFERENCES branches(id), -- all messages are branch-specific
    subject VARCHAR(255) NOT NULL, -- subject required for parent messages
    content TEXT NOT NULL,
    message_type VARCHAR(20) DEFAULT 'parent_to_branch',
    thread_id UUID, -- for threading (max 3 exchanges)
    thread_count INTEGER DEFAULT 1, -- track exchange count
    attachments JSONB,
    read_at TIMESTAMP,
    replied_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Announcements table (Updated for HQ/Branch Targeting)
CREATE TABLE announcements (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    author_id UUID NOT NULL REFERENCES users(id),
    author_type VARCHAR(20) NOT NULL CHECK (author_type IN ('hq', 'branch')), -- who created
    target_audience VARCHAR(50) NOT NULL, -- 'all_network', 'all_teachers', 'all_parents', 'specific_branch', 'branch_users', 'branch_teachers', 'branch_parents'
    branch_ids UUID[], -- for targeting specific branches
    media_urls TEXT[],
    priority VARCHAR(20) DEFAULT 'normal',
    published_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    expires_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Configurable Admin Accounts (Enhanced)
CREATE TABLE admin_accounts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID NOT NULL REFERENCES users(id),
    created_by UUID NOT NULL REFERENCES users(id), -- Branch Principal who created this
    branch_id UUID NOT NULL REFERENCES branches(id), -- branch-specific only
    page_permissions JSONB NOT NULL, -- {"student_management": true, "teacher_management": false, etc}
    message_permission BOOLEAN DEFAULT FALSE, -- can handle parent messages
    account_description VARCHAR(255), -- "Student Admin", "Billing Admin", etc
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Auto-Billing Configuration
CREATE TABLE billing_config (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    branch_id UUID REFERENCES branches(id), -- null for HQ global config
    notification_day INTEGER NOT NULL DEFAULT 25, -- day of month for notifications
    due_day INTEGER NOT NULL DEFAULT 1, -- day of next month for overdue
    full_day_amount DECIMAL(10,2) NOT NULL DEFAULT 560.00,
    half_day_amount DECIMAL(10,2) NOT NULL DEFAULT 400.00,
    registration_amount DECIMAL(10,2) NOT NULL DEFAULT 1280.00,
    auto_billing_enabled BOOLEAN DEFAULT TRUE,
    late_enrollment_prorating BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Database Indexing Strategy
```sql
-- Performance Indexes (Enhanced)
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role_branch ON users(role, branch_id);
CREATE INDEX idx_users_assigned_classes ON users USING GIN(assigned_classes);
CREATE INDEX idx_students_branch_class ON students(branch_id, class_id);
CREATE INDEX idx_attendance_student_date ON attendance(student_id, date);
CREATE INDEX idx_attendance_date_status ON attendance(date, status);
CREATE INDEX idx_attendance_photo_status ON attendance(photo_upload_status);
CREATE INDEX idx_attendance_edit_requested ON attendance(edit_requested);

-- Auto-Billing System Indexes
CREATE INDEX idx_bills_student ON student_bills(student_id);
CREATE INDEX idx_bills_parent ON student_bills(parent_id);
CREATE INDEX idx_bills_auto_generated ON student_bills(auto_generated);
CREATE INDEX idx_bills_status ON student_bills(status);
CREATE INDEX idx_bills_due_date ON student_bills(due_date);
CREATE INDEX idx_bills_billing_month ON student_bills(billing_month);
CREATE INDEX idx_bills_invoice_type ON student_bills(invoice_type);
CREATE INDEX idx_bills_notification_date ON student_bills(notification_date);

-- Payment System Indexes
CREATE INDEX idx_payments_bill ON payments(bill_id);
CREATE INDEX idx_payments_parent ON payments(parent_id);
CREATE INDEX idx_payments_method ON payments(payment_method);
CREATE INDEX idx_payments_billplz_status ON payments(billplz_status);
CREATE INDEX idx_payments_verification_status ON payments(verification_status);
CREATE INDEX idx_payments_paid_date ON payments(paid_date);
CREATE INDEX idx_payments_billplz_bill ON payments(billplz_bill_id);
CREATE INDEX idx_payments_billplz_transaction ON payments(billplz_transaction_id);

-- Original Indexes
CREATE INDEX idx_messages_recipient_read ON messages(recipient_id, read_at);
CREATE INDEX idx_announcements_published ON announcements(published_at);
```

---

## 🔌 API Specifications

### RESTful API Design
```javascript
// Base URL Structure
const API_BASE = 'https://api.brighthill.com/v1';

// Authentication Endpoints
POST   /auth/login
POST   /auth/register
POST   /auth/forgot-password
POST   /auth/reset-password
POST   /auth/refresh-token
DELETE /auth/logout

// User Management
GET    /users                    // List users (admin/principal)
GET    /users/:id               // Get user details
PUT    /users/:id               // Update user
DELETE /users/:id               // Deactivate user
POST   /users/invite            // Send invitation

// Student Management
GET    /students                // List students
POST   /students                // Register new student
GET    /students/:id            // Get student details
PUT    /students/:id            // Update student
DELETE /students/:id            // Remove student
POST   /students/:id/parents    // Link parent to student

// Enhanced Attendance Management (with photo support)
GET    /attendance              // Get attendance records
POST   /attendance              // Mark attendance with photos
PUT    /attendance/:id          // Update attendance
POST   /attendance/photos       // Upload student photos for attendance
GET    /attendance/photos/:id   // Get attendance photo
POST   /attendance/edit-request // Request attendance edit approval
PUT    /attendance/approve-edit // Approve/reject attendance edit
GET    /attendance/summary      // Attendance statistics
GET    /attendance/reports      // Generate reports

// Auto-Billing System
GET    /auto-billing/bills              // List auto-generated bills
POST   /auto-billing/generate           // Trigger auto-bill generation for student
GET    /auto-billing/bills/:id          // Get auto-bill details
PUT    /auto-billing/add-items/:id      // Add items to existing monthly bill
GET    /auto-billing/student/:id        // Get all bills for specific student
POST   /auto-billing/notify             // Send notifications on configured date
GET    /auto-billing/config             // Get billing configuration
PUT    /auto-billing/config             // Update billing configuration

// Auto-Payment Management (Billplz Only)
GET    /payments                // List payments
POST   /payments/billplz        // Create Billplz payment URL (auto-triggered)
GET    /payments/:id            // Get payment details
GET    /payments/history        // Payment history
GET    /payments/receipts/:id   // Download Billplz receipt

// Admin Account Management
GET    /admin-accounts          // List branch admin accounts
POST   /admin-accounts          // Create admin account with page permissions
GET    /admin-accounts/:id      // Get admin account details
PUT    /admin-accounts/:id      // Update admin permissions
DELETE /admin-accounts/:id      // Deactivate admin account

// Billplz Integration
POST   /billplz/webhook         // Handle Billplz webhooks
POST   /billplz/create          // Create Billplz bill
GET    /billplz/status/:id      // Get Billplz payment status
GET    /billplz/transactions    // List Billplz transactions

// Communication (Updated)
GET    /messages                // Get branch messages
POST   /messages/branch         // Send message to branch
PUT    /messages/:id/read       // Mark as read
GET    /messages/thread/:id     // Get message thread (max 3 exchanges)
GET    /announcements           // Get announcements (HQ/Branch)
POST   /announcements/hq        // Create HQ announcement
POST   /announcements/branch    // Create branch announcement
GET    /announcements/history   // Get announcement history

// File Upload
POST   /upload/avatar           // Upload profile picture
POST   /upload/media            // Upload photos/videos
POST   /upload/document         // Upload documents
```

### API Response Format
```javascript
// Success Response
{
  "success": true,
  "data": {
    // Response data
  },
  "message": "Operation successful",
  "timestamp": "2025-08-21T10:00:00Z"
}

// Error Response
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": {
      "field": "email",
      "reason": "Invalid email format"
    }
  },
  "timestamp": "2025-08-21T10:00:00Z"
}

// Paginated Response
{
  "success": true,
  "data": {
    "items": [...],
    "pagination": {
      "page": 1,
      "limit": 20,
      "total": 100,
      "totalPages": 5,
      "hasNext": true,
      "hasPrev": false
    }
  }
}
```

---

## 🔐 Security Requirements

### Authentication & Authorization
```javascript
// JWT Token Structure
{
  "header": {
    "alg": "HS256",
    "typ": "JWT"
  },
  "payload": {
    "sub": "user_id",
    "email": "user@example.com",
    "role": "teacher",
    "branchId": "branch_id",
    "permissions": ["read:students", "write:attendance"],
    "iat": 1692628800,
    "exp": 1692632400
  }
}

// Refresh Token Flow
1. User login → Access token (15min) + Refresh token (7 days)
2. Access token expires → Use refresh token to get new access token
3. Refresh token expires → User must login again
```

### Security Measures
```javascript
// Password Requirements
const passwordPolicy = {
  minLength: 8,
  maxLength: 128,
  requireUppercase: true,
  requireLowercase: true,
  requireNumbers: true,
  requireSpecialChars: true,
  preventCommonPasswords: true,
  preventReuse: 5 // last 5 passwords
};

// Rate Limiting
const rateLimits = {
  login: "5 attempts per 15 minutes per IP",
  api: "1000 requests per hour per user",
  fileUpload: "10 uploads per minute per user",
  resetPassword: "3 attempts per hour per email"
};

// Data Encryption
const encryption = {
  passwordHashing: "bcrypt with 12 rounds",
  sensitiveData: "AES-256-GCM",
  dataInTransit: "TLS 1.3",
  apiKeys: "Environment variables only"
};
```

### Privacy & Compliance
- **GDPR Compliance:** User data export/deletion capabilities
- **Data Minimization:** Collect only necessary data
- **Access Logging:** Audit trail for all data access
- **Data Retention:** Automatic cleanup of expired data

---

## ☁️ Infrastructure & Deployment

### Deployment Architecture
```yaml
# Docker Compose Structure
version: '3.8'
services:
  web-app:
    build: ./web-app
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - API_URL=http://backend:3001

  backend:
    build: ./backend
    ports:
      - "3001:3001"
    environment:
      - DATABASE_URL=${DATABASE_URL}
      - REDIS_URL=${REDIS_URL}
    depends_on:
      - mariadb
      - redis

  mariadb:
    image: mariadb:10.11
    environment:
      - MARIADB_DATABASE=${DB_NAME}
      - MARIADB_USER=${DB_USER}
      - MARIADB_PASSWORD=${DB_PASSWORD}
      - MARIADB_ROOT_PASSWORD=${DB_ROOT_PASSWORD}
    volumes:
      - mariadb_data:/var/lib/mysql

  redis:
    image: redis:6-alpine
    volumes:
      - redis_data:/data

volumes:
  mariadb_data:
  redis_data:
```

### Cloud Infrastructure (AWS/GCP)
```javascript
// Infrastructure Components
const infrastructure = {
  compute: {
    web: "AWS ECS / Google Cloud Run",
    backend: "AWS ECS / Google Cloud Run",
    database: "AWS RDS MariaDB / Google Cloud SQL MariaDB"
  },
  storage: {
    files: "AWS S3 / Google Cloud Storage",
    cache: "AWS ElastiCache Redis / Google Memorystore"
  },
  networking: {
    loadBalancer: "AWS ALB / Google Cloud Load Balancer",
    cdn: "AWS CloudFront / Google Cloud CDN",
    dns: "AWS Route 53 / Google Cloud DNS"
  },
  monitoring: {
    logs: "AWS CloudWatch / Google Cloud Logging",
    metrics: "AWS CloudWatch / Google Cloud Monitoring",
    errors: "Sentry",
    uptime: "Pingdom / UptimeRobot"
  }
};
```

### CI/CD Pipeline
```yaml
# GitHub Actions Workflow
name: Deploy BrightHill Connect
on:
  push:
    branches: [main, staging]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run Tests
        run: |
          npm ci
          npm run test
          npm run test:e2e

  build-and-deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - name: Build Docker Images
      - name: Push to Registry
      - name: Deploy to Environment
      - name: Run Health Checks
```

---

## 📱 Mobile-Specific Requirements

### React Native Configuration
```javascript
// Performance Optimizations
const mobileConfig = {
  bundle: {
    enableHermes: true,
    bundleInDebug: false,
    minifyEnabled: true
  },
  images: {
    resizeMode: 'contain',
    cache: 'memory-disk',
    placeholder: 'blur'
  },
  navigation: {
    enableScreens: true,
    backBehavior: 'history'
  }
};

// Device Capabilities
const deviceFeatures = {
  camera: {
    quality: 0.8,
    allowsEditing: true,
    aspect: [4, 3]
  },
  notifications: {
    badge: true,
    sound: true,
    alert: true
  },
  storage: {
    secure: true, // Keychain/Keystore
    size: '100MB'
  }
};
```

### App Store Requirements
```javascript
// iOS App Store
const iosRequirements = {
  minimumVersion: "iOS 12.0",
  targetVersion: "iOS 16.0",
  devices: ["iPhone", "iPad"],
  permissions: [
    "NSCameraUsageDescription",
    "NSPhotoLibraryUsageDescription",
    "NSMicrophoneUsageDescription",
    "NSNotificationUsageDescription"
  ]
};

// Google Play Store
const androidRequirements = {
  minimumSDK: 23, // Android 6.0
  targetSDK: 33,  // Android 13
  permissions: [
    "CAMERA",
    "READ_EXTERNAL_STORAGE",
    "WRITE_EXTERNAL_STORAGE",
    "RECORD_AUDIO",
    "INTERNET",
    "WAKE_LOCK"
  ]
};
```

---

## 🔍 Monitoring & Analytics

### Application Monitoring
```javascript
const monitoring = {
  errorTracking: {
    service: "Sentry",
    environment: "production",
    release: "1.0.0"
  },
  performance: {
    apm: "New Relic / DataDog",
    realUserMonitoring: true,
    syntheticTests: true
  },
  logs: {
    level: "info",
    structured: true,
    retention: "30 days"
  },
  metrics: {
    customMetrics: [
      "user_login_count",
      "attendance_marked_count",
      "payment_success_rate",
      "message_sent_count"
    ]
  }
};
```

### Business Analytics
```javascript
const analytics = {
  userBehavior: {
    tool: "Google Analytics 4 / Mixpanel",
    events: [
      "user_login",
      "attendance_marked",
      "payment_completed",
      "message_sent",
      "announcement_viewed"
    ]
  },
  performance: {
    kpis: [
      "daily_active_users",
      "attendance_completion_rate",
      "payment_success_rate",
      "user_engagement_time"
    ]
  }
};
```

---

## 🧪 Testing Strategy

### Testing Pyramid
```javascript
// Unit Tests (70%)
const unitTests = {
  frontend: "Vitest / Jest",
  backend: "Jest / Mocha",
  mobile: "Jest",
  coverage: ">80%"
};

// Integration Tests (20%)
const integrationTests = {
  api: "Supertest",
  database: "Test containers",
  services: "Mock services"
};

// E2E Tests (10%)
const e2eTests = {
  web: "Playwright / Cypress",
  mobile: "Detox / Maestro",
  critical: "User journeys"
};
```

---

## 📋 Development Standards

### Code Quality
```javascript
const codeStandards = {
  linting: {
    javascript: "ESLint + Prettier",
    typescript: "TSLint rules",
    vue: "Vue ESLint plugin",
    react: "React ESLint plugin"
  },
  git: {
    commitFormat: "Conventional Commits",
    branchNaming: "feature/issue-description",
    prTemplate: "Required template",
    protection: "Require reviews"
  },
  documentation: {
    api: "OpenAPI/Swagger",
    code: "JSDoc comments",
    architecture: "ADRs (Architecture Decision Records)"
  }
};
```

---

**Implementation Priority:**
1. **Phase 1:** Core authentication, user management, basic dashboard
2. **Phase 2:** Student management, attendance system, basic communication
3. **Phase 3:** Payment system, advanced reporting, notifications
4. **Phase 4:** Advanced features, analytics, optimization

**Next Steps:**
1. Set up development environment and CI/CD pipeline
2. Implement core backend APIs
3. Create basic frontend layouts
4. Integrate authentication system
5. Deploy staging environment for testing