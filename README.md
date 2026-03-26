# Bashige Translate (Ad Edition)

**Bashige Translate** is a lightweight Windows desktop translator built with **Tauri + React**.  
It’s designed to be **simple**, **fast**, and **AI-smart**—a small 4:3 window with a practical toolbar, streaming output, and one-click copy/paste.

## Highlights

- **Simple UI**: compact 4:3 window, minimal controls, no clutter.
- **Efficient workflow**: paste → translate → stream output → copy.
- **AI-smart translation**:
  - **Streaming** output (see text as it’s generated)
  - **Mode control**: Faithful / Balanced / Idiomatic
  - **Auto-detect source language**
- **Safety-focused defaults**:
  - Base URL restricted to **`https://`** (and blocks `localhost` / private IPs)
  - API key is **not saved by default** (“Remember” toggle)
- **Ad footer**: affiliate-style text ad; click opens your browser to a third‑party link.

## Screens / UX

- Top toolbar: **Base URL**, **API Key**, **Remember**, **Model**, **Mode**, **Target**
- Two panes: **Input** / **Output**
- Bottom: **AD** footer (clickable text)

## Requirements

- **Windows 10/11**
- **Microsoft Edge WebView2 Runtime** (often already installed on Win10/11)
- For development/build:
  - **Node.js** (LTS recommended)
  - **Rust toolchain** (`rustup`, stable)
  - Visual Studio Build Tools (MSVC) as required by Tauri on Windows

## Getting Started (Development)

```bash
cd translator-app-ad
npm install
npm run tauri dev
```

## Configuration

This app talks to an **OpenAI-compatible** Chat Completions endpoint:

- **LLM Base URL**: e.g. `https://api.openai.com/v1`
- **API Key**: provider key (Bearer is auto-handled if pasted with prefix)
- **Model ID**: e.g. `gpt-4o-mini` (or your provider’s model name)
- **Mode**:
  - **Faithful**: more literal/precise
  - **Balanced**: default
  - **Idiomatic**: more localized/native phrasing
- **Target**: output language

### Notes on API Key storage

- By default, the key is **not persisted**.
- If you enable **Remember**, the key is stored in the app’s local storage on this device.

## Build (Portable EXE)

```bash
cd translator-app-ad
npm run tauri build
```

Portable executable output:

- `src-tauri/target/release/translator-app.exe`

## Ads / Affiliate Disclosure

This edition includes an **affiliate-style ad footer**:

- Shown as an **AD** label + text.
- Clicking the ad **opens your default browser** to a third-party website:
  - `https://rushtranslate.com/?ref=tianic`

The app does **not** embed third‑party ad scripts/iframes and does **not** send your translation text to the ad link.

## Privacy

- Text you translate is sent to the LLM provider you configured in **Base URL**.
- This project does not intentionally collect analytics/telemetry by default.
- If you enable **Remember**, your API key is stored locally on your machine.

## Troubleshooting

### “HTTP 401 Unauthorized”

- API key is invalid/expired, or the Base URL / model does not match your key/provider.

### Build hangs on WiX download (MSI packaging)

If you only need the **portable EXE**, you can use the already-built:

- `src-tauri/target/release/translator-app.exe`

## License

Choose a license that matches your distribution needs (e.g. MIT / Apache-2.0).  
If you plan to distribute broadly with affiliate links, include clear disclosures in your releases and documentation.
