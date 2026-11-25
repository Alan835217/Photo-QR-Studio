# Photo QR Studio

A single-page web app: upload a photo, enter your information, and get a styled QR code with your photo in the middle. Scanning the code shows the information you entered.

## Run it
1. Unzip the folder.
2. Double-click `index.html` to open it in a browser (Chrome, Edge, Firefox, Safari).
3. Or host the folder on any static host (GitHub Pages, Netlify, Vercel, any web server).

No build step, no server, no account needed.

## Features
- QR types: contact card (vCard), plain text, link, WiFi, WhatsApp, UPI pay, email, location, calendar event, SMS, call
- Live preview with automatic scan check, contrast warnings
- Photo in the center (circle or rounded square, adjustable size)
- Colors, quick palettes, dot styles, caption under the code
- Downloads: PNG / JPG / WebP at 512-4096 px, SVG, business card image (3 templates)
- Copy image, share (on phones), printable sticker sheet
- Autosaves your form text in the browser, Hindi/English labels, light/dark mode
- Shortcut: Ctrl/Cmd + D downloads the QR

## Logo and icons
- `favicon.svg`: the app logo (also embedded in `index.html`, so the tab icon shows even without this file)
- `apple-touch-icon.png` (180 px): used when someone adds the page to an iPhone home screen
- `icon-512.png`: large icon for social profiles or a future installable-app setup
Keep `apple-touch-icon.png` next to `index.html` when you upload.

## Fields per content type
The form changes when you pick a content type:
- Contact card: name, phone, email, company
- Plain text: message / text
- Link: website URL
- WiFi: network name (SSID), password, encryption
- WhatsApp: country code, phone number, pre-filled message
- UPI pay: UPI ID (VPA), payee name, amount
- Email: recipient email, subject, body
- Location: latitude, longitude
- Event: title, start, end, location (plus time zone handling)
- SMS: phone number, message (plus SMS format)
- Call: phone number

## Format notes
- Contact card writes both `N:` (Last;First) and `FN:` lines (vCard 3.0)
- Email supports subject and body
- SMS can use `SMSTO:number:message` (best for Android) or `sms:` (standard)
- Event times are converted to UTC by default, or can be floating local time
- WhatsApp has a separate country-code field

## Internet needed on first load
The app loads two small libraries from cdnjs:
- qrcode-generator 1.4.4 (creates the QR code)
- jsQR 1.4.0 (scan check)

To work fully offline, download both files, put them in a `lib/` folder next to `index.html`, and change the two `<script src="...">` lines at the top of `index.html` to `lib/qrcode.min.js` and `lib/jsQR.min.js`.

## Notes
- The QR code stores text only, never the photo. The photo is a visual in the center.
- Always test-scan a code with a phone before printing it. Use a dark QR on a light background for best results.
- Your photo and details stay in your browser. Nothing is uploaded.
