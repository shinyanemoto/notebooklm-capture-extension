# NotebookLM Capture Extension

Chrome extension (Manifest v3) + Google Apps Script.

## Goal
- Capture selected text from a web page
- Append it to a Google Docs document in Google Drive (Workspace)
- Use the document as a source in NotebookLM

## Architecture
Chrome Extension → GAS Web App (POST) → Google Docs → NotebookLM

## Repository plan
- `src/` : extension files (background, content, popup)
- `gas/` : Apps Script (doPost) and deployment notes
- `SPEC.md` : requirements & API contract

## Notes
This repo should remain within Google services where possible (Docs/Drive/NotebookLM/Apps Script).
