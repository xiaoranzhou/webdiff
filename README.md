# maDMP Validator & Diff Tool

A client-side web application for validating and comparing machine-actionable Data Management Plans (maDMP) according to the RDA DMP Common Standard.

## Features

### 1. JSON Validation
- Validates maDMP JSON against schema version 1.2
- Detailed error reporting with paths and descriptions
- Real-time validation feedback

### 2. Multiple Upload Methods
- **File Picker**: Traditional browse and select
- **Drag & Drop**: Drag JSON files directly into the browser
- **Paste JSON**: Copy and paste JSON content directly

### 3. API Integration
- Send maDMP to common-madmp-api endpoint
- Receive merged maDMP response
- Configurable endpoint URL (saved in localStorage)
- Connection testing

### 4. Diff Visualization (4 Formats)

#### Side-by-Side View
- Two-panel comparison with synchronized scrolling
- Color-coded changes (green=added, red=removed, yellow=modified)
- Line numbers for easy reference

#### Unified Diff View
- Git-style unified diff format
- Single panel showing all changes
- Context lines around modifications

#### JSONata Queries
- Transformation queries to convert input to output
- Grouped by change type (additions, deletions, modifications)
- Copy-to-clipboard functionality
- Value previews for each change

#### Tree View
- Hierarchical structure visualization
- Expandable/collapsible nodes
- Change indicators at each level
- Icons for different data types

### 5. Statistics
- Input JSON metrics (size, object count, depth)
- Diff statistics (total changes, percentages)
- Real-time updates

### 6. Search & Filter
- **Real-time Search**: Search across all changes by path or value
- **Filter by Type**: Show/hide added, removed, modified, or unchanged fields
- **Match Highlighting**: Visual highlighting of search results
- **Match Navigation**: Navigate through search results with keyboard shortcuts
- **Live Counters**: See counts of each change type with badge indicators

### 7. Change Navigation
- **Next/Previous Controls**: Navigate through changes sequentially
- **Keyboard Shortcuts**: Use Alt+Arrow keys for quick navigation
- **Visual Highlighting**: Current change highlighted in active view
- **Change Counter**: Track your position (e.g., "3 / 15")
- **Cross-View Support**: Navigation works across all diff visualization formats

### 8. Session Management
- **Save Sessions**: Save current comparison state for later review
- **Session History**: Browse previously saved sessions
- **Bookmarks**: Star important sessions for quick access
- **Auto-naming**: Sessions automatically named with timestamps
- **Quick Restore**: Click any session to instantly restore it
- **Clear History**: Remove old sessions to keep history manageable

### 9. Export & Share (Multiple Formats)
- **JSON Export**: Raw diff data for programmatic use
- **HTML Export**: Self-contained report viewable in any browser
- **PDF Export**: Professional formatted reports with statistics
- **CSV Export**: Tabular data for spreadsheet analysis
- **Markdown Export**: Documentation-friendly format for wikis/README files
- **Copy to Clipboard**: Quick copy of diff results as text

### 10. Keyboard Shortcuts
- **File Operations**: Ctrl+O (open), Ctrl+S (save session), Ctrl+E (export)
- **Navigation**: Alt+Arrows (next/prev change)
- **Search**: Ctrl+F (focus search), F3 (next match), Shift+F3 (prev match), Esc (clear)
- **Views**: Ctrl+1/2/3/4 (switch diff views)
- **Other**: Ctrl+D (dark mode), F11 (fullscreen), ? (show shortcuts help)
- **API**: Ctrl+Enter (send to API)

### 11. UI Features
- Dark mode toggle (with localStorage persistence)
- Responsive design (mobile-friendly)
- Fullscreen mode for diff views
- Toast notifications for user feedback
- Loading indicators for async operations
- Tooltips on all interactive elements
- Professional color-coded changes
- Collapsible tree nodes

## Technology Stack

- **UI Framework**: Bootstrap 5.2
- **JavaScript**: Vanilla ES6+
- **State Management**: Zustand v4
- **JSON Validation**: Ajv v8
- **Query Language**: JSONata v2
- **Diff Engine**: jsdiff v5
- **PDF Generation**: jsPDF v2.5
- **Schema**: RDA-DMP-Common-Standard v1.2

## Getting Started

### 1. Open the Application

Simply open `index.html` in a modern web browser. No build process or server required!

```bash
# Open with default browser
open index.html

# Or use a local server
python3 -m http.server 8000
# Then navigate to http://localhost:8000
```

### 2. Upload a maDMP JSON File

Choose one of three methods:
- Click "File" tab and browse for a JSON file
- Click "Drop" tab and drag a file into the drop zone
- Click "Paste" tab and paste JSON content directly

### 3. Validate

The tool automatically validates your maDMP against schema v1.2 and displays results.

### 4. Configure API (Optional)

1. Enter your common-madmp-api endpoint URL
2. Click "Test Connection" to verify
3. Click "Send to API" to submit your maDMP

### 5. View Differences

Switch between the four visualization formats to explore changes:
- **Side-by-Side**: Visual comparison
- **Unified**: Git-style diff
- **JSONata**: Transformation queries
- **Tree**: Structural view

### 6. Search and Navigate Changes

- Use the search bar to find specific changes by path or value
- Toggle filters to show/hide change types (added, removed, modified, unchanged)
- Use navigation buttons or Alt+Arrow keys to move between changes
- Press Ctrl+F to focus the search box, F3 for next match

### 7. Save and Manage Sessions

- Click "Save Session" to save the current comparison
- View session history in the left sidebar
- Click the star icon to bookmark important sessions
- Click any session to restore it instantly
- Click "Clear History" to remove all saved sessions

### 8. Export Results (Multiple Formats)

- Click the "Export" dropdown to choose format:
  - **JSON**: Raw diff data
  - **HTML**: Self-contained browser report
  - **PDF**: Professional formatted document
  - **CSV**: Spreadsheet-compatible table
  - **Markdown**: Documentation-friendly format
- Use "Copy" button for quick clipboard copy
- Press ? key to view all keyboard shortcuts

## File Structure

```
standard-diff/
├── index.html                          # Main HTML file
├── README.md                           # This file
├── css/
│   └── styles.css                      # Custom styles & dark mode
├── js/
│   ├── main.js                         # Application entry point
│   ├── store.js                        # Zustand state management
│   ├── utils.js                        # Utility functions
│   ├── validator.js                    # JSON schema validation
│   ├── api.js                          # API integration
│   ├── diff-engine.js                  # Diff calculation
│   ├── diff-search.js                  # Search & filter functionality
│   ├── diff-navigation.js              # Change navigation controls
│   ├── session-manager.js              # Session save/load/history
│   ├── keyboard-shortcuts.js           # Keyboard shortcuts system
│   ├── diff-renderers/
│   │   ├── side-by-side.js             # Side-by-side view
│   │   ├── unified.js                  # Unified diff view
│   │   ├── jsonata.js                  # JSONata queries
│   │   └── tree.js                     # Tree structure view
│   └── exporters/
│       ├── pdf-exporter.js             # PDF report generation
│       ├── csv-exporter.js             # CSV export
│       ├── markdown-exporter.js        # Markdown export
│       └── html-exporter.js            # HTML report generation
└── schemas/
    └── maDMP-schema-1.2.json           # maDMP JSON schema v1.2
```

## Example maDMP Files

Example maDMP JSON files are available in the `RDA-DMP-Common-Standard/examples/JSON/` directory:

- `ex8-dmp-minimal-content.json` - Minimal valid maDMP
- `ex9-dmp-long.json` - Comprehensive example
- `ex1-header-fundedProject.json` - Funded project example
- And more...

## Browser Compatibility

Tested and working on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## API Endpoint Configuration

The tool expects a common-madmp-api endpoint that:

1. Accepts POST requests with maDMP JSON
2. Returns merged/processed maDMP JSON
3. Supports content negotiation:
   - Accepts: `application/vnd.org.rd-alliance.dmp-common.v1.2+json`
   - Returns: `application/vnd.org.rd-alliance.dmp-common.v1.2+json`

Example endpoint: `https://your-api.example.com/dmps`

## Validation Schema

The tool validates against RDA DMP Common Standard v1.2:
- Schema location: `schemas/maDMP-schema-1.2.json`
- Standard: [RDA-DMP-Common-Standard](https://github.com/RDA-DMP-Common/RDA-DMP-Common-Standard)

## Features in Detail

### Validation Errors

When validation fails, you'll see:
- Error count badge
- JSON path to error location
- Detailed error message
- Error type (required, type, format, etc.)

### Diff Statistics

The tool calculates and displays:
- Total number of changes
- Added fields count
- Removed fields count
- Modified fields count
- Change percentage

### Search & Filter

The search functionality allows you to:
- Search by JSON path (e.g., "dmp.title")
- Search by value (e.g., "MIT License")
- Filter results by change type
- See match counts in real-time
- Navigate matches with F3/Shift+F3
- Clear search with Esc key

### Session Management

Sessions store complete comparison state:
- Input and output JSON
- Validation results
- Diff results and statistics
- API endpoint configuration
- Maximum 20 sessions kept (oldest auto-deleted)
- Bookmark favorite sessions with star icon
- Export sessions for sharing

### Keyboard Shortcuts Reference

| Category | Shortcut | Action |
|----------|----------|--------|
| **File** | Ctrl+O | Open file picker |
| | Ctrl+S | Save current session |
| | Ctrl+E | Export diff |
| **Navigation** | Alt+← / Alt+↑ | Previous change |
| | Alt+→ / Alt+↓ | Next change |
| **Search** | Ctrl+F | Focus search box |
| | F3 | Next search result |
| | Shift+F3 | Previous search result |
| | Esc | Clear search |
| **Views** | Ctrl+1 | Side-by-side view |
| | Ctrl+2 | Unified view |
| | Ctrl+3 | JSONata view |
| | Ctrl+4 | Tree view |
| **Other** | Ctrl+D | Toggle dark mode |
| | F11 | Toggle fullscreen |
| | ? | Show shortcuts help |
| | Ctrl+Enter | Send to API |

### Export Formats Comparison

| Format | Best For | Features |
|--------|----------|----------|
| **JSON** | APIs, automation | Raw structured data |
| **HTML** | Sharing, archiving | Self-contained, interactive |
| **PDF** | Reports, printing | Professional formatting |
| **CSV** | Spreadsheets, analysis | Tabular data |
| **Markdown** | Documentation, wikis | Human-readable text |

### Dark Mode

Toggle between light and dark themes:
- Preference saved to localStorage
- Optimized color schemes for both modes
- Reduced eye strain in low-light environments
- Toggle with button or Ctrl+D shortcut

## Troubleshooting

### Validation Fails
- Ensure JSON is valid (use JSONLint.com)
- Check that it follows maDMP schema v1.2
- Review error messages for specific issues

### API Connection Fails
- Verify endpoint URL is correct
- Check CORS headers are enabled on API
- Test endpoint with curl/Postman first
- Check browser console for errors

### Diff Not Showing
- Ensure both input and output are loaded
- Check that validation passes for both
- Refresh the page and try again

## Development

### Local Development

1. Clone the repository
2. Open `index.html` in a browser
3. Make changes to JS/CSS files
4. Refresh browser to see changes

### Code Structure

- **Modular Design**: Each component is self-contained
- **State Management**: Zustand for reactive state
- **Event-Driven**: DOM events trigger state updates
- **No Build Required**: Pure vanilla JavaScript

### Adding Features

1. Create new module in `js/`
2. Add to `index.html` script tags
3. Wire up in `main.js`
4. Test thoroughly

## License

This tool is provided as-is for validating and comparing maDMP documents according to the RDA DMP Common Standard.

## Credits

- RDA DMP Common Standards Working Group
- Bootstrap 5.2 framework
- Zustand state management
- Ajv JSON schema validator
- JSONata query language
- jsdiff library

## Support

For issues related to:
- **This tool**: Check browser console for errors
- **maDMP Standard**: See [RDA-DMP-Common-Standard](https://github.com/RDA-DMP-Common/RDA-DMP-Common-Standard)
- **API Issues**: Contact your API provider

## Changelog

### Version 2.0.0 (2025)
- **Search & Filter**: Real-time search across all changes with type filtering
- **Navigation Controls**: Next/previous change navigation with keyboard shortcuts
- **Session Management**: Save, load, and manage comparison sessions with history
- **Multiple Export Formats**: Added HTML, PDF, CSV, and Markdown exports
- **Keyboard Shortcuts**: Comprehensive keyboard navigation system
- **Enhanced UI**: Improved visual highlighting, collapsible sections, bookmarks
- **Performance**: Optimized rendering for large diffs
- **Documentation**: Comprehensive README with feature guide

### Version 1.0.0 (2025)
- Initial release
- Full maDMP v1.2 validation
- Four diff visualization formats
- API integration
- Dark mode support
- Export/import functionality

---

**Made with ❤️ for the research data management community**
