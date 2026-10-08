# Northstar POS v0.11 — Live Barcode + QR PWA

Deploy **all contents** of this folder to GitHub Pages repository root. HTTPS is mandatory for camera use.

## Live scanner
- Open Sales → **Scan**, grant camera access.
- Scan QR, EAN-13, EAN-8, UPC-A/E, Code 128, Code 39, ITF or Codabar.
- Product barcodes and SKUs can also be encoded into QR codes. JSON QR codes (`{"sku":"..."}`) and QR URLs containing `?sku=` or `?barcode=` are supported for product lookup. Other QR payloads are treated as identifiers; URLs are never opened.
- A recognized product opens the quantity dialog; confirm to add it to the existing cart.
- **Flip camera**, **flash** (when supported), **scan photo**, and manual value entry are provided.

## Browser compatibility / first-time internet requirement
Scanner attempts to load **html5-qrcode v2.3.8** from `unpkg.com` on first use. After first load it may be retained in browser cache but **offline automatic scanning is not guaranteed** without bundling a local decoder. If loading fails, a native BarcodeDetector fallback is attempted where available. Manual entry always remains available. Camera requires HTTPS or localhost; opening local HTML directly does not enable camera access.

For production offline use, download/vendor the pinned audited scanner library into `vendor/html5-qrcode.min.js`, update SCANNER_LIB and service-worker precache, and retest on Android Chrome, iOS Safari, and desktop Chrome/Edge.

## Demo credentials
- SuperAdmin: Nur Farah, PIN 9999
- Supervisor: Daniel Tan, PIN 2222
- Cashier: Aisha Rahman, PIN 1234

## Boundaries
This is browser-local demonstration, not a production shared branch-server POS. Camera frames stay in the browser. Do not use real customer data or sensitive credentials.
