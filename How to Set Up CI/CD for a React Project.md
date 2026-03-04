🟢 STEP 1 — How to Set Up CI/CD for a React Project (Beginner Friendly)
We’ll use:

- React app
    
- GitHub
    
- GitHub Actions (free CI/CD tool)
    

No Docker yet. Keep it simple first.

---

🧱 What We Are Building

When you push code to GitHub:

1. It installs dependencies
    
2. Runs tests
    
3. Builds your React app
    
4. Fails if something is broken
    

That’s CI.

---

🛠 Step 1 — Create a React App (If You Don’t Have One)

npx create-react-app my-app  
cd my-app

Push it to GitHub.

---

🛠 Step 2 — Create GitHub Actions Workflow

Inside your project create this folder:

.github/workflows/

Inside that folder create:

ci.yml

Full path:

.github/workflows/ci.yml

---

🛠 Step 3 — Add This Code

name: React CI  
  
on:  
  push:  
    branches: [main]  
  
jobs:  
  build:  
    runs-on: ubuntu-latest  
  
    steps:  
      - name: Checkout code  
        uses: actions/checkout@v3  
  
      - name: Install dependencies  
        run: npm install  
  
      - name: Run tests  
        run: npm test -- --watchAll=false  
  
      - name: Build project  
        run: npm run build

---

🧠 What This Means (Very Simple)

When you push to `main` branch:

GitHub:

- Creates a virtual machine
    
- Downloads your code
    
- Runs npm install
    
- Runs tests
    
- Builds your app
    

If something fails → ❌ build fails  
If everything works → ✅ green check

---

🧪 What Happens If You Break Something?

Example:

const x = ;

Push it.

GitHub will:

- Try to build
    
- Crash
    
- Show red ❌
    

You fix it → push again → green ✅

This protects production.

---

🎯 That’s Basic CI

Now your project automatically checks:

- Build errors
    
- Test failures
    
- Broken code
    

---

🟡 OPTIONAL — Add Auto Deploy (Simple CD)

If using Vercel:

Just connect GitHub to Vercel.

Every push:

- CI runs
    
- Vercel automatically deploys
    

That’s CI + CD.

You didn’t upload anything manually.

---

🔥 Real Understanding

Before CI:

> “It works on my machine”

After CI:

> “It works on EVERY machine”

That’s the power.

---

🧠 Quick Recap

CI = automatic testing & building  
CD = automatic deployment

You now understand basic CI setup.