# Terms Matching Tool - AI Development Guide

## Project Overview
A browser-based educational drag-and-drop matching game for key terms and definitions. Students select topics from multiple specifications and match terms to definitions with instant feedback.

## Architecture
- **Single-file application**: Complete solution in `index.html` with embedded CSS/JS
- **Data source**: CSV files hosted on GitHub, loaded via fetch API
- **No build process**: Direct browser execution, no dependencies

## Data Structure & Configuration

### CSV Format (Critical Pattern)
```csv
"Specification Code","Specification Name"
"Topic Code","Topic Name" 
"Term","Definition"
"Term","Definition"
...
```

**Line 1**: Specification metadata  
**Line 2**: Topic metadata  
**Lines 3+**: Term-definition pairs

### GitHub Configuration
Update these constants in the `<script>` section:
- `GITHUB_USERNAME`: Repository owner
- `GITHUB_REPO`: Repository name
- `specificationFolders`: Maps folder names to CSV file arrays

### File Organization
```
/
├── index.html                 # Main application
├── {SPEC_FOLDER}/            # e.g., "1CP2", "7517"
│   ├── topic1.csv
│   └── topic2.csv
```

## Key Behavioral Patterns

### Specification Loading
1. Reads first CSV from each folder in `specificationFolders` to extract spec metadata
2. Populates specification selection grid with codes and descriptions
3. Loads topic CSVs on-demand when specification selected

### Game Mechanics
- **One-strike rule**: Single incorrect match resets entire game
- **Drag validation**: Only allows cross-type drops (term→definition, definition→term)
- **Visual feedback**: Green pulse for correct, red shake + reset for incorrect
- **Success state**: Copy-to-clipboard functionality when all pairs matched

### Modal System
- **Selection modal**: Two-step process (specification → topic)
- **Error popup**: Displays when incorrect match made
- **State management**: Tracks current specification/topic selections

## Development Workflows

### Adding New Topics
1. Create CSV file in appropriate specification folder
2. Add filename to `specificationFolders` configuration
3. Follow exact CSV format with metadata lines

### Adding New Specifications
1. Create new folder with CSV files
2. Add folder mapping to `specificationFolders` object
3. First CSV in folder determines specification metadata

### Testing Locally
- Use local HTTP server (Python: `python -m http.server`)
- Cannot test GitHub CSV loading with file:// protocol
- Use browser dev tools to debug fetch() responses

## Critical Implementation Details

### CSV Parsing Logic
```javascript
const specInfo = lines[0].split(',').map(s => s.trim());  // Specification
const topicInfo = lines[1].split(',').map(s => s.trim());  // Topic
// Terms start at index 2
```

### Drag & Drop System
- Uses HTML5 drag API with custom validation
- `dataset.type` distinguishes 'term' vs 'definition'
- Visual feedback through CSS classes: `dragging`, `drag-over`, `correct`, `incorrect`

### State Management
Global variables track game state:
- `currentSpecification`/`currentTopic`: Selected content
- `currentTermPairs`: Loaded term-definition pairs
- `matchedPairs`: Successfully matched pairs
- `draggedElement`/`draggedType`: Current drag operation

## Styling Conventions
- CSS-in-HTML approach with comprehensive animations
- Gradient themes: `#667eea` to `#764ba2`
- Responsive grid layouts for topic selection
- Animation classes for state transitions (`slideIn`, `fadeIn`, `shake`, etc.)

## External Dependencies
- GitHub raw file API for CSV hosting
- Browser Clipboard API for copy functionality
- No external libraries or frameworks