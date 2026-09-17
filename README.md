# OmniPOS Universal POS — MVP 1.1

Corrected first-run flow: Sign In -> one-time POS setup -> universal POS workspace.

Setup options are shown only on first setup (or when "Run Setup Again" is selected):
- Business type
- Primary selling categories (multi-select)
- Language
- Currency

After setup the app includes Sale, Inventory, Reports, Products, and Settings. Demo data is persisted in browser localStorage.

Run with:
```cmd
npm install
npm run dev
```

Prototype sign-in accepts any non-empty username/email and password. Production should replace this with secure backend authentication.

## Login UI
The login page was redesigned to match the supplied OmniPOS reference: split branding/login layout, POS terminal logo, Sign In, Sign Up, and Forgot Password affordances.

## Inventory v1.3
Inventory now includes an overview dashboard, item management, search/filtering, low/out-of-stock states, inventory value, stock movements, receiving, adjustments, item detail drawer, reorder points, SKU/barcode fields, unit/cost tracking, and extension-ready workflows for transfers, purchase orders, suppliers, locations, and recipes/components.

## Reports v1.5
Reports now includes period filters, payment/category/cashier filters, Overview KPIs, time-of-day sales chart, transaction reporting, product performance, profitability, inventory reporting, payment breakdown, cashier reporting, tax summary, refunds/voids, shift/Z-report workspace, and CSV export. New sales store line-item/payment metadata for report aggregation.

## Settings v1.6
Expanded Settings into an administrative control center with Overview, Business Profile, POS & Checkout, Payments, Tax, Receipts, Inventory, Users & Security, Customers & Loyalty, Language & Region, Appearance, Notifications, Backup & Data, Integrations, and Audit Log. Settings are persisted in localStorage and designed for future backend integration.

## v1.8.1 Stability Fix
Restored the Inventory, Products, Reports, and supporting component definitions that were accidentally omitted from the v1.8 package. This fixes blank/black screens when selecting those navigation modules.

## OmniPOS v1.9 — Account & Owner PIN
- Sign Up now requires a strict 6-digit numerical Owner Switch PIN.
- Staff → Owner switching uses the signed-in account's 6-digit PIN.
- Login stores prototype accounts locally.
- Built-in test account: username `test`, password `test`, Owner PIN `062396`.
- Added Reset Data / Login control on the login page to clear local device data.

## OmniPOS v1.10 — Stock-Safe Sales
- Sale quantities cannot exceed the product's available tracked stock.
- Product buttons disable when stock is zero or the cart already contains the maximum available quantity.
- Cart +/- controls are capped at current stock.
- Checkout performs a final stock validation before completing a transaction.
- Negative tracked stock is normalized to zero on application load.

## OmniPOS v1.11 — Discreet Owner Switch
- Removed visible STAFF MODE / OWNER MODE labels.
- Owner Switch PIN inputs disable browser autofill and password-manager autofill hints.
- Owner Switch PIN is numeric-only and hard-capped at 6 characters.
- Sign-up and Settings Owner PIN fields enforce the same 6-digit limit.
- New setup no longer pre-populates an Owner PIN.
- Owner verification requires exactly 6 digits.

## OmniPOS v1.12 — Login Autofill Disabled
- Sign-in username/email field disables browser autofill.
- Sign-in password field disables autofill/password-manager completion hints.
- Sign-up username, password and confirmation fields disable autofill.
- Login and signup forms use explicit autocomplete controls and non-reused field names.

## OmniPOS v1.13 — Sale Search Autofill Disabled
- Disabled browser autofill/autocomplete on the Sale product search field.
- Added a unique field name and non-autofill form metadata.
- Disabled autocorrect, autocapitalize and spellcheck for fast POS product searching.

## OmniPOS v1.14 — Receipt Preview & Printer Setup
- Added a live test receipt preview in the previously unused right side of Receipt Settings.
- Added Test Print, which opens a printer-friendly sample receipt and invokes the browser print dialog.
- Added Detect Printers UI for Wi-Fi/network, Bluetooth and wired/USB connection paths.
- Uses browser capability detection for Bluetooth/USB and clearly reports that silent Wi-Fi discovery/direct thermal printing requires a native/mobile bridge or local print service.

## OmniPOS v1.15 — Products & Services Management
- Added Add, Edit and Remove controls to the Products & Services module.
- Added Product / Service / Bundle type selection.
- Added optional inventory tracking for services/non-stock items.
- Added product search/filtering.
- Added confirmation before catalog removal.
- Editing preserves the existing product ID so related inventory/sales references remain stable.

## OmniPOS v1.16 — Reference Receipt Design
- Updated the Receipt Settings preview to closely follow the supplied receipt reference.
- Added configurable business name, address lines, phone, footer, transaction/date/table information and payment detail presentation.
- Added itemized QTY / ITEM / PRICE columns, dashed separators, emphasized total, thank-you block and barcode-style footer.
- Updated Test Print Receipt to use the same reference layout.

## OmniPOS v1.18 — Universal Operations Foundation
Implemented from the requested roadmap items:
1. Realistic authentication/authorization structure foundation and account-scoped Owner PIN flow.
3. Order lifecycle and expanded checkout/payment methods.
4. Inventory movement/receiving workflow foundation.
5. Product/service management foundation.
6. Configurable business-specific modules.
7. Flexible tax-aware transaction calculations.
8. Template-ready receipt and test print workflow.
9. Printer Manager / hardware connection-ready UI.
10. Expanded reports foundation with transaction metadata.
11. Cash register and shift opening/closing foundation.
12. Audit event recording for sensitive local actions.
13. Centralized application state/data repository pattern using consistent entities; current demo remains local until an API/database is connected.
14. Offline-aware operation with pending-sync counter.
15. Installable PWA/mobile shell foundation and platform-service-ready hardware architecture.
16. Responsive compact navigation and quick command search.
17. Expanded POS controls: customers, purchasing, suppliers, expenses, loyalty, tables, appointments, delivery, cash register, audit and printer management.
