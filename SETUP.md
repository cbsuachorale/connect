# CBSUA Chorale – Clarions of Isarog (Chorale Connect)

A static website (single `index.html`). No build step.

## Deploy
1. Upload every file in this folder to a GitHub repository (the root must contain `index.html`).
2. In Vercel: **Add New → Project → Import** the repository. Framework preset: **Other**. Leave build command and output directory empty. Click **Deploy**.

## IMPORTANT – make sign-ups work across devices
Until you add Firebase, each visitor's browser keeps its own private data. A member who signs up on one phone
will NOT exist on another device. To share members, posts, announcements and music sheets with everyone:

1. Go to https://console.firebase.google.com → create a project (free Spark plan is enough).
2. Build → **Firestore Database** → Create database (production mode, any region).
3. Firestore → **Rules** → paste the contents of `firestore.rules` → Publish.
4. Project settings → General → Your apps → add a **Web app** → copy the `firebaseConfig` values.
5. Open `index.html`, find `const FIREBASE_CONFIG = null;` and replace it with:
   ```js
   const FIREBASE_CONFIG = { apiKey:"...", authDomain:"...", projectId:"...", storageBucket:"...", messagingSenderId:"...", appId:"..." };
   ```
6. Commit and push; Vercel redeploys automatically.

The Admin page shows **Cloud sync ON** when it works.

## Access
- Visitors: Home (general information) and the Audition Form only.
- Members and alumni (after sign up): Overview, History, Constituents, CBSUA Chorale Center, Chorale Connect, Announcements, Music Sheets, Profile.
- Administrator (cbsuachorale.calabanga@cbsua.edu.ph): can edit the Overview and History pages (Edit page button), post announcements, upload music sheets, and remove members or posts.

## Security note
Login is handled in the browser (hashed passwords, no email verification). It is suitable for a community portal,
not for sensitive data. Anyone with a CBSUA email can sign up. The admin can remove any member under Admin → Members.
