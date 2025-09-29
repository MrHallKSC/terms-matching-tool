# Terms Matching Tool 🎯

An interactive drag-and-drop educational game for matching key terms with their definitions. Perfect for students studying computer science specifications or any subject requiring terminology mastery.

## Features ✨

- **Interactive Drag & Drop**: Intuitive matching interface with visual feedback
- **Multi-Specification Support**: Organize topics by different curricula or subjects
- **One-Strike Challenge**: Incorrect matches reset the game, encouraging careful thinking
- **Progress Tracking**: Visual display of matched pairs with smooth animations
- **Copy to Clipboard**: Export all definitions once completed
- **Responsive Design**: Works on desktop and mobile devices

## Demo 🚀

![Terms Matching Tool Demo](https://via.placeholder.com/600x400/667eea/ffffff?text=Drag+%26+Drop+Interface)

*Students drag terms from the left column to match definitions on the right*

## Quick Start 🏃‍♂️

1. **Clone or download** this repository
2. **Update configuration** in `index.html` (lines 538-540):
   ```javascript
   const GITHUB_USERNAME = 'YourUsername';  // <-- Change this
   const GITHUB_REPO = 'your-repo-name';   // <-- Change this
   ```
3. **Add your CSV files** following the format below
4. **Serve locally** or deploy to any web server

### Local Development
```bash
# Python 3
python -m http.server 8000

# Python 2
python -SimpleHTTPServer 8000

# Node.js (if you have http-server installed)
npx http-server
```

Then visit `http://localhost:8000`

## CSV Data Format 📋

Each topic requires a CSV file with this exact structure:

```csv
"Specification Code","Specification Name"
"Topic Code","Topic Name"
"Term 1","Definition for term 1"
"Term 2","Definition for term 2"
"Term 3","Definition for term 3"
```

### Example: `1CP2/hardware.csv`
```csv
"1CP2","Edexcel Computer Science"
"3.1.1","Hardware"
"CPU","The main part of the computer, consisting of registers, ALU and control unit"
"RAM","Volatile memory used for temporary storage of programs and data"
"Von Neumann architecture","Traditional computer architecture where instructions and data share the same memory"
```

**Important Notes:**
- Line 1: Specification metadata (code, full name)
- Line 2: Topic metadata (code, topic name) 
- Lines 3+: Term-definition pairs
- Use quotes around values containing commas
- Keep definitions concise but complete

## Project Structure 📁

```
terms-matching-tool/
├── index.html              # Complete application (HTML + CSS + JS)
├── README.md              # This file
├── .github/
│   └── copilot-instructions.md
└── 1CP2/                  # Specification folder
    └── 3.1.1_Hardware.csv # Topic CSV file
```

## Adding Content 📝

### New Topics
1. Create CSV file in appropriate specification folder
2. Add filename to `specificationFolders` configuration:
   ```javascript
   const specificationFolders = {
       '1CP2': [
           '3.1.1_Hardware.csv',
           'new_topic.csv'        // Add here
       ]
   };
   ```

### New Specifications
1. Create new folder (e.g., `GCSE-CS/`)
2. Add CSV files following the format
3. Update configuration:
   ```javascript
   const specificationFolders = {
       '1CP2': ['3.1.1_Hardware.csv'],
       'GCSE-CS': ['algorithms.csv', 'networks.csv']  // Add here
   };
   ```

## Game Rules 🎮

1. **Select** your specification and topic from the modal
2. **Drag** terms to their matching definitions (or vice versa)
3. **Correct matches** turn green and move to the "Matched Pairs" section
4. **Incorrect matches** shake red and **reset the entire game**
5. **Complete all matches** to unlock the copy-to-clipboard feature

### Strategy Tips
- Read all terms and definitions first
- Start with the ones you're most confident about
- Remember: one mistake resets everything!

## Customization 🎨

### Styling
The tool uses CSS custom properties for easy theming. Key colors:
- Primary gradient: `#667eea` to `#764ba2`
- Success: `#4CAF50`
- Error: `#f44336`

### Behavior
Modify these variables in the JavaScript section:
- Animation timings
- Drag & drop sensitivity
- Modal behavior
- Success messages

## Browser Support 🌐

- ✅ Chrome/Edge (recommended)
- ✅ Firefox
- ✅ Safari
- ⚠️ Internet Explorer (not supported)

Requires:
- HTML5 Drag and Drop API
- ES6+ JavaScript features
- Fetch API for loading CSV files
- Clipboard API (for copy feature)

## Deployment Options 🚀

### GitHub Pages
1. Push to GitHub repository
2. Enable Pages in repository settings
3. CSV files load automatically from `main` branch

### Static Hosting
Compatible with:
- Netlify
- Vercel
- GitHub Pages
- Any web server

### Local Network
Perfect for classroom use - host on local server for offline access.

## Troubleshooting 🔧

### CSV Files Not Loading
- Check `GITHUB_USERNAME` and `GITHUB_REPO` are correct
- Ensure CSV files are in `main` branch
- Verify file paths match `specificationFolders` configuration
- Use browser dev tools to check network requests

### Drag & Drop Not Working
- Ensure you're not trying to drop terms on terms (or definitions on definitions)
- Check that CSV parsing succeeded (dev tools console)
- Try refreshing the page

### Performance Issues
- Large CSV files (>50 terms) may cause slowdowns
- Consider splitting into smaller topics
- Check for memory leaks in browser dev tools

## Contributing 🤝

1. Fork the repository
2. Create a feature branch
3. Test your changes locally
4. Submit a pull request

### Development Guidelines
- Keep the single-file architecture
- Maintain CSV format compatibility
- Test drag & drop on multiple browsers
- Update this README for new features

## License 📄

MIT License - see repository for full details.

## Support 💬

- Create an issue for bugs or feature requests
- Check existing issues before posting
- Include browser version and steps to reproduce

---

Made with ❤️ for education. Perfect for Computer Science curricula, language learning, or any subject requiring term memorization.