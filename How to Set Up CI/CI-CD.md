# What is CI/CD?

**CI/CD = Continuous Integration + Continuous Delivery (or Deployment)**

It’s a way to **automatically build, test, and deploy code** whenever developers make changes.

Instead of:

> Write code → Manually test → Manually deploy → Hope it works 😅

You do:

> Write code → Push to Git → Everything runs automatically ✅

---

# 🧩 Part 1: Continuous Integration (CI)

### 🔹 What it means

Every time you push code:

- It automatically builds
    
- Runs tests
    
- Checks for errors
    
- Makes sure nothing is broken
    

### 🔹 Why it exists

When multiple developers work together:

- Code can conflict
    
- One change can break another feature
    

CI catches problems **early**.

---

### 🛠 Example (React App like yours)

You push code to GitHub.

CI automatically:

1. Installs dependencies
    
2. Builds the React app
    
3. Runs tests
    
4. Runs lint checks
    
5. Fails if something is broken
    

If tests fail → merge is blocked ❌  
If tests pass → ready to ship ✅

---

# 🚚 Part 2: Continuous Delivery (CD)

After CI passes:

### Continuous Delivery

- The app is automatically prepared for release
    
- But **you manually approve** deployment
    

### Continuous Deployment

- It automatically deploys to production
    
- No manual approval needed
    

---

# 🏗 Full CI/CD Flow

Developer writes code  
        ↓  
Push to GitHub  
        ↓  
CI runs (build + test)  
        ↓  
If success →  
        ↓  
CD deploys to:  
   - Staging  
   - Production

---

# 🧠 Real-World Example

Let’s say you're working on your React Query + form refactor.

You push code.

CI:

- Runs ESLint
    
- Runs unit tests
    
- Builds app
    
- Ensures no TypeScript errors
    

CD:

- Deploys to staging
    
- Or deploys directly to production
    

You don’t manually upload anything.

---

# 🛠 Popular CI/CD Tools

### CI Tools

- GitHub Actions
    
- GitLab CI
    
- CircleCI
    
- Jenkins
    

### CD / Deployment Platforms

- Vercel
    
- Netlify
    
- AWS
    
- Azure
    
- Docker + Kubernetes
    

---

# 🧱 Simple GitHub Actions Example

name: CI  
  
on:  
  push:  
    branches: [main]  
  
jobs:  
  build:  
    runs-on: ubuntu-latest  
      
    steps:  
      - uses: actions/checkout@v3  
        
      - name: Install dependencies  
        run: npm install  
          
      - name: Run tests  
        run: npm test  
          
      - name: Build  
        run: npm run build

This runs automatically every time you push.

---

# 🎯 Why CI/CD Is Important

Without CI/CD:

- Manual testing
    
- Manual deployments
    
- More bugs
    
- Slower releases
    

With CI/CD:

- Faster releases
    
- Safer changes
    
- Fewer production bugs
    
- Better teamwork
    

---

# 🔥 Simple Analogy

Think of CI/CD like a **factory assembly line**:

You add a new part (code change) →  
Machines automatically test it →  
If it passes quality check →  
It gets shipped to customers.

---

# 🧑‍💻 Why You Should Care (Especially As a Dev)

As someone working with:

- React
    
- Forms
    
- Shared components
    
- Refactors
    

CI/CD:

- Prevents breaking old flows
    
- Ensures validation logic still works
    
- Protects production

1. [[How to Set Up CI/CD for a React Project]]
2. [[CD Works With Docker]]