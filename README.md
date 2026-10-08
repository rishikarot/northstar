# Northstar POS v0.8 - Browser prototype

Open `index.html` in Chrome, Edge, or Safari. The application is a **single-browser demonstration**, not a secure production POS or a multi-counter branch database.

Demo sign-in accounts: Aisha Rahman (Cashier, PIN 1234), Daniel Tan (Supervisor, PIN 2222), and Nur Farah (SuperAdmin, PIN 9999). Demo PINs are client-side and must never be used as real credentials.

## Notable features
- Login screen; role-based module/menu visibility; custom role permissions; per-user branch mappings (UI only, not server-enforced)
- Collapsible left navigation groups with retained state and scroll position
- Malaysia sample branches, products, purchasing, transfers, shifts, sales, returns, reports, and audit log CSV export
- Product emoji search/categories, automatic SKU draft, cost+markup-price calculations, editable product rows, CSV sample template
- Mac payment: use **Shift+1 (Cash), Shift+2 (Card), Shift+3 (QR), Shift+4 (Credit)** while payment dialog is open. Arrow Up/Down cycles methods. `Ctrl+1–4` may also work where not OS-reserved. `Enter` completes payment.
- `F2` scan focus; `F3` edit; `F6` hold; `F8` resume; `F9` payment. Actual function keys may require Fn on Mac.

## Architecture limitation
All data, PINs, and role UI are stored in the browser. This is **not authentication or authorization security**. Offline multi-counter billing requires the planned branch server, SQLite transactional commits, backend RBAC, password hashing, network sync, and backup monitoring. Do not run real business payments using this prototype.

## Margin
Margin field is implemented as **markup on cost**, `(selling price - unit cost) / unit cost × 100`. Accounting gross margin on selling price is a different metric. The UI labels the input accordingly.

## Validation
JavaScript syntax validated with Node. Automated browser navigation/interaction was blocked by the test environment; test manually in your target Mac browser before demo.
