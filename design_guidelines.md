# CVS Dental Care CRM - Design Guidelines

## Design Approach

**Selected Approach:** Design System-Based with Healthcare UI Patterns

**Justification:** This is a utility-focused, information-dense healthcare application where efficiency, data clarity, and professional trust are paramount. The design will draw from modern healthcare platforms like Epic MyChart and Practo, emphasizing clean data presentation, intuitive workflows, and HIPAA-compliant professional aesthetics.

**Key Design Principles:**
1. **Clinical Clarity:** Information hierarchy optimized for quick scanning and decision-making
2. **Professional Trust:** Medical-grade precision in layouts and interactions
3. **Efficient Workflows:** Minimize clicks, maximize productivity for dental staff
4. **Data Density with Breathing Room:** Pack information without overwhelming

---

## Typography

**Font Families:**
- Primary: Inter (via Google Fonts CDN) - for UI elements, forms, tables
- Accent: Poppins (via Google Fonts CDN) - for headings, dashboard stats

**Type Scale:**
- **Hero Stats/Numbers:** text-4xl font-bold (dashboard metrics)
- **Page Headers:** text-3xl font-semibold 
- **Section Headers:** text-2xl font-semibold
- **Card Titles:** text-xl font-medium
- **Body Text:** text-base font-normal
- **Labels/Metadata:** text-sm font-medium
- **Captions/Helpers:** text-xs font-normal

**Line Heights:**
- Headers: leading-tight
- Body text: leading-relaxed
- Dense data (tables): leading-snug

---

## Layout System

**Spacing Primitives:** Tailwind units of **2, 4, 6, 8, 12, 16**
- Micro spacing (icons, badges): p-2, gap-2
- Standard component padding: p-4, p-6
- Section spacing: p-8, py-12
- Major layout gaps: gap-6, gap-8
- Container spacing: px-4 md:px-8

**Grid Structure:**
- **Dashboard Layout:** Fixed sidebar (w-64) + fluid main content area
- **Responsive Breakpoints:** Mobile-first, stack at md breakpoint
- **Content Max-Width:** max-w-7xl for main containers
- **Card Grids:** grid-cols-1 md:grid-cols-2 lg:grid-cols-3 for stat cards
- **Table Views:** Full-width responsive tables with horizontal scroll on mobile

**Page Structure:**
```
[Sidebar Navigation (fixed left)] | [Main Content Area]
                                   | - Page Header (sticky)
                                   | - Action Bar (search/filters/CTAs)
                                   | - Content Grid/List
```

---

## Component Library

### A. Navigation & Header

**Top Header Bar:**
- Full-width sticky header (h-16)
- Left: CVS Dental Care logo + clinic name (text-xl font-bold)
- Right: Contact info (phone icon + 7901403030, email icon + cvsdentalcare@gmail.com), user profile dropdown
- Icons from Heroicons (via CDN)

**Sidebar Navigation:**
- Fixed left sidebar (w-64, hidden on mobile with hamburger toggle)
- Menu items: Dashboard, Patients, Appointments, Reports, Settings
- Active state: subtle treatment, icon + label layout
- Bottom: User role badge + logout

### B. Dashboard Components

**Stat Cards (Grid of 4-6):**
- Compact cards in 2x2 or 3x2 grid
- Each card: Large number (text-4xl), label below (text-sm), trend icon
- Examples: Total Patients, Today's Appointments, Pending Treatments, This Month's Revenue

**Quick Actions Panel:**
- Prominent CTAs: "Add New Patient", "Schedule Appointment"
- Secondary actions: "View Calendar", "Generate Report"

**Activity Timeline:**
- Recent appointments, patient registrations
- List format with timestamps, patient names, treatment types

**Charts Section:**
- Appointments trend (line chart using Chart.js)
- Patient distribution by treatment type (donut chart)
- Monthly comparison (bar chart)

### C. Data Tables

**Patient List Table:**
- Headers: Name, Age, Gender, Phone, Last Visit, Actions
- Row height: h-12 with py-2 padding
- Zebra striping for readability
- Sticky header on scroll
- Action buttons: View, Edit, Delete (icon buttons, gap-2)
- Pagination at bottom: 10/25/50 per page options

**Appointment Table:**
- Headers: Date/Time, Patient Name, Doctor, Treatment, Status, Actions
- Status badges: Upcoming, Completed, Cancelled (with distinct treatments)
- Inline edit for status changes

### D. Forms

**Patient Profile Form:**
- Two-column layout on desktop (grid-cols-2 gap-6)
- Single column on mobile
- Input groups with labels above (text-sm font-medium mb-2)
- Input fields: h-10, px-4, rounded border
- File upload zone: Dashed border, drag-drop area for X-rays/documents
- Submit/Cancel buttons: Bottom right alignment

**Appointment Booking Form:**
- Date/time picker (integrate with calendar)
- Doctor/hygienist dropdown
- Treatment type selection
- Patient search/select (autocomplete)
- Notes textarea (h-24)

### E. Calendar View

**Monthly Calendar Grid:**
- 7-column grid for days of week
- Each cell shows appointments as small badges
- Click to view day details
- View toggles: Day/Week/Month tabs
- Today indicator

**Day/Week View:**
- Time slots in 30-min increments (8 AM - 8 PM)
- Appointment blocks with patient name, treatment
- Click to edit/reschedule

### F. Patient Detail Page

**Layout:**
- Two-column: Left (70%) patient details, Right (30%) quick actions
- Tab navigation: Profile, Treatment History, Appointments, Documents
- Treatment Timeline: Vertical timeline with dates, procedures, notes
- Document Gallery: Grid of uploaded files (X-rays, prescriptions) with thumbnails

### G. Search & Filters

**Global Search Bar:**
- Top of page: w-full max-w-md
- Placeholder: "Search patients, appointments..."
- Instant results dropdown

**Filter Panel:**
- Collapsible sidebar or top bar
- Filter by: Date range, Doctor, Treatment type, Status
- Clear all filters button

### H. Modals & Overlays

**Confirmation Dialogs:**
- Center screen, max-w-md
- Clear action (Delete patient, Cancel appointment)
- Primary/Secondary button pair

**Detail Modals:**
- Larger modals (max-w-2xl) for quick patient view
- Slide-in panels from right for edit forms

### I. Alerts & Notifications

**Toast Notifications:**
- Top-right position
- Auto-dismiss after 4 seconds
- Success, Error, Warning, Info types

**Reminder Badges:**
- Small badges on appointment cards for upcoming reminders
- Email/SMS status indicators

---

## Accessibility & Interaction

- All form inputs have visible labels and focus states
- Keyboard navigation for all interactive elements
- ARIA labels for icon-only buttons
- Color-blind safe status indicators (use icons + text)
- Touch targets minimum 44x44px for mobile

---

## Animations

**Minimal, Purposeful Animations:**
- Page transitions: Simple fade-in (duration-200)
- Modal entry: Scale-in (duration-300)
- Table row hover: Subtle background shift
- **No loading spinners** - use skeleton screens for data loading
- **No scroll animations** - instant content visibility

---

## Responsive Behavior

**Mobile Adaptations:**
- Hamburger menu for sidebar navigation
- Stack all multi-column layouts to single column
- Horizontal scroll for tables (with sticky first column)
- Bottom sheet modals instead of center modals
- Larger touch targets (h-12 for buttons)

**Desktop Optimizations:**
- Two-column forms
- Multi-column card grids
- Side-by-side calendar and appointment list
- Hover states for table rows and cards

---

## Images

**No Hero Images:** This is a utility application, not a marketing site. Dashboard leads with actionable data.

**Clinical/Contextual Images:**
- Placeholder avatar icons for patients (if no photo uploaded)
- Dental X-ray thumbnails in document gallery
- Empty state illustrations (use Heroicons for "No appointments scheduled")