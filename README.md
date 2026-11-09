# Momora Room Management & Integrated Accounts Suite v3.0

Comprehensive Lodge & Postnatal Care Management Software designed for **Momora Postnatal Care**. Features complete room booking & date-wise availability tracking, medicines and pharmacy stock management, extra therapeutic treatments, customer invoicing, WhatsApp notifications (receipts, full bills, payment delay reminders), custom package rate editor, and strict Role-Based Access Control (Staff vs. Administrator).

---

## 🌟 Key Functional Modules

### 1. 🏢 9 Apartments Layout & 2BHK Full / Shared Dynamic Booking
- **9 Total Apartments configured across 14 Room Units**:
  - **3 Apartments — 1BHK Premium Suites (All Premium)**:
    - 👑 Apartment 1: `P-101` (1BHK Premium Suite)
    - 👑 Apartment 2: `P-102` (1BHK Premium Suite)
    - 👑 Apartment 3: `P-103` (1BHK Premium Suite)
  - **1 Apartment — 2BHK Premium Suite**:
    - 👑 Apartment 4: `P-104` (2BHK Premium Suite)
  - **5 Apartments — 2BHK Shared / Full Apartments (10 Bedrooms Total)**:
    - 🟢 Apartment 5: `C-101` (Classic Bedroom A) & 🔴 `S-101` (Standard AC Bedroom B)
    - 🟢 Apartment 6: `C-102` (Classic Bedroom A) & 🔴 `S-102` (Standard AC Bedroom B)
    - 🟢 Apartment 7: `C-103` (Classic Bedroom A) & 🔴 `S-103` (Standard AC Bedroom B)
    - 🟢 Apartment 8: `C-104` (Classic Bedroom A) & 🔴 `S-104` (Standard AC Bedroom B)
    - 🟢 Apartment 9: `C-105` (Classic Bedroom A) & 🔴 `S-105` (Standard AC Bedroom B)
- **⚡ 2BHK Full Booking Dynamics ("ഒരു 2BHK Full Book ചെയ്യുമ്പോൾ 2 റൂമിന്റെ എണ്ണം കുറയും")**:
  - **2BHK Shared**: Reserving as Shared occupies only the chosen bedroom (vacant room count drops by **1**). The paired bedroom remains vacant and can be independently booked by another guest.
  - **2BHK Full**: Reserving as Full blocks **both bedrooms** in that apartment!
    - The system vacant room count immediately decreases by **2**.
    - Both rooms in that apartment show occupied/booked status on the Rooms Grid with a paired indicator (`🔒 Apt 5 Full 2BHK with C-101`).
    - The date-range availability finder and calendar automatically count both rooms as occupied and prevent any overlapping bookings on either bedroom.
- **🔍 "Check Room Availability" Tool**:
  - Select any Check-in & Check-out date range.
  - Instantly reveals:
    - 🟢 **Available Rooms (Vacant)**: Ready to book, with a "+ Book Now" button that pre-fills the booking modal.
    - 🔴 **Occupied / Booked Rooms**: Displays guest names, stay dates, and paired full apartment lock notices.
  - Interactive Booking Calendar: Click on any day to inspect availability for that specific date.
- **Reservation Operations**: Check-in, Check-out, Edit, Cancel, and automatic double-booking prevention.
- **❌ Instant Cancel on Active Reservations**:
  - Explicit Cancel button (`❌ Cancel`) on every active reservation card.
  - Instantly cancels accidental reservations, vacating the room immediately and freeing it up for new bookings.

---

### 2. 🔐 Mandatory Login & Role-Based Access Control (Admin vs Staff)
- **Mandatory Login Gatekeeper on Open**:
  - Software opens directly with the **👑 Admin Login** tab active and ready by default.
  - **👑 Administrator Login**: Master credentials (Username: `Safvantt` / Password: `Sfz@78633`).
  - **👤 Staff Login**: Out-of-the-box pre-configured Duty Staff account (Username: `reception` / Password: `123`, or `staff` / `123`).
  - **Zero-Error Form Architecture**:
    - Pure JavaScript handling prevents any browser form submission reloads or query string leaks (`return false;` + `type="button"` + Enter key triggers).
    - Session state reliably persists in `sessionStorage` with instant visual status indicators.
  - **Fail-safe Direct Access ("Admin Login & Staff Login എപ്പോഴും ഓപ്പൺ ആകുന്ന സംവിധാനം")**:
    - **Header Buttons**: Dedicated `👑 Admin Login` and `👤 Staff Login` buttons in the top navigation header are always visible and clickable at all times.
    - **Interactive Role Badge**: Clicking the role badge in the top bar (`👑 Admin` / `👤 Staff`) directly opens the portal to switch accounts.
    - **Direct Tab Authentication**: Clicking any restricted Admin navigation tab (`💰 Accounts & Finance`, `👥 Staff Accounts`, `☁️ Cloud & Settings`) immediately pops up the Admin Login modal with automatic redirection after authentication.
    - **Strict Password Privacy**: Passwords are completely confidential and masked (`••••••••`), never displayed in plain text or hints.
  - **👥 Staff Account Creation by Admin**: To ensure privacy and data security, new staff IDs and passwords are created by Administrator inside `👥 Staff Accounts` with monthly salaries and contact info.
- **Staff Access**:
  - Front-desk operations: Check room availability, book rooms, check-in & check-out guests.
  - Dispense medicines & monitor stock availability.
  - Add extra treatments to room stays.
  - Manage bills, share receipts & delay reminders via WhatsApp.
  - **Restricted**: Front-desk staff have no access to overall facility net profits, consolidated financial reports, or system master settings.
- **Admin Access & Staff Salary / Advances Suite ("സ്റ്റാഫ് ശമ്പളവും വാങ്ങിയ പണവും ബാക്കി തുകയും")**:
  - Full access to `💰 Accounts & Finance` combining **Daily Income**, **Daily Expenses**, and **Monthly P&L Reports** in one unified dashboard.
  - **👥 Staff Salary & Cash Advances Ledger**:
    - **Monthly Salary Setting**: Assign each staff member a monthly base salary (₹).
    - **Live Month Picker**: Select any salary month cycle (`YYYY-MM`) with quick previous/next month navigation.
    - **💸 Record Staff Advance (പണം വാങ്ങിയത്)**:
      - Log advances taken with amount, payment mode (Cash, UPI, Bank Transfer), date, and purpose/reason.
      - **Live Balance Preview**: Instantly calculates and previews current balance payable and balance remaining after advance.
      - **Automatic Expense Integration**: Automatically logs advance into Facility Daily Expenses under `Staff Salary`, ensuring accurate daily/monthly accounts.
    - **Net Balance Payable (ബാക്കി കൊടുക്കാനുള്ള ശമ്പളം)**: Displays exact balance remaining (`Monthly Salary - Advances Disbursed`).
    - **📜 Staff Advances Register & History**: Chronological log of all disbursements with one-click view modal and delete actions.
  - Staff Account creation and credential management (`👥 Staff Accounts`).
  - System settings and financial ledger exports (Excel / PDF).

---

### 3. 📋 Active Reservations & Past Guest Check-out History
- **Clean Slate**: Active reservations list starts completely empty with no mock dummy profiles.
- **Separation of Checked-out Guests**:
  - Active reservation tab only shows active bookings (`Booked` & `Occupied`).
  - Once a mother checks out (`Completed`), she is automatically archived into **`📋 Check-out History (Past Guests)`**.
  - Front-desk staff can always review past stays, reprint bills, or re-share invoices without cluttering active rooms.

---

### 4. 💊 Medicines & Pharmacy Stock Management
- **Pre-seeded Authentic Brochure Medicines**:
  - *നാഡീകഷായം (Nadi Kashayam 450ml)* - ₹360 (Bottle)
  - *ത്രികടുചൂർണ്ണം (Thrikaduchooranam 100g)* - ₹180 (Packet)
  - *ഉലുവക്കഞ്ഞി കിറ്റ് (Uluva Kanji Kit)* - ₹250 (Kit)
  - *അയമോദകം (Ayamodakam Decoction 500ml)* - ₹140 (Bottle)
  - *മുക്കിടി (Mukkidi Herbal Remedy)* - ₹220 (Bottle)
  - *ധന്வந்தരം തൈലം (Dhanwantharam Thailam 450ml)* - ₹380 (Bottle)
  - *ബലാ തൈലം (Bala Thailam 450ml)* - ₹450 (Bottle)
  - *ദശമൂലാരിഷ്ടം (Dasamoolarishtam 450ml)* - ₹220 (Bottle)
  - *ജീരകാരിഷ്ടം (Jeerakarishtam 450ml)* - ₹210 (Bottle)
  - *സൗഭാഗ്യശുണ്ഠി ലേഹ്യം (Sowbhagya Shunti Lehyam 500g)* - ₹520 (Jar)
  - *രസ്നാദി ചൂർണ്ണം (Rasnadi Chooranam 50g)* - ₹90 (Packet)
  - *സ്നാന ചൂർണ്ണം (Herbal Baby Bath Powder)* - ₹290 (Packet)
  - *നാൽപാമരാദി തൈലം for Baby* - ₹360 (Bottle)
  - *പ്രസവരക്ഷാ കിറ്റ് (Maternity Healing Herbs Mix)* - ₹480 (Kit)
  - *വേദന സംഹാരി (Postpartum Pain Relief Liniment)* - ₹190 (Bottle)
- **🔍 Real-time Live Product Availability Search**:
  - Typing any medicine name provides an instant, interactive stock availability banner:
    - ✅ **IN STOCK**: Exact stock count, rate, and one-click "+ Bill to Room" action.
    - ⚠️ **LOW STOCK**: Warning for items under 5 units with restock prompt.
    - ❌ **OUT OF STOCK**: Clear alert preventing accidental dispensing.
    - ❌ **PRODUCT NOT FOUND**: Instant button to add the missing product to inventory.
- **Direct Room Dispensing**:
  - Dispense medications directly to a guest room. Automatically deducts inventory stock and itemizes onto the guest's running stay invoice.

---

### 5. 📦 Official Postnatal Packages & Dynamic Rate Card
- **Clean Rate Card**:
  - Detailed treatment lists removed from rate cards for a clean, uncluttered layout.
  - Highlights essential package duration, room rates, and luxury suite amenities.
- **Official Brochure Rate Matrix**:
  | Duration | Classic (2BHK Shared) | Classic (2BHK Full) | Standard AC (2BHK Shared) | Standard AC (2BHK Full) | Premium AC (1BHK) | Premium AC (2BHK) |
  | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
  | **07 Days** | ₹21,000 | ₹25,000 | ₹24,000 | ₹29,000 | ₹30,000 | ₹33,000 |
  | **10 Days** | ₹29,000 | ₹33,000 | ₹33,000 | ₹38,000 | ₹41,000 | ₹45,000 |
  | **14 Days** | ₹37,000 | ₹42,000 | ₹40,000 | ₹44,000 | ₹51,000 | ₹55,000 |
  | **21 Days** | ₹53,000 | ₹57,000 | ₹56,000 | ₹62,000 | ₹68,000 | ₹74,000 |
  | **28 Days** | ₹74,000 | ₹79,000 | ₹82,000 | ₹87,000 | ₹94,000 | ₹1,03,000 |
  | **40 Days** | ₹1,02,000 | ₹1,08,000 | ₹1,06,000 | ₹1,12,000 | ₹1,15,000 | ₹1,25,000 |
- **✏️ Editable Package Prices**:
  - Click **"✏️ Edit Package Prices"** in the Packages tab at any time to modify rates for any duration or room category.
  - Custom rates persist in `localStorage` and dynamically sync into new booking calculations.
  - One-click **"🔄 Reset to Brochure Rates"** to restore original rates whenever desired.

---

### 6. 🎨 Brochure Visual Theme & Category Colors
- **Brochure Color Scheme**:
  - Background: Warm Linen / Ivory (`#faf6f0`)
  - Accent / Primary: Coral Rose (`#e83a5e`)
  - Typography: Espresso Black (`#2d2522`)
  - Borders & Cards: Soft Warm Sand (`#ebdcd5`)
- **Explicit Room Category Colors**:
  - 👑 **Premium AC**: **Champagne Gold** (`#c59b27`)
  - 🔴 **Standard AC**: **Burgundy** (`#800020`)
  - 🟢 **Classic**: **Emerald Green** (`#0b664a`)

---

### 7. 🧾 Customer Billing, WhatsApp & Cloud Sync
- Single click generation of professional, printable invoices.
- Direct WhatsApp integration with pre-formatted Payment Receipts, Complete Bills, and Payment Delay Reminders.
- Optional Supabase Cloud Sync with local offline fallback.
