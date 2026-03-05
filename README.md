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

## 使い方（日本語）

### 1. 前提
- Google Workspace（Drive/Docs/GAS/NotebookLM）が使えること
- Chromeで拡張をローカル読み込みできること

### 2. Google Docs（NotebookLMソース）の準備
- NotebookLMでソースにするGoogle Docsを作成（例: `NotebookLM Source`）
- NotebookLM側にソースとして追加（必要に応じてRefresh）

### 3. Google Apps Script（GAS）の準備
- Google Drive上で新規GASを作成
- `doPost`でJSONを受け取り、対象のGoogle Docsへ追記（SPEC.mdにあるデータ契約に合わせる）
- 追記先のGoogle Docs IDを指定
- Webアプリとしてデプロイしてendpoint URLを取得
  - 会社の運用ルールに合わせたアクセス権設定にする

### 4. Chrome拡張の設定
- GASのendpoint URLを拡張側の設定（config/manifest等）に設定
- Chromeの拡張機能画面で`Developer Mode`をONにし、`src/`を読み込む
- ページ上でテキスト選択→右クリック→「Send to NotebookLM」で送信

### 5. NotebookLMで参照する
- Docsの変更が反映されない場合、NotebookLM側でソースのRefreshを実行する
