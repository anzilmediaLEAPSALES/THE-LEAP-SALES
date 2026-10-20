# Deploy SalesDesk (free) - public multi-user version

Every visitor can create a free account and gets a PRIVATE workspace (empty at start).
There is also a "Try the demo" button: sample data, no account, nothing saved.

Files: public/index.html (the app) - firestore.rules (privacy rules) - firebase.json (hosting config)

## 1. Firebase console (your project already exists)
1. Build -> Authentication -> Sign-in method:
   - Email/Password -> Enable.
   - Google -> Enable (optional; adds a "Continue with Google" button that works).
   - Settings -> User actions: keep "Enable create (sign-up)" TICKED (this is a public app).
2. Build -> Firestore Database -> Create database (production mode, nearest region).
3. Firestore Database -> Rules tab -> delete everything -> paste the content of firestore.rules -> Publish.
4. Authentication -> Settings -> Authorized domains: *.web.app and *.firebaseapp.com are already there.
   If you host somewhere else (Netlify, GitHub Pages, your own domain), click Add domain and enter it
   without https://  (example: myapp.netlify.app). Login is blocked on any domain not listed.

## 2. Personalise
Open public/index.html in Notepad. At the top, edit:
    window.APP_INFO={name:"SalesDesk",author:"YOUR NAME",url:"https://your-portfolio-or-github"};
This puts "portfolio project by YOUR NAME" in the footer. Rename the app if you like.
If you fork this for another Firebase project, replace the values in window.FIREBASE_CONFIG too.

## 3. Publish (pick one)
A. Netlify Drop (no installs): app.netlify.com/drop -> drag the `public` folder -> create a free account.
B. Cloudflare Pages / GitHub Pages: upload the `public` folder contents.
C. Firebase Hosting (needs Node.js): npm install -g firebase-tools, firebase login,
   firebase use --add, firebase deploy.
Then add that address under Authorized domains (step 1.4) if it is not *.web.app.

## 3b. Install on a phone
Open the link in Chrome (Android) or Safari (iPhone) -> menu -> "Add to Home Screen" / "Install app".
The orange LEAP icon appears on the home screen and the app opens full-screen.

## 4. Test
Open the link -> "Try the demo". Then create an account on your phone and PC and check that the
same data appears on both.

## Limits and honesty notes
- Free Spark plan quotas are shared by ALL users of your project: 50,000 reads and 20,000 writes per
  day, 1 GiB database. Fine for a portfolio and small teams; a very busy app would need to upgrade.
- Each sheet is one record of ~1 MB max (several hundred rows). The app warns if a sheet is too large.
- Users only see their own data (rules enforce it), but as the project owner YOU can open the Firestore
  console and see stored data. Say so in a privacy note if you invite real users, and don't enter
  sensitive personal data in a demo.
- Last write wins if the same account edits the same sheet on two devices at the same moment.
