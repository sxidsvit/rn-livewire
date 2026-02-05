rn-livewire 💬

rn-livewire is a production-ready full-stack monorepo designed for real-time communication. It features a unified high-performance backend serving both Web (React) and Mobile (React Native/Expo) clients through a seamless integration of REST APIs and WebSockets.

🚀 Key Features

Real-time Messaging: Instant message delivery powered by Socket.io.

Cross-platform Ecosystem: Shared backend infrastructure for iOS, Android, and Web.

Enterprise-grade Auth: Secure user management and session handling via Clerk.

Interactive UI: Live typing indicators and real-time user presence (Online/Offline status).

High Performance: Backend powered by Bun, the fast JavaScript all-in-one toolkit.

Robust Monitoring: Integrated Sentry support for real-time error tracking and performance profiling.

🛠 Tech Stack

Core Backend

Runtime: Bun (High-performance JS runtime)

Framework: Express with TypeScript

Database: MongoDB using Mongoose ODM

Real-time: Socket.io for bi-directional communication

Security: Clerk SDK for JWT verification and route protection

Client Applications

Web: React 18, Vite, and TailwindCSS

Mobile: React Native via Expo (managed workflow)

State Management: React Hooks & Context API

📂 Project Structure

rn-livewire/
├── backend/ # Bun + Express + Socket.io Server
│ ├── src/
│ │ ├── controllers/ # Business logic & Route handlers
│ │ ├── models/ # Mongoose schemas (User, Message, Chat)
│ │ ├── middleware/ # Auth & Error handling layers
│ │ └── utils/ # Socket.IO & Database configurations
├── web/ # React.js Web Application
└── mobile/ # React Native (Expo) Mobile App

⚡ Quick Start

Prerequisites

Bun (Recommended) or Node.js

MongoDB instance (Local or Atlas)

Clerk account for Authentication API keys

1. Installation

Install dependencies for the entire monorepo:

bun install

2. Environment Configuration

Populate the .env files in their respective directories:

backend/.env

MONGODB_URI: Your MongoDB connection string.

CLERK_SECRET_KEY: Your private Clerk key.

FRONTEND_URL: Your web client URL (e.g., http://localhost:5173).

web/.env & mobile/.env

VITE_CLERK_PUBLISHABLE_KEY: Your public Clerk key.

VITE_API_URL: Backend API endpoint (e.g., http://localhost:3000).

3. Running the Application

Component

Command

Backend

cd backend && bun run dev

Web Client

cd web && bun run dev

Mobile App

cd mobile && npx expo start

📡 Architecture Overview

The system implements a Dual Communication Architecture:

REST API: Handles CRUD operations, such as fetching chat history, user profiles, and initial data loading.

WebSockets: Manages low-latency interactions, including message broadcasting, typing status, and presence updates.

🏗 Deployment

The project is Docker-ready. The backend is configured to serve the production build of the web application, allowing you to deploy the entire stack as a single container.

# Build and run using Docker

docker build -t rn-livewire .
docker run -p 3000:3000 rn-livewire

📖 In-depth Documentation

For detailed technical specifications, API endpoint definitions, and architectural diagrams, visit the DeepWiki.

📄 License

This project is licensed under the MIT License. See the LICENSE file for details.

Developed with ❤️ by sxidsvit
