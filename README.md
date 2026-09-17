# Snag Points — standalone

A standalone Snag Points register with a WhatsApp Export Chat ZIP importer.

## GitHub Pages
Upload `index.html` to the repository root and enable GitHub Pages from `main` / `root`.

## WhatsApp ZIP
Select the ZIP produced by WhatsApp Export Chat. The app reads the chat TXT and exported images locally. The actual user message becomes Description. Multiple photos attached to one message are grouped into one snag where the export structure permits it. Floor and Location are left for review rather than guessed.

## Excel photos
The Excel exporter is built into the app and does **not** use ExcelJS, SheetJS, or another external Excel library. It writes the XLSX package directly and embeds JPG/PNG photographs into `xl/media`, creates the Excel drawing relationships, and anchors each photograph to its Image 1–Image 5 cell area. The exported file is `snag-register-photo-register.xlsx`.

The Image cells are deliberately wide and the snag rows are tall so the photographs are visible like a pasted photo register.

## Browser storage
Snags are currently stored in localStorage. Large photo archives can eventually exceed browser storage limits; for large-scale production use, move photo blobs to IndexedDB or Supabase Storage.
