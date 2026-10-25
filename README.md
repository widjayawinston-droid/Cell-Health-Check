# CellCheck – GitHub Pages ready

Static battery-screening website, converted so GitHub Pages can publish it directly from the **main** branch's **/(root)** directory. No build is needed.

## Upload / publish

1. Extract `CellCheck_GitHub_Pages_Ready.zip` on your computer.
2. Open https://github.com/widjayawinston-droid/Cell_Check and select **Add file → Upload files** (on an empty repository, choose **uploading an existing file**).
3. Upload the **contents** of the extracted folder, not its containing folder and not the ZIP itself. `index.html`, `app.js`, and `styles.css` must appear directly in the repository's main file list.
4. Click **Commit changes**.
5. Open **Settings → Pages → Build and deployment**, select **Deploy from a branch**, branch **main**, folder **/(root)**, and click **Save**.
6. After Pages deployment succeeds, visit https://widjayawinston-droid.github.io/Cell_Check/

**Do not select `/docs`** or upload the files inside an extra `dist` or `cellcheck-detector` folder. A custom domain can be configured later under **Settings → Pages → Custom domain**.

## Local development

Serve the project root from localhost (avoid `file://` when testing ES modules or Web Serial):

```bash
python -m http.server 8000
```

Then open http://localhost:8000. Web Serial requires desktop Chrome/Edge and a secure origin (GitHub Pages HTTPS or localhost).

Run the included automated tests with Node.js:

```bash
npm run check
npm test
```

## Important limitations

- This is a **static frontend**. Demo battery records and test history are stored per browser in local storage; GitHub Pages does not provide a central database or inventory API.
- A separately hosted HTTPS API with suitable CORS configuration is required for shared, persistent inventory across users. See `integration-guide.html`.
- The website **does not switch a physical electrical load**; safety cut-offs must be implemented in firmware/hardware. Battery approval requires qualified review.
- `CellCheckTelemetry.h` is only an Arduino output-format helper. It does not provide a complete measurement or switching circuit.
- Never commit private API tokens, secrets or credential files to a public repository.
