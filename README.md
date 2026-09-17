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


## WhatsApp import behavior

- The complete WhatsApp message text is placed into **Description** for the corresponding image group.
- Floor and Location are **not automatically extracted** from the message; you can enter them during Review.
- If one message has multiple exported images and the ZIP/chat export allows the filenames to be associated, those images are kept in one snag entry as Image 1, Image 2, Image 3, etc.
- Excel export now creates an `.xlsx` workbook with actual embedded images (for supported JPG/PNG/GIF photos), rather than only listing filenames.
- On a phone, Excel/Sheets preview apps may not render embedded images exactly like desktop Microsoft Excel. If images appear missing on mobile, open the `.xlsx` in Microsoft Excel desktop/web first to verify.


### Tested against the supplied WhatsApp export

The importer now handles the export pattern where WhatsApp writes:

- `IMG-....jpg (file attached)` on the timestamped message line
- the user's actual caption/message on the following line(s)
- several consecutive image-only attachment lines followed by one caption

In the last case, the consecutive images are grouped into **one snag entry** and the following caption becomes that entry's Description. The generated image filename and `(file attached)` marker are not put into Description.


## Excel photo export

The export now creates `snag-register-with-photos.xlsx`. Each photo is embedded in its corresponding **Image 1 / Image 2 / Image 3 / Image 4 / Image 5 cell area**, with the row height increased so the photo is visible like a pasted image in the spreadsheet.

The photos are embedded into the `.xlsx` package itself; they are not just filenames or external links.


## Photo export implementation

The XLSX export is generated directly as an Office Open XML package. Photos are written into `xl/media/` and connected to worksheet drawing anchors. Each photo is anchored to its Image 1–Image 5 cell area, so the `.xlsx` contains the actual image binary rather than a filename.


### Excel layout

The export is a photo-register layout: one snag occupies one row, and Image 1–Image 5 are dedicated photo cells. Each embedded photo is anchored to the complete cell area with a small margin and a tall row, so it visually appears like a photograph pasted into that cell, matching the supplied reference screenshot.
