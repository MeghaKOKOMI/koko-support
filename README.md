# KOKOMI Tip Page

A single-file UPI tipping page with a dark purple to baby purple theme.
Viewers pick an amount, the QR code updates instantly, and on mobile they can open their UPI app directly.

## Files

| File | What it is |
| --- | --- |
| `tip-page.html` | The complete page (HTML, CSS, JS and your logo, all in one file) |
| `README.md` | This guide |

## Quick start

1. Open `tip-page.html` in any browser to preview it.
2. Host it (see below) and share the link with your viewers.

The page needs an internet connection, because the QR library loads from cdnjs.

## Settings

Open `tip-page.html` in a text editor and find `CONFIG` near the bottom:

```js
const CONFIG = {
  upiId: "mmegha@ptyes",   // your UPI ID
  payeeName: "KOKOMI",     // name shown in UPI apps
  brand: "KOKOMI",         // name shown in the page header
  avatarUrl: "...",        // logo (embedded image or a normal image link)
  note: "Stream Tip",      // payment note
  presets: [50, 100, 200, 500],
  defaultAmount: 500
};
```

- Change `presets` to show different quick-amount buttons.
- Change `avatarUrl` to a normal image link (or another embedded image) to swap your logo.

## Colors

The colors are at the top of the file under `:root`:

- `--aqua`: main baby purple accent
- `--coral`: pink highlight
- `--line`, `--card`, `--mist`: borders, buttons and soft text

The background fade is in `body`, and the card fade is in `.wrap`.

## How it works

- The QR encodes a standard UPI link: `upi://pay?pa=<UPI ID>&pn=<name>&am=<amount>&cu=INR&tn=<note>`.
- Changing the amount (typing or tapping a preset) regenerates the QR.
- App buttons (Google Pay, PhonePe, Paytm, BHIM, Other) open the matching UPI app on mobile. On PC they stay disabled, so PC viewers scan the QR with their phone.
- The COPY button copies your UPI ID.
- Nothing is stored. There is no backend and no tracking.

## Hosting

Any static host works:

- **GitHub Pages:** upload the file as `index.html` to a repo and enable Pages.
- **Netlify or Vercel:** drag and drop the file.
- **Stream panels or bio link:** paste the hosted URL.

## Before you go live

- Send yourself ₹1 through the QR to confirm the UPI ID is correct and the money reaches you.
- If an app button opens nothing, that app is not installed on the viewer's phone. They can try another button or scan the QR.
- UPI apps decide whether to honor the amount and note, so a few apps may show them as editable.
