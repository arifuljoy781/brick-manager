# Brick Business Manager — GitHub Pages + Google Drive

This is a static HTML app. GitHub Pages hosts the app and Google Drive stores each user's application data.

## 1. Create the Google OAuth client

1. Open Google Cloud Console.
2. Create/select a project.
3. Enable **Google Drive API**.
4. Configure **Google Auth Platform / OAuth consent screen**.
5. Create an OAuth 2.0 Client ID with application type **Web application**.
6. Under **Authorized JavaScript origins**, add your GitHub Pages origin. For a project site this is normally:
   `https://YOUR-GITHUB-USERNAME.github.io`
   (Do not add the repository path.)
7. If the OAuth app is **External** and still in testing, add your Google account under **Test users**.
8. Copy the Web Client ID.

Google's browser quickstart explains creating the Web application client and authorized JavaScript origins:
https://developers.google.com/workspace/drive/api/quickstart/js

## 2. Put the Client ID in the app

Open `config.js` and replace:

`YOUR_GOOGLE_CLIENT_ID.apps.googleusercontent.com`

with your actual Web Client ID.

Do not put a client secret in this project. Browser OAuth web apps use the client ID; the client ID is not a password.

## 3. Upload to GitHub

Create a GitHub repository, for example `brick-business-manager`, and upload all files in this folder, including `.github/workflows/pages.yml`.

Commit to the `main` branch.

## 4. Turn on GitHub Pages

In the repository:

**Settings → Pages → Build and deployment → Source: GitHub Actions**

Pushes to `main` will then deploy the site.

## 5. Use the app

Open your GitHub Pages URL and click **Sign in with Google**.

The app uses Google's `drive.appdata` application-data area. Each Google account gets its own cloud data, so signing into the same account on another device loads the same purchases, sales, locations, and reports.

The app does not use localStorage as the primary database. If an older copy has legacy local data, the first successful Google sign-in can migrate it to Drive and then remove the legacy local copy.

## Important

GitHub Pages is static hosting. Never store a Google client secret, service-account key, or other private credential in the repository.

Google Drive app data is private to the application and the user's account.
