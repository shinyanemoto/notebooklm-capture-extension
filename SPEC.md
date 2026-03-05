# SPEC (MVP)

## Goal
- Chrome: capture selected text and the current tab URL/title
- Provide a context menu: "Send to NotebookLM"
- Send data via POST to a Google Apps Script web app endpoint
- Append to a Google Docs document (the doc is registered as a NotebookLM source)

## Tech
- Chrome Extension: Manifest v3
- Google Apps Script: Web App (doPost)
- Google Docs + Google Drive
- NotebookLM: reads Google Docs as a source

## Data contract
POST JSON
```json
{
  "title": "...",
  "url": "...",
  "text": "...",
  "ts": "2026-03-05T12:00:00+09:00"
}
```

## Doc append format (example)
```text
2026-03-05 12:00 JST
Title: ...
URL: ...

Text:
...
----
```

## Deliverables
1) manifest.json + minimal extension scaffold
2) background script: create context menu & send payload
3) GAS endpoint: append to a Google Doc
4) README updates as needed
