# Alex's PDF Editor

A PDF editor that runs in the browser and syncs through Google Drive. You can edit existing text, add text, whiteout, highlight, draw boxes, freehand drawing, check and X stamps, signatures and images. You can also rotate, reorder, delete or insert pages and join PDFs together.

Live at: https://badzepplinflyer.github.io/pdf-editor/

## How syncing works

- Click **Connect Drive** and sign in with Google once on each device.
- Every PDF you open is saved as you edit. **Recent** lists them on every device.
- In your Google Drive you'll see a **PDF Editor** folder:
  - Finished PDFs from **Save PDF → Save to Google Drive** go directly in that folder.
  - **Working files (used by the editor)** holds your original PDFs and the edit files (`.pdfedit`) the editor needs to reopen a document where you left off. Don't edit these by hand.
- The editor uses the `drive.file` permission, so it can only see files it created. The rest of your Drive is off limits to it.

## One-time Google setup (about 10 minutes)

1. Go to https://console.cloud.google.com/ and create a project named **PDF Editor**.
2. **APIs & Services → Library**: search for **Google Drive API** and click **Enable**.
3. **APIs & Services → OAuth consent screen** (also called "Google Auth Platform"):
   - User type: **External**. App name: **Alex's PDF Editor**. Fill in your email where it asks.
   - Scopes: you can skip this step.
   - **Audience / Test users**: add your own Gmail address. Leave the app in **Testing**.
4. **APIs & Services → Credentials → Create credentials → OAuth client ID**:
   - Application type: **Web application**
   - Authorized JavaScript origins: `https://badzepplinflyer.github.io`
   - No redirect URIs are needed.
5. Copy the **Client ID** (it ends in `.apps.googleusercontent.com`) into `GOOGLE_CLIENT_ID` in `index.html`. (Already done for this repo.)

Because the app stays in Testing, Google may ask you to sign in again about once a week. That's normal for personal apps that aren't verified.

## Turning on GitHub Pages

Repo **Settings → Pages → Build and deployment**: Source **Deploy from a branch**, Branch **main**, folder **/ (root)**, then **Save**. The site is live a minute later.
