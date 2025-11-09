 # LuminaFrame — Local image gallery

 LuminaFrame is a small client-side image gallery with an interactive lightbox and a drag-and-drop / browse uploader.

 Functionality

 - Responsive image grid with featured photos.
 - Click an image to open the lightbox; navigate with prev/next buttons or Arrow keys; Escape closes the lightbox.
 - Upload images via drag & drop or file picker; previews display prior to upload.
 - Uploaded files are read with FileReader to data-URLs and appended to the gallery.
 - Client-side persistence: uploaded data-URL images are saved to localStorage under `luminaframe_user_images_v1` (subject to browser storage limits).
 - Filter images by category; deleting an image removes it from the gallery and persisted storage.

 Implementation notes (mechanism)

 - In-memory state: a `galleryImages` array holds initial images plus user uploads.
 - Upload flow: files → FileReader → data-URL → push into `galleryImages` → `renderGallery()` → `saveStoredImages()` writes uploads to localStorage.
 - Lightbox: `openLightbox(index)` sets `currentImageIndex`; `updateLightbox()` displays the image/caption; navigation wraps around the `galleryImages` array.
 - Filtering: `filterGallery(filter)` shows/hides `.gallery-item` elements using their `data-category` attributes.

 How to run

 - Open `index.html` in your browser (no server required).

 Notes

 - This project is entirely client-side; for larger persistence or multi-user features, use IndexedDB or a server backend.

- Tailwind is loaded via CDN for convenience (great for prototyping). For production or more customization, integrate Tailwind using PostCSS or the Tailwind CLI so you can purge unused styles and configure the design system.

- The project's primary visual styles remain in `styles.css`. Tailwind utilities were added selectively — you can progressively refactor components to use Tailwind classes if you want a utility-first approach.

## Persistence of uploaded images

- Uploaded images are stored in your browser's localStorage so they remain visible when you reopen the page. This is client-side only and does not upload images to a server.
- localStorage has size limits (typically a few MBs). Storing many or very large images may fail. If you receive a storage error, consider uploading fewer images or smaller images. For production, switch to a server-side storage or IndexedDB for larger data.

## Recent housekeeping

- An admin messages page was added: `messages.html`. This page reads messages saved to localStorage under the key `luminaframe_messages_v1` and lets you view, copy, delete individual messages, or clear all stored messages.

To access messages, open `messages.html` in the same browser where messages were submitted. Note: messages are stored locally on that browser only.
