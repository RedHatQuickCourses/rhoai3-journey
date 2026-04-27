# PDF Conversion Guide

This guide provides detailed instructions for converting the HTML marketing materials to PDF format for printing, distribution, and presentation use.

## Quick Start

The easiest method is to use your web browser's built-in print-to-PDF function:

1. Open the HTML file in any modern browser (Chrome, Firefox, Safari, Edge)
2. Press `Cmd+P` (Mac) or `Ctrl+P` (Windows/Linux)
3. Select "Save as PDF" or "Print to PDF" as the destination
4. Click "Save" or "Print"

## Recommended Files for PDF Export

### 📄 `journey-infographic.html`
**Purpose:** One-page visual overview  
**Best for:** Handouts, email attachments, social media

**Print Settings:**
- Paper size: Letter (8.5" x 11")
- Orientation: Portrait
- Margins: Default
- Scale: 100%
- Background graphics: ON (to preserve colors)
- Headers/Footers: OFF

**Expected result:** Single-page PDF with full-color graphics

---

### 📄 `condensed-overview.html`
**Purpose:** Two-page comprehensive reference  
**Best for:** Workshops, proposals, executive briefings

**Print Settings:**
- Paper size: Letter (8.5" x 11")
- Orientation: Portrait
- Margins: Default (0.75 inches)
- Scale: 100%
- Background graphics: ON
- Headers/Footers: OFF

**Expected result:** Two-page PDF with tables and graphics

---

## Browser-Specific Instructions

### Google Chrome / Microsoft Edge

1. Open the HTML file in Chrome/Edge
2. File → Print (or `Cmd+P` / `Ctrl+P`)
3. Destination: Click "Change" → Select "Save as PDF"
4. Layout: Portrait
5. Paper size: Letter
6. Margins: Default
7. Options:
   - ✅ Background graphics
   - ❌ Headers and footers
8. Click "Save"
9. Choose filename and location

**Tip:** Chrome gives the best color accuracy and layout consistency.

---

### Safari (macOS)

1. Open the HTML file in Safari
2. File → Print (or `Cmd+P`)
3. Click "Show Details" at the bottom
4. PDF dropdown (bottom-left) → "Save as PDF"
5. Choose filename and location

**Note:** Safari may render some gradient backgrounds differently. Use Chrome for best results.

---

### Firefox

1. Open the HTML file in Firefox
2. File → Print (or `Cmd+P` / `Ctrl+P`)
3. Destination: Select "Save to PDF" or "Print to PDF"
4. Orientation: Portrait
5. Paper size: Letter
6. Print backgrounds: ON
7. Headers and footers: OFF
8. Click "Save"

---

## Advanced Options

### Using Command Line (macOS)

If you have `wkhtmltopdf` installed:

```bash
# Install wkhtmltopdf (one-time setup)
brew install wkhtmltopdf

# Convert to PDF
wkhtmltopdf --page-size Letter --orientation Portrait \
  journey-infographic.html journey-infographic.pdf

wkhtmltopdf --page-size Letter --orientation Portrait \
  condensed-overview.html condensed-overview.pdf
```

### Using Command Line (Linux)

```bash
# Install wkhtmltopdf (Ubuntu/Debian)
sudo apt-get install wkhtmltopdf

# Install wkhtmltopdf (RedHat/Fedora)
sudo dnf install wkhtmltopdf

# Convert to PDF
wkhtmltopdf --page-size Letter --orientation Portrait \
  journey-infographic.html journey-infographic.pdf
```

### Using Headless Chrome (Any OS)

If you have Chrome installed:

```bash
# macOS
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome \
  --headless --disable-gpu --print-to-pdf=journey-infographic.pdf \
  journey-infographic.html

# Linux
google-chrome --headless --disable-gpu --print-to-pdf=journey-infographic.pdf \
  journey-infographic.html

# Windows (PowerShell)
& "C:\Program Files\Google\Chrome\Application\chrome.exe" `
  --headless --disable-gpu --print-to-pdf=journey-infographic.pdf `
  journey-infographic.html
```

---

## Quality Tips

### For Best Print Quality

1. **Always enable "Background graphics"** — The color backgrounds are part of the design
2. **Use 100% scale** — Don't shrink to fit, the layouts are already optimized
3. **Disable headers/footers** — The URLs and page numbers clutter the design
4. **Use Chrome or Edge** — Better CSS rendering than other browsers
5. **Check the preview** — Before saving, verify the layout looks correct

### For Best File Size

The HTML → PDF conversion typically produces:
- Infographic: ~200-400 KB
- Condensed Overview: ~300-500 KB

If you need smaller files:
1. After generating PDF, use online compression (e.g., smallpdf.com)
2. Or use Preview (Mac): File → Export → Quartz Filter → "Reduce File Size"

### For Color Accuracy

If printing on professional printers:
- Save as PDF with "RGB" color space (default)
- For CMYK conversion, use Adobe Acrobat or professional print software
- The Red Hat red is `#cc0000` (RGB: 204, 0, 0 | CMYK: 0, 100, 100, 20)

---

## Troubleshooting

### Problem: Background colors don't print

**Solution:** Enable "Background graphics" or "Print backgrounds" in print settings

### Problem: Page breaks in wrong places

**Solution:** The HTML files are designed for letter-size. Ensure "Paper size: Letter" is selected, not A4

### Problem: Text is cut off

**Solution:** 
- Verify scale is 100%
- Check margins are "Default" (not "None" or "Minimum")
- Try a different browser (Chrome recommended)

### Problem: Fonts look different

**Solution:** The fonts are system fonts (Segoe UI, etc.). This is normal variation between operating systems. The layouts are designed to work with font substitution.

### Problem: PDF is too large

**Solution:**
- Use Chrome instead of Safari (better optimization)
- After generation, compress with Preview (Mac) or online tools
- The inline CSS and styling add some size but ensure consistency

---

## Bulk Conversion Script

To convert all marketing HTML files to PDF at once:

**macOS/Linux (bash):**
```bash
#!/bin/bash
for file in journey-infographic condensed-overview; do
  echo "Converting ${file}.html to PDF..."
  /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome \
    --headless --disable-gpu --print-to-pdf=${file}.pdf ${file}.html
done
echo "Done! Generated PDFs:"
ls -lh *.pdf
```

**Windows (PowerShell):**
```powershell
$files = @("journey-infographic", "condensed-overview")
foreach ($file in $files) {
    Write-Host "Converting $file.html to PDF..."
    & "C:\Program Files\Google\Chrome\Application\chrome.exe" `
      --headless --disable-gpu --print-to-pdf="$file.pdf" "$file.html"
}
Write-Host "Done! Generated PDFs:"
Get-ChildItem *.pdf
```

---

## Recommended File Names

When saving PDFs, use descriptive names:

- `RHOAI-3x-Journey-Infographic.pdf`
- `RHOAI-3x-Condensed-Overview.pdf`
- `RHOAI-3x-Executive-Brief.pdf` (if converting the full HTML)
- `RHOAI-3x-Practitioner-Guide.pdf` (if converting the full HTML)

This makes them easier to find and share via email or document management systems.

---

## Questions?

If you encounter issues not covered here, try:
1. Using Google Chrome (most reliable browser for HTML→PDF)
2. Checking that JavaScript is enabled (though these files don't require it)
3. Verifying your browser is up-to-date
4. Opening an issue in the repository with a screenshot of the problem

**Happy converting!** 📄✨
