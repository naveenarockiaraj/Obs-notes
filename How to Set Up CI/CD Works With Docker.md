# STEP 2 — How CI/CD Works With Docker (Beginner Friendly)

First, very simple:

# 🐳 What is Docker?

Docker lets you package:

- Your code
    
- Node
    
- Dependencies
    
- Environment
    

Into one container.

Think of Docker like:

📦 A box that contains your entire app  
So it runs the same everywhere.

---

# 🤯 Why Do We Need Docker?

Without Docker:

- Your machine → Node 18
    
- Server → Node 16
    
- Works locally ❌ breaks in production
    

With Docker:

- Same environment everywhere
    
- No "works on my machine" problem
    

---

# 🧱 How Docker Fits Into CI/CD

Normal CI:

Push code → Install deps → Test → Build

CI with Docker:

Push code → Build Docker image → Test inside container → Deploy container

Instead of deploying raw code,  
we deploy a container.

---

# 🛠 Step 1 — Add Docker to React Project

Inside your React project root:

Create file:

Dockerfile

Add this:

# Step 1: Build React app  
FROM node:18 as build  
  
WORKDIR /app  
  
COPY package*.json ./  
RUN npm install  
  
COPY . .  
RUN npm run build  
  
# Step 2: Serve build using nginx  
FROM nginx:alpine  
  
COPY --from=build /app/build /usr/share/nginx/html  
  
EXPOSE 80  
CMD ["nginx", "-g", "daemon off;"]

---

# 🧠 What This Does

Step 1:

- Uses Node 18
    
- Builds React app
    

Step 2:

- Uses nginx
    
- Serves static files
    

Now your React app is production-ready inside a container.

---

# 🛠 Step 2 — Build Docker Image Locally

docker build -t my-react-app .

Run it:

docker run -p 3000:80 my-react-app

Open:

http://localhost:3000

Your app runs inside Docker 🎉

---

# 🟢 Now Add Docker to CI

Update `.github/workflows/ci.yml`

name: React CI with Docker  
  
on:  
  push:  
    branches: [main]  
  
jobs:  
  docker-build:  
    runs-on: ubuntu-latest  
  
    steps:  
      - uses: actions/checkout@v3  
  
      - name: Build Docker image  
        run: docker build -t my-react-app .

Now every push:

- Builds Docker image
    
- Fails if Docker build fails
    

---

# 🚀 Real CI/CD With Docker (Production Style)

Real companies do:

1. Push code
    
2. Build Docker image
    
3. Push image to Docker registry (like Docker Hub or AWS ECR)
    
4. Server pulls image
    
5. Deploy container
    

Flow:

GitHub → Build Image → Push to Registry → Deploy to Server

---

# 🧠 Why Big Companies Use Docker

Because:

- Backend runs in container
    
- Frontend runs in container
    
- Database runs in container
    
- Everything consistent
    
- Easy scaling
    

---

# 🔥 Visual Comparison

Without Docker:

Server setup manually  
Install Node  
Install Nginx  
Copy files  
Pray

With Docker:

docker pull my-app  
docker run my-app  
Done.

---

# 🎯 What You Learned

- Docker packages your app
    
- CI builds Docker image
    
- CD deploys Docker container
    
- Ensures environment consistency
    

You now understand beginner-level Docker + CI/CD 💪