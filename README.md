# Markdown File Viewer

A simple, lightweight web-based markdown previewer that renders `.md`, `.markdown`, and `.txt` files with GitHub-style formatting.

## Features

- **File and Folder Selection**: Select or drag markdown files and folders onto the viewer
- **Local Relative Images**: Preview images referenced from markdown files in a selected folder
- **Recent Files Sidebar**: Quick access to recently opened files
- **Table of Contents**: Quick access to headings in the content
- **GitHub-Style Rendering**: Clean, familiar markdown styling
- **Syntax Highlighting**: Code blocks with language-specific highlighting
- **Mermaid Diagram Rendering**: Diagrams using code blocks with mermaid syntax
- **Safe Preview by Default**: Removes unsafe HTML and disables Mermaid HTML/click features
- **Sandboxed Original Preview**: Review content that requires those features in an isolated iframe
- **Standalone HTML Export**: Download the current preview as a self-contained HTML document
- **Print / Save PDF**: Open the browser print dialog with previewer controls hidden
- **Responsive Design**: Works on desktop and mobile devices
- **No Installation Required**: Single HTML file, runs in any modern browser

## Usage

### Quick Start

1. Download `index.html`
2. Open it in your web browser
3. Drag a markdown file or folder onto the drop zone, or select a file or folder
4. View your rendered markdown instantly

### File Support

- `.md` files
- `.markdown` files  
- `.txt` files

### Folder Preview and Local Images

Select or drop a folder containing markdown and image files. The viewer chooses a markdown file using the following order:

1. `README.md` in the folder root
2. `index.md` in the folder root
3. The only markdown file, if there is one
4. A root-level markdown file, then the first markdown file by name

Images referenced with relative paths, such as `images/diagram.png` or `../assets/logo.svg`, are displayed when the referenced files are included in the selected folder.

### Export and Print

- Use **Download HTML** to save the safe rendered markdown as a standalone HTML file. Local images from a selected folder are embedded in the downloaded file.
- Use **Print / Save PDF** to open your browser's print dialog. Previewer controls and sidebars are hidden from the printed output.

### Content Safety

Markdown opens in **Safe mode** by default. Unsafe HTML and Mermaid links or click actions are disabled.

If a document needs HTML formatting or Mermaid interactions, a **Safe mode** checkbox appears in the document controls. Turn it off only for content you trust. After a warning, the original content is shown in an isolated preview.

Downloaded HTML files and printed documents always use the safe preview.

### URL Loading

You can also load markdown files directly from URLs by adding a `file` parameter:
```
index.html?file=https://raw.githubusercontent.com/user/repo/main/README.md
```

The target URL must allow cross-origin requests (CORS). Encode the URL before using it as a `file` parameter when it contains its own query string or fragment.

### Recent Files

- Access recently opened files via the left sidebar (click the left icon)
- Files are automatically added when opened
- Remove individual files or clear all recent files
- Recent files persist during your browser session

### Table of Contents

- Access the table of contents via the right sidebar (click the right icon)
- Click an item in the table of contents to scroll to that header.

## Technical Details

Built with:

- [Marked.js](https://marked.js.org/) for markdown parsing
- [Prism.js](https://prismjs.com/) for syntax highlighting
- [Mermaid.js](https://mermaid.js.org/) for rendering Mermaid diagrams
- [DOMPurify](https://github.com/cure53/DOMPurify) for HTML sanitization
- Vanilla JavaScript (no frameworks)
- GitHub-inspired CSS styling

## Browser Compatibility

Works in all modern browsers that support:
- File API
- Drag and Drop API
- ES6 features

## Local Development

No build process required! Simply:
1. Clone or download the repository
2. Open `index.html` in your browser
3. Start using it immediately

## Use Cases

- Previewing README files before committing
- Reading documentation without opening an IDE
- Quickly viewing markdown files from a file explorer
- Sharing rendered markdown with others
- Offline markdown viewing

## Limitations

- Local relative images are supported only when the markdown file is opened as part of a selected folder
- External images remain external URLs in downloaded HTML files
- Recent file history is lost when the page is closed (Stored in memory only; the browser's localStorage is not used)
- An internet connection is required for external resources (Libraries such as Mermaid, Prism, Marked, and DOMPurify are loaded from CDN)

## License

Feel free to use, modify, and distribute as needed.

---

**Note**: This tool runs entirely in your browser - no data is sent to any servers. All file processing happens locally on your machine.
