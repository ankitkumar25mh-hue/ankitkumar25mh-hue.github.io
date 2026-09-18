# Local Presentations Directory

This directory stores real PowerPoint presentations for local development and testing.

## Directory Structure

```
public/presentations/
├── README.md              # This file
├── .gitkeep               # Keeps directory in git
├── your-presentation.pptx # Place your .pptx files here
└── converted/             # Converted PDF files (auto-generated)
    └── your-presentation.pdf
```

## How to Add a Real Presentation for Testing

1. **Place your `.pptx` file** in `public/presentations/`
   - Example: `public/presentations/my-lecture.pptx`

2. **Convert to PDF** using one of these methods:

   ### Option A: LibreOffice (Recommended, Free)
   ```bash
   # Install LibreOffice first (https://www.libreoffice.org/)
   # Then run:
   libreoffice --headless --convert-to pdf --outdir public/presentations/converted public/presentations/my-lecture.pptx
   ```

   ### Option B: PowerPoint (Windows/macOS)
   - Open the .pptx in PowerPoint
   - File → Save As → PDF
   - Save to `public/presentations/converted/my-lecture.pdf`

   ### Option C: Online Converter (Quick Test)
   - Use cloudconvert.com, smallpdf.com, or similar
   - Upload .pptx, download PDF to `public/presentations/converted/`

3. **The application will auto-discover** the presentation if:
   - `.pptx` file exists in `public/presentations/`
   - Corresponding `.pdf` exists in `public/presentations/converted/`
   - Filenames match (e.g., `my-lecture.pptx` ↔ `my-lecture.pdf`)

## Supported File Naming

| PPTX File | Expected PDF | Presentation ID |
|-----------|--------------|-----------------|
| `finance-basics.pptx` | `finance-basics.pdf` | `finance-basics` |
| `Q3-results.pptx` | `Q3-results.pdf` | `Q3-results` |

The presentation ID is derived from the filename (without extension).

## Metadata

Currently, real presentations use:
- **Title**: Derived from filename (kebab-case → Title Case)
- **Category**: Defaults to "Finance" (can be extended with metadata file)
- **Description**: "Imported from PowerPoint file"
- **Date**: File creation date
- **Slides**: Auto-detected from PDF page count

## Notes

- **Do not commit** `.pptx` or `.pdf` files to git (they're in .gitignore)
- Large files should be added locally only
- For production, this will be replaced with Supabase Storage
- The conversion step is manual in Phase 2; will be automated later