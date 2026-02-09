# HTML-to-Inline-help
# Inline Help Generator (HTML → Clean + IDs + Excel + Cross-References)

## Overview
This project generates inline help sections from a Zendesk-exported HTML developer guide.

It performs the following in one script:
1. Cleans Zendesk-specific HTML wrappers and styles  
2. Adds stable, unique IDs to all headings (h1–h6)  
3. Rewrites cross-reference links so anchors still work after IDs change  
4. Exports all headings with full absolute paths into an Excel file  
5. Generates a JSON file (`headings.json`) for UI integration  
6. Reports broken internal anchor links in a separate Excel sheet  

---

## Output Use Case
In the product UI:
- Each setting/help icon maps to a heading ID (example: `"authentication"`)
- When clicked, the UI loads the cleaned HTML and extracts only that section
- The section is shown as inline help (modal / side panel / tooltip container)

---

## Files

### Input
- `guide.html`  
  Zendesk-exported HTML developer guide

### Output
- `guide.cleaned.html`  
  Clean HTML with stable heading IDs and updated internal links

- `headings.xlsx`  
  Excel index of headings and their full absolute paths

- `headings.json`  
  JSON version of the same heading index (recommended for UI)

---

## Setup (macOS + Homebrew Python)

macOS Homebrew Python blocks system-wide installs by default (PEP 668).  
Use a virtual environment.

### 1) Create and activate venv
```bash
python3 -m venv .venv
source .venv/bin/activate

python -m pip install --upgrade pip
python -m pip install beautifulsoup4 lxml openpyxl

python clean_and_index.py guide.html output/guide.cleaned.html output/headings.xlsx https://docs.example.com/guide.html

## Folder Structure

inline-help-generator/
├── clean_and_index.py
├── guide.html
├── output/
│   ├── guide.cleaned.html
│   ├── headings.xlsx
│   └── headings.json
└── .venv/

### Create a Folder

mkdir inline-help-generator
cd inline-help-generator

- Put your HTML file inside or Copy your Zendesk export here and name it:
`guide.html`





