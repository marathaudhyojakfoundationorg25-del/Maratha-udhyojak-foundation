```markdown
# Maratha Udhyojak Foundation — Members Website

This is a small static site that lists entrepreneur members and allows authenticated admins to add or delete members. It uses Firebase for storage (Firestore + Storage) and Firebase Authentication (email/password).

Files:
- index.html — UI
- app.js — Firebase + app logic
- styles.css — Styling

## Setup (Firebase)

1. Create a Firebase project at https://console.firebase.google.com/.
2. In Project settings -> General, add a Web App and copy the firebaseConfig object. Replace the placeholder firebaseConfig in app.js.
3. In Firebase Console:
   - Enable Firestore (Datastore mode) and create it (choose a location).
   - Enable Firebase Storage.
   - Enable Authentication -> Sign-in method -> Email/Password.
4. Create an admin user (Authentication -> Users -> Add user) with an email and password. That user will be able to add/delete members.

## Firestore structure

Collection: `members`
Each document:
- name (string)
- business (string, optional)
- bio (string, optional)
- photoURL (string, optional)
- photoPath (string, optional) — storage path for deletion

## Security rules (example)

Example rules are provided in firebase.rules — review and adapt before going to production.

A minimal example:
- Allow reads for everyone.
- Allow writes only for authenticated users.

## Deploying

Option A — GitHub Pages (static)
1. Push these files to your repository root (main branch).
2. In the repository Settings -> Pages, set Source to `main` branch and `/ (root)`.
3. Save; your site will be served at `https://<your-org-or-user>.github.io/<repo-name>/`.

Option B — Netlify/Vercel
- Drag-and-drop, or connect the repo and deploy. They handle HTTPS and fast CDN.

## Notes & next steps

- You may want to restrict writes to a small admin set. For that, add an `admins` collection or custom claims for admin accounts and update Firestore rules accordingly.
- For production, tighten Security Rules for Storage and Firestore (e.g., allow delete only by users with admin claim).
- If you want, an automation can be used to commit these files directly to the repo and enable Pages hosting.
```
