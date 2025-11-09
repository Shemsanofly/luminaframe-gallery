# LuminaFrame — Simple image gallery

LuminaFrame is a small, local image gallery with a lightbox and an upload area. Open `index.html` in your browser to run the project locally.

## What I changed

- Extracted the large inline `<style>` block from `index.html` into an external `styles.css` file.
- Added Tailwind CSS via the official CDN (`<script src="https://cdn.tailwindcss.com"></script>`) in the head so you can use utility classes quickly.
- Applied a few Tailwind utility classes to the header, hero heading, and the primary CTA to improve visual polish while keeping existing custom styles.
- Added this `README.md` with usage notes.

Files updated/added:

- `index.html` — now links to `styles.css` and loads Tailwind via CDN. Small enhancements were added (Tailwind utility classes on header, hero, and CTA).
- `styles.css` — the extracted custom CSS (previously inline in `index.html`).
- `README.md` — this file.

## How to run

1. Open the project folder in your editor or file explorer.
2. Open `index.html` in your browser. (No server required for local testing.)

On Windows you can right-click `index.html` and choose "Open with" → your browser, or run from PowerShell:

```powershell
start .\index.html
```

## Notes on Tailwind usage

- Tailwind is loaded via CDN for convenience (great for prototyping). For production or more customization, integrate Tailwind using PostCSS or the Tailwind CLI so you can purge unused styles and configure the design system.

- The project's primary visual styles remain in `styles.css`. Tailwind utilities were added selectively — you can progressively refactor components to use Tailwind classes if you want a utility-first approach.

## Persistence of uploaded images

- Uploaded images are stored in your browser's localStorage so they remain visible when you reopen the page. This is client-side only and does not upload images to a server.
- localStorage has size limits (typically a few MBs). Storing many or very large images may fail. If you receive a storage error, consider uploading fewer images or smaller images. For production, switch to a server-side storage or IndexedDB for larger data.

If you'd like, I can switch the implementation to use IndexedDB for more robust local persistence.

## Next steps / suggestions

- Replace the Tailwind CDN with a proper build (Tailwind CLI / PostCSS) to remove unused CSS before deploying.
- Gradually convert components to Tailwind utilities and remove overlapping rules from `styles.css` to reduce specificity clashes.
- Improve lightbox transitions and add thumbnails or swipe gestures for mobile.

If you'd like, I can:

- Convert the layout to be mostly Tailwind utilities (cleaner, smaller CSS).
- Create a small build setup with Tailwind CLI (adds `package.json` + build script).

Tell me which next step you prefer and I'll implement it.

## Recent housekeeping

- The About page was intentionally removed from the site navigation and replaced with a small placeholder that redirects to the homepage. The file `about.html` remains as a redirect/placeholder to avoid broken links; remove it entirely if you want the file deleted.
- An admin messages page was added: `messages.html`. This page reads messages saved to localStorage under the key `luminaframe_messages_v1` and lets you view, copy, delete individual messages, or clear all stored messages.

To access messages, open `messages.html` in the same browser where messages were submitted. Note: messages are stored locally on that browser only.
