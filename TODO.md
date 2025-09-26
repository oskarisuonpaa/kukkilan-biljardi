# Kukkilan Biljardi - Development TODOs

## High Priority - Core Functionality

### 1. Security & Data Protection

- [ ] **Protect admin routes** - Authentication/authorization middleware
- [ ] **Encrypt customer data** - Encrypt sensitive booking information in database

### 2. Booking System Core Features

- [x] **Minimum booking duration (1h)** - Add validation to prevent < 1 hour bookings ✅ _Frontend + Backend validation_
- [x] **Modify booking calendars to reflect opening times** - Integrate opening hours with calendar availability ✅ _Calendar now uses dynamic operating hours, shows closed status, and respects opening exceptions_
- [x] **Connect opening exceptions to info field in /reserve** - Show holiday hours and full-day closures on booking page ✅ _Reserve page now displays upcoming exceptions (holidays, special hours, closures) with Finnish date formatting_
- [x] **Hourly pricing per table** - Database schema + admin interface for individual table pricing ✅ _Added hourly_price_cents field to calendars, backend API support, admin interface for setting prices, pricing utility functions_

### 3. UI/UX Improvements - Finnish Language

- [x] **All text in Finnish** - Replace all English text with Finnish equivalents
- [x] **Adjust table ordering in /reserve/tables** - Configurable table ordering via admin panel (snooker first by default) ✅ _Snooker tables now appear first, then sorted alphabetically_
- [x] **Fix calendar styling** - Improve calendar component appearance/functionality ✅ _Enhanced colors, contrast, and visual hierarchy_

## Medium Priority - Customer Experience

### 4. Information & Communication

- [x] **Information and notice board on front page** - Enhance homepage with dynamic content ✅ _Added notices section that displays active notices from backend with date formatting_
- [x] **Privacy policy page background image removal** - Clean up privacy policy styling ✅ _Background slideshow disabled on privacy page_
- [x] **Slower background image transitions** - Reduce animation frequency ✅ _Increased from 7s to 12s intervals with smoother 1.2s fades_

### 5. Booking Enhancements

- [ ] **Admin daily overview** - Single page showing all table reservations for selected day
- [ ] **Booking confirmation emails** - Email system integration ⚠️ _Requires customer email setup_
- [ ] **Booking terms and conditions** - Surveillance cameras, liability, etc. ⚠️ _Requires customer content_

## Lower Priority - Advanced Features

### 6. Payment Integration

- [ ] **Online payments + e-Passi support** - Integrate Skrill, Paytrail, or similar payment gateway

---

## Implementation Notes

### ⚠️ Customer Input Required:

- **Email configuration** (SMTP settings, templates)
- **Booking terms content** (surveillance, liability terms)
- **Payment gateway preferences** (Paytrail vs Skrill vs others)

### Technical Dependencies:

- **Database migrations** needed for: individual table pricing, opening exceptions, encrypted customer data, configurable table ordering
- **Admin authentication system** prerequisite for: pricing management, table ordering configuration, daily overview page
- **Email service integration** for: booking confirmations

### Quick Wins (Start Here):

1. Finnish language translations
2. Minimum booking duration validation
3. Calendar styling fixes
4. Table ordering adjustment

---

## Current Status

- ✅ Basic booking system functional
- ✅ Admin routes structure exists (needs protection)
- ✅ Media upload system working
- ⏳ Opening hours system exists (needs integration with booking calendar)
- ❌ Payment system not implemented
- ❌ Email system not implemented
