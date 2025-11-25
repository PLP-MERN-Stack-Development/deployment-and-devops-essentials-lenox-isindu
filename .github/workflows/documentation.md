 Deployment Documentation

 Project Overview

This documentation covers the production deployment of a real-time chat application (PingHub) built with the MERN stack (MongoDB, Express.js, React, Vercel), including CI/CD pipelines, monitoring, and maintenance procedures.

 Live Deployment URL


Environment	URL	Status
Production Frontend	https://real-time-communication-with-socket-io-lenox-isindu.vercel.app/	


Production Backend	https://pinghub-n0zt.onrender.com/


Backend Health Check	https://pinghub-n0zt.onrender.com/api/health	


Database Health Check	https://pinghub-n0zt.onrender.com/api/health/db	




 Deployment Architecture


Component	Technology	Hosting Platform
Frontend	React + Vite	Vercel
Backend	Express.js + Socket.io	Render
Database	MongoDB	MongoDB Atlas
CI/CD	GitHub Actions	GitHub

🔄 CI/CD Pipeline Implementation

Backend CI Pipeline 

Purpose: Validates server syntax, installs dependencies, and ensures the backend can initialize without critical errors.

Frontend CI Pipeline 

Purpose: Installs dependencies, runs linting, and builds the React application to verify production readiness.

Backend CD Pipeline (.github/workflows/deploy-backend.yml)

   
Purpose: Automatically deploys the backend to Render when changes are pushed to the main branch.

Frontend CD Pipeline (.github/workflows/deploy-frontend.yml)

Purpose: Automatically deploys the frontend to Vercel using the Vercel CLI integration .

 Environment Configuration


Backend Environment Variables (Render Dashboard)
env
MONGODB_URI=mongodb+srv://username:passwoed@cluster0.j7ep10i.mongodb.net/db?appName=Cluster0
PORT=5000
CLIENT_URL=frontend url
NODE_ENV=production
Frontend Environment Variables (Vercel Dashboard)
env
VITE_API_URL=backendurl


 Health Monitoring & Security
 
Health Check Endpoints
Basic Health: GET /api/health - Returns server status, uptime, memory usage, and online users

Database Health: GET /api/health/db - Returns MongoDB connection status

Security Implementation
Helmet.js: Secure HTTP headers

Compression: Response compression for performance

Rate Limiting: 1000 requests per 15 minutes per IP

CORS: Configured for production frontend domain

