
Galaxy Dodge — Full Package README
=================================

Included:
- index.html  : The full game (open in browser)
- galaxy_dodge_full_package.zip : This package (same files)
- netlify/functions/submit-score.js : Example Netlify function (Supabase)
- netlify/functions/get-scores.js   : Example Netlify function to retrieve top scores
- capacitor/ : Capacitor config & package.json for building Android APK
- README contains steps to deploy and build.

--- Quick start (play locally) ---
1) Open `index.html` in your browser (double click).
2) Use pointer/touch to control the ship. Tap/click to shoot. Swipe up quickly to boost.
3) Scores are saved locally. Open leaderboard in UI.

--- Remote leaderboard (Supabase + Netlify) ---
1) Create a Supabase project (https://supabase.com) and create a table `scores`:
   - id uuid primary key default gen_random_uuid()
   - name text
   - score int
   - created_at timestamp with time zone default now()

2) Create a Supabase service key (anon or service_role) and note SUPABASE_URL and SUPABASE_KEY.

3) Deploy the provided Netlify functions:
   - In Netlify, create a new site from the repo (or drag & drop).
   - Add environment variables:
       SUPABASE_URL = your supabase url
       SUPABASE_KEY = your supabase anon/service key
   - Deploy the site. The functions are at /.netlify/functions/submit-score and /get-scores

4) On client, call fetch('/.netlify/functions/submit-score', {method:'POST', body: JSON.stringify({name, score})})

--- Building Android APK (Capacitor) ---
Prerequisites: Node.js, npm, Java JDK, Android Studio

1) Unzip the package locally.
2) cd capacitor
3) npm install
4) npx cap init galaxy-dodge com.example.galaxydodge --web-dir=../ (sets web assets to parent root)
5) npx cap add android
6) npx cap copy android
7) Open Android Studio: File -> Open -> capacitor/android
8) Build signed APK or run on device/emulator.

Note: The provided capacitor folder contains package.json and a minimal config to get you started.

--- Deploy to Netlify / Vercel static site ---
- Netlify: connect repo or drag & drop the folder; set build command none, publish directory root (or specify).
- Vercel: create new project and deploy static build. For serverless functions, Netlify is easier in this example.

--- Copyright / Assets ---
I used simple vector primitives for sprites to avoid copyright issues. If you want exact Galaxy Attack assets, you must supply them or confirm acceptable license.

--- Need help? ---
Tell me which step you'd like me to do now:
- Prepare a GitHub repo and push these files (I can output instructions & the git commands)
- Generate Netlify-ready ZIP (already included)
- Help you create Supabase table SQL
- Guide you step-by-step through Capacitor/Android Studio build


Application ID (bundle id) used for this build: com.ali.kacmaz
