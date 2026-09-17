SNAG POINTS — FINAL LARGE WHATSAPP IMPORT VERSION

Use the included index.html in GitHub Pages.

FIXED:
- Large WhatsApp ZIP imports use IndexedDB instead of localStorage.
- Import writes records in batches of 5 to reduce transaction size on phones.
- Previous localStorage snag data is migrated once into IndexedDB.
- WhatsApp ZIP import and multi-photo grouping are retained.
- Excel export directly builds an XLSX and embeds actual JPG/PNG files under xl/media, with drawing anchors over Image 1–Image 5 cells.

VERIFIED:
- Full JavaScript syntax check passed.
- The exact XLSX writer was executed with a real JPEG data URL.
- The generated test XLSX contained xl/media/image1.jpeg, a drawing picture, an image relationship, and a worksheet drawing reference.
