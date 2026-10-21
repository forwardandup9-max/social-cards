# CLAUDE.md

## Image format

- Always save and upload images as **JPEG** (`.jpg`). Never save or upload PNG.
- Convert any PNG to JPEG before uploading it to Blotato (including via `blotato_create_presigned_upload_url`).
  - JPEG has no transparency: flatten transparent areas onto a white background.
  - Use quality 90 and keep the original dimensions.
  - Example (Python/Pillow):
    ```python
    from PIL import Image
    img = Image.open("in.png").convert("RGBA")
    bg = Image.new("RGB", img.size, "white")
    bg.paste(img, mask=img.getchannel("A"))
    bg.save("out.jpg", "JPEG", quality=90)
    ```
- Upload the converted `.jpg`, never the original `.png`.
