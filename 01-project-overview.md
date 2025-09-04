# 📚 BrightHill Connect - Project Overview

**Version:** 1.0  
**Last Updated:** 2025-08-21  
**Status:** Development Phase  

## 🎯 Executive Summary

BrightHill Connect is a comprehensive preschool/kindergarten management system designed to streamline operations across multiple branches while providing a centralized digital platform for all stakeholders.

### Core System Features
1. **HQ Configurable Packages** - All programme types with configurable amounts
2. **Auto-Billing System** - Registration + monthly invoices from enrollment to year-end
3. **One-by-One Photo Attendance** - Mandatory photos for present students, no alternatives
4. **No Post Approval** - Classroom feed posts publish immediately
5. **Audit Logs** - All billing activities logged for HQ review

## 🏢 Organization Structure

### BrightHill Network
- **Central HQ (Management)** - Overall oversight and strategic management
- **Multiple Branches** - Individual preschool locations with local operations
- **Branch Principals** - Day-to-day branch management
- **Teachers** - Classroom instruction and student engagement
- **Parents** - Primary stakeholders for student welfare and fees

## 👥 Simple User Structure

| Who | Uses What | Does What |
|-----|-----------|-----------|
| **HQ/Branch Principal** | Web App | HQ configurable packages, auto-billing, configurable admin accounts |
| **Teachers** | Mobile App | One-by-one photo attendance (mandatory), text classroom updates |
| **Parents** | Mobile App | Auto-billing notifications (25th), Billplz payments, child updates |

## 🛠 Technical Architecture

### Web Application (Admin/Principal)
- **Frontend:** Vue.js with Nuxt.js
- **Target Users:** Central Admin, Branch Principals
- **Device Focus:** Desktop/Tablet optimized

### Mobile Application (Teacher/Parent)
- **Frontend:** React Native
- **Target Users:** Teachers, Parents
- **Device Focus:** Mobile-first with tablet support

### Backend System
- **Status:** Unified backend for both platforms (confirmation pending)
- **Integration Points:** Payment gateways, notification systems, reporting

## 🎯 Current Development Status

### ✅ Completed
- Web application base structure (AI-generated)
- Mobile app foundation (login, settings, basic templates)
- Core user role definitions
- Initial wireframes and screen specifications

### 🔄 In Progress
- Feature synchronization between platforms
- Detailed dashboard designs (especially teacher/parent)
- Client requirements finalization

### ⏳ Pending
- Final design approval from BrightHill
- Backend architecture confirmation
- Payment gateway integration specifications
- Branding guidelines implementation

## 🚀 Development Approach

### Phase 1 (Current)
- **Scope:** Essential features for 2-person development team
- **Duration:** Quick delivery with proper foundation
- **Focus:** Core functionality over advanced features
- **Strategy:** Minimum viable product with room for expansion

### Key Constraints
- **Team Size:** 2 developers
- **Timeline:** Rapid development cycle
- **Client Feedback:** Awaiting detailed requirements from BrightHill

## 📋 Success Metrics

1. **Operational Efficiency**
   - Reduced manual paperwork and WhatsApp coordination
   - Automated fee collection tracking
   - Real-time attendance monitoring

2. **User Engagement**
   - Daily active users (teachers taking attendance)
   - Parent app usage for progress tracking
   - Communication frequency between stakeholders

3. **Business Impact**
   - Improved fee collection rates
   - Enhanced parent satisfaction
   - Streamlined branch operations

## 📚 Related Documentation

- [User Roles & Permissions](02-user-roles.md)
- [Feature Specifications](03-feature-specifications.md)
- [Site Maps & User Flows](04-sitemaps-flows.md)
- [Complete Menu Hierarchy](10-menu-ideas.md)
- [Technical Requirements](05-technical-requirements.md)
- [Context Questions](06-context-questions.md)

---

**Next Review:** Update with client feedback and development progress  
**Stakeholder Approval:** Pending BrightHill management review