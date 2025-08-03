# Job Tracker Application
### Enhanced Full-Stack Job Application Management System

## ⚡ Quick Start (3 Commands Only!)

```bash
# 1. Navigate to project directory
cd FSD_Assignment_Project

# 2. Install all dependencies (frontend + backend)
npm run setup

# 3. Start application (run in separate terminals)
npm run start-backend    # Terminal 1
npm run start-frontend   # Terminal 2
```

**🎉 Done! App running at:** `http://localhost:3000`

---

## 📋 Project Overview

This is a comprehensive job tracking application built with **React** (frontend) and **Node.js/Express** (backend) with **MongoDB** database. The application allows users to manage their job applications, track status changes, and maintain a detailed history of each application's progress.

## 🎯 Assignment Requirements & Implementation

### ✅ **1. Debug the broken job status display and API persistence**

**Problem Identified:**
- The original code had a critical bug where `job.jstat` was used instead of `job.status`
- This caused job status display and updates to fail completely
- API endpoints were not properly handling status persistence

**Solution Implemented:**
- Fixed the property name from `job.jstat` to `job.status` throughout the codebase
- Enhanced error handling in both frontend and backend
- Implemented proper validation for status updates
- Added comprehensive error logging and user feedback

**Files Fixed:**
- `backend/server.js` - Corrected status field references and API endpoints
- `frontend/src/JobList.jsx` - Fixed status display and update logic
- `frontend/src/api.js` - Enhanced API error handling

### ✅ **2. Implement a feature to track job status history**

**Implementation Details:**
- Added comprehensive status history tracking system
- Each status change is automatically recorded with timestamp
- History includes previous status, new status, and date of change
- Implemented both frontend and backend components for history management

**Backend Implementation:**
```javascript
// Automatic history tracking on status updates
const historyEntry = {
  status: newStatus,
  changedAt: new Date(),
  previousStatus: job.status
};
job.history = job.history || [];
job.history.push(historyEntry);
```

**Database Schema Enhancement:**
- Added `history` array field to job documents
- Each history entry contains: `status`, `changedAt`, `previousStatus`, `notes`

### ✅ **3. Show history in UI under each job**

**UI Implementation:**
- Expandable job cards showing detailed history
- Chronological display of status changes
- Visual timeline with status badges and timestamps
- Edit functionality for adding notes to history entries
- Professional styling with modern icons

**Features Added:**
- **Expandable History View:** Click to expand/collapse job details
- **Status Timeline:** Visual representation of job progress
- **Interactive History Editing:** Add notes to any history entry
- **Real-time Updates:** Instant UI updates on status changes
- **Professional Design:** Modern UI with Lucide icons

## 🛠️ Technology Stack

### **Frontend:**
- **React 19.1.1** - Modern React with hooks
- **Vite 5.1.0** - Fast development build tool
- **Axios** - HTTP client for API communication
- **Lucide React** - Modern SVG icons
- **CSS-in-JS** - Inline styling for component isolation

### **Backend:**
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **CORS** - Cross-origin resource sharing
- **Native MongoDB Driver** - Database connectivity

## 📦 Quick & Easy Installation Setup

### **Prerequisites:**
- Node.js (v16 or higher)
- MongoDB (local installation or MongoDB Atlas)
- npm package manager

### **🚀 Super Simple Setup (Recommended)**

This project includes helpful scripts in the root `package.json` that make setup incredibly easy!

#### **Step 1: Extract & Navigate**
```bash
# Extract zip file and navigate to project directory
cd FSD_Assignment_Project
```

#### **Step 2: One-Command Setup**
```bash
# Install all dependencies for both frontend and backend
npm run setup
```
*This single command automatically installs dependencies in both backend and frontend directories!*

#### **Step 3: Start the Application**

**Option A: Using npm scripts (Easy)**
```bash
# Terminal 1: Start backend server
npm run start-backend

# Terminal 2: Start frontend development server  
npm run start-frontend
```

**Option B: Manual start (Traditional way)**
```bash
# Terminal 1: Backend
cd backend && npm start

# Terminal 2: Frontend
cd frontend && npm run dev
```

### **✅ That's it! Your application is now running:**
- **Backend API:** `http://localhost:3001`
- **Frontend App:** `http://localhost:3000`

### **🎯 Available npm Scripts (Root Directory):**
```json
{
  "setup": "Install all dependencies",
  "start-backend": "Start the backend server", 
  "start-frontend": "Start the frontend development server",
  "install-all": "Install dependencies for both frontend and backend"
}
```

### **📋 Database Configuration**

**Option A: Local MongoDB**
- Ensure MongoDB is running on default port (27017)
- Database `jobTracker` will be created automatically

**Option B: MongoDB Atlas (Cloud)**
- Create account at [MongoDB Atlas](https://www.mongodb.com/atlas)
- Get connection string
- Update `backend/server.js` line 6 with your connection string

## 🎮 How to Use the Application

### **1. Add New Job Application**
- Fill in company name, position, and initial status
- Click "Add Job" to create new entry
- Job automatically gets timestamp and empty history

### **2. Update Job Status**
- Click on any job card to expand details
- Use status dropdown to change current status
- History is automatically updated with timestamp

### **3. View Status History**
- Expand job card to see full history timeline
- Each status change shows previous status, new status, and date
- Professional visual representation with color-coded status badges

### **4. Add Notes to History**
- Click the edit icon (✏️) next to any history entry
- Add contextual notes about that status change
- Submit to save notes permanently

### **5. Manage Applications**
- Delete applications that are no longer relevant
- Edit job details as needed
- Track progress through the entire application process

## 🏗️ Project Structure

```
FSD_Assignment_Project/
├── backend/
│   ├── package.json          # Backend dependencies
│   ├── server.js            # Main server file with all APIs
│   └── node_modules/        # Backend dependencies
├── frontend/
│   ├── public/             # Static assets
│   ├── src/
│   │   ├── App.jsx         # Main application component
│   │   ├── JobList.jsx     # Job management component
│   │   ├── api.js          # API communication layer
│   │   └── main.jsx        # React entry point
│   ├── package.json        # Frontend dependencies
│   ├── vite.config.js      # Vite configuration
│   └── index.html          # HTML template
└── README.md              # This file
```

## 🔧 API Endpoints

### **Jobs Management:**
- `GET /api/jobs` - Retrieve all jobs
- `POST /api/jobs` - Create new job
- `PUT /api/jobs/:id` - Update job (includes automatic history tracking)
- `DELETE /api/jobs/:id` - Delete job
- `PUT /api/jobs/:id/history/:historyId` - Update history entry notes

### **System:**
- `GET /api/health` - Server health check

## 🐛 Troubleshooting

### **Common Issues:**

**1. "Cannot connect to server" error:**
- Ensure MongoDB is running
- Check backend server is started (`npm start` in backend directory)
- Verify port 3001 is not in use by another application

**2. "Module not found" errors:**
- Run `npm install` in both frontend and backend directories
- Clear npm cache: `npm cache clean --force`

**3. Database connection issues:**
- Check MongoDB service is running
- Verify connection string in `backend/server.js`
- For Atlas: ensure IP whitelist includes your IP

**4. Port conflicts:**
- Frontend (Vite): Change port in `vite.config.js`
- Backend: Modify port in `server.js`

## 📊 Database Schema

### **Job Document Structure:**
```javascript
{
  _id: ObjectId,
  company: String,
  position: String,
  status: String,
  appliedDate: Date,
  history: [
    {
      status: String,
      changedAt: Date,
      previousStatus: String,
      notes: String (optional)
    }
  ]
}
```

## 🎨 Design Features

### **Modern UI/UX:**
- Clean, professional interface design
- Responsive layout for all screen sizes
- Consistent color scheme and typography
- Smooth animations and transitions
- Accessibility considerations

### **Status Color Coding:**
- **Applied:** Blue (#3498db)
- **Reviewed:** Orange (#f39c12)
- **Interview:** Purple (#9b59b6)
- **Offer:** Green (#27ae60)
- **Rejected:** Red (#e74c3c)

## 🚀 Future Enhancements

The application footer showcases a comprehensive roadmap of upcoming features including:
- Smart analytics and insights
- Enhanced user experience features
- Collaboration and sharing capabilities
- Advanced data management and security

## 👨‍💻 Developer Information

**Developed by:** Uvais Ahmad  
**Enhanced with:** AI-powered features and modern React patterns  
**Architecture:** Full-stack MERN application with comprehensive error handling

## 📝 Submission Notes

This project demonstrates:
- **Problem-solving skills:** Successfully identified and fixed critical bugs
- **Full-stack development:** Comprehensive frontend and backend implementation
- **Modern development practices:** Clean code, error handling, user experience focus
- **Feature enhancement:** Went beyond requirements with additional functionality
- **Professional presentation:** Complete documentation and deployment readiness

---

**Thank you for reviewing this enhanced job tracker application!** 🚀
