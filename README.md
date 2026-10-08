# Northstar POS v0.12 — Session & Contextual Scanning

## Start
Upload **the contents** of this folder to the root of your GitHub Pages repository. Open its HTTPS Pages URL. Hard-refresh once after deployment so the updated PWA shell is used.

## Changes
- Demo login is retained for up to 8 hours within the same browser tab/session after refresh. Explicit Log out clears it. Opening in a separate browser, private mode, or after browser session removal can require sign-in again. Do not use demo PIN security in production.
- Products → Add/Edit Product → **Scan barcode / QR**. Scanning a new barcode or product code fills the barcode form field without saving the product. An existing code is rejected to avoid duplicate barcode assignments.
- Purchasing → Receive purchase stock → **Scan item barcode / QR**. A recognized existing barcode or SKU selects that product and populates its unit cost, without posting stock until Save. Unknown items must be created in Products.
- Sales → Scan continues to open the quantity dialog for recognized codes.
- Live scanning uses html5-qrcode loaded from a CDN on first use; requires internet initially; browser-native BarcodeDetector fallback and manual entry are available. Secure HTTPS (or localhost) and camera permission are required.

## Notes
Browser localStorage keeps sample business data. `sessionStorage` only retains the demo user ID, branch, view and expiry; it does not hold a secret/token or enforce permissions. Production login needs server-issued secure sessions and server-enforced permissions. PWA does not replace the local branch server.

## Testing
JavaScript parsing passed. Automated Chromium navigation was blocked in this build environment. Please smoke-test sign-in → refresh, Products scan, Purchases scan, and Sales scan on the deployed HTTPS site.
