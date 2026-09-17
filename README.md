# Snag Points — Standalone

A standalone browser-based Snag Points register.

## Files

- `index.html` — complete application. No build step is required.

## GitHub Pages

1. Create a new GitHub repository.
2. Upload `index.html` to the repository root.
3. Enable GitHub Pages from the repository's Pages settings.
4. Open the published page.

## WhatsApp ZIP import

Use WhatsApp's **Export Chat** function and keep the exported ZIP. The ZIP should contain the chat `.txt` and the exported photos.

In the app:
1. Choose the ZIP.
2. Click **Read ZIP & Review**.
3. Check the automatically matched photo/message records.
4. Correct Floor, Location, Description, or Status where necessary.
5. Click **Import Selected**.

The ZIP is processed in the browser; it is not sent to a server by this app.

## Important storage note

This first standalone version stores snag records and photo data in the browser's localStorage. Very large photo collections can exceed browser storage limits. For a large historical register, the next production step should move photos to IndexedDB or Supabase Storage while keeping only metadata locally.
