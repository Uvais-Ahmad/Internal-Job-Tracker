# Vercel Deployment Guide for Job Tracker

## 🚀 Quick Deployment Steps

### 1. Setup MongoDB Atlas (Free Database)
1. Go to [MongoDB Atlas](https://www.mongodb.com/atlas)
2. Create free account and cluster
3. Get connection string (looks like): 
   ```
   mongodb+srv://username:password@cluster.mongodb.net/jobtracker
   ```

### 2. Deploy to Vercel
1. **Push to GitHub** (if not already done):
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/Uvais-Ahmad/Internal-Job-Tracker.git
   git push -u origin main
   ```

2. **Deploy on Vercel**:
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub account
   - Click "New Project"
   - Import your GitHub repository
   - Configure:
     - **Framework**: Other
     - **Root Directory**: Leave empty
     - **Build Command**: `npm run vercel-build`
     - **Output Directory**: `frontend/dist`

### 3. Environment Variables in Vercel
Add in Vercel Dashboard → Settings → Environment Variables:
```
MONGODB_URI = mongodb+srv://username:password@cluster.mongodb.net/jobtracker
NODE_ENV = production
```

### 4. Your Live URLs
- **Frontend**: `https://your-project.vercel.app`
- **API**: `https://your-project.vercel.app/api/health`

## 🔧 Files Configured for Deployment
- ✅ `vercel.json` - Vercel configuration
- ✅ `frontend/src/api.js` - Dynamic API URLs
- ✅ `backend/server.js` - Environment variables & Vercel export
- ✅ Build scripts in package.json files

## 🎯 After Deployment
Your app will be live at: `https://your-project-name.vercel.app`

Test the deployment:
1. Visit the URL
2. Add a test job
3. Update status to verify API works
4. Check history functionality
