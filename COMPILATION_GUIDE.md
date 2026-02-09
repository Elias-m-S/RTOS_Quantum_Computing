# LaTeX Compilation Guide

This guide helps you compile the LaTeX template if you're new to LaTeX.

## Option 1: Using Overleaf (Recommended for Beginners)

1. Go to [Overleaf](https://www.overleaf.com/)
2. Create a free account or log in
3. Click "New Project" → "Upload Project"
4. Upload the `quantum_rtos_report.tex` file
5. Create a `figures` folder in Overleaf and upload your figure files
6. Edit the template directly in your browser
7. Click "Recompile" to generate the PDF
8. Download the PDF when done

**Advantages**: No installation needed, works in browser, easy to collaborate

## Option 2: Local Installation

### Windows

1. **Install MiKTeX**:
   - Download from [miktex.org](https://miktex.org/download)
   - Run the installer and follow the prompts
   - Use default settings

2. **Install a LaTeX Editor** (optional but recommended):
   - **TeXstudio**: Download from [texstudio.org](https://www.texstudio.org/)
   - **TeXmaker**: Download from [xm1math.net/texmaker](https://www.xm1math.net/texmaker/)

3. **Compile**:
   - Open `quantum_rtos_report.tex` in your editor
   - Press F5 or click the "Build & View" button
   - Or use command line:
     ```cmd
     pdflatex quantum_rtos_report.tex
     pdflatex quantum_rtos_report.tex
     ```

### macOS

1. **Install MacTeX**:
   ```bash
   # Using Homebrew
   brew install --cask mactex
   
   # Or download from: https://www.tug.org/mactex/
   ```

2. **Install a LaTeX Editor** (optional):
   - **TeXShop** (included with MacTeX)
   - **TeXstudio**: `brew install --cask texstudio`

3. **Compile**:
   ```bash
   pdflatex quantum_rtos_report.tex
   pdflatex quantum_rtos_report.tex
   ```

### Linux (Ubuntu/Debian)

1. **Install TeX Live**:
   ```bash
   sudo apt-get update
   sudo apt-get install texlive-full
   ```

2. **Install a LaTeX Editor** (optional):
   ```bash
   sudo apt-get install texstudio
   ```

3. **Compile**:
   ```bash
   pdflatex quantum_rtos_report.tex
   pdflatex quantum_rtos_report.tex
   ```

## Why Compile Twice?

LaTeX needs to compile twice to:
1. First pass: Generate the document and create auxiliary files
2. Second pass: Resolve cross-references (figure numbers, citations, etc.)

## Using latexmk (Advanced)

For automatic compilation with proper number of passes:

```bash
# Install latexmk (usually included with TeX distributions)
latexmk -pdf quantum_rtos_report.tex

# For continuous compilation (recompiles on file changes)
latexmk -pdf -pvc quantum_rtos_report.tex
```

## Troubleshooting

### Missing Packages Error

If you get an error about missing packages:

**MiKTeX (Windows)**: Should automatically prompt to install missing packages

**TeX Live (Linux/Mac)**:
```bash
# Install the specific package
sudo tlmgr install <package-name>

# Or install common packages
sudo tlmgr install caption float geometry hyperref booktabs
```

### Graphics Path Issues

If figures don't show up:
1. Make sure figure files are in the `figures/` directory
2. Check that filenames match exactly (including case)
3. Use forward slashes in paths: `figures/image.png`

### Compilation Hangs

If compilation seems stuck:
- Press `X` or `Q` to exit
- Check for syntax errors in your LaTeX code
- Look at the `.log` file for error messages

## Generated Files

After compilation, you'll see several new files:
- `quantum_rtos_report.pdf` - **Your final document** ✓
- `quantum_rtos_report.aux` - Auxiliary file for references
- `quantum_rtos_report.log` - Compilation log (useful for debugging)
- `quantum_rtos_report.out` - Hyperref output file

You only need to keep the PDF file.

## Clean Up Auxiliary Files

To clean up auxiliary files after compilation:

```bash
# On Linux/Mac
rm *.aux *.log *.out

# On Windows (Command Prompt)
del *.aux *.log *.out

# Using latexmk
latexmk -c
```

## Getting Help

- [Overleaf Learn](https://www.overleaf.com/learn) - Excellent tutorials
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX) - Comprehensive guide
- [TeX StackExchange](https://tex.stackexchange.com/) - Q&A community
- Check the `.log` file for detailed error messages
