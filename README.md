# rn-livewire

A full-stack, real-time chat application with seamless cross-platform support. Connect instantly on mobile (iOS/Android) or web with end-to-end message synchronization and live user presence tracking.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Backend Setup](#backend-setup)
  - [Mobile Setup](#mobile-setup)
  - [Web Setup](#web-setup)
- [Configuration](#configuration)
- [Running Locally](#running-locally)
- [Development](#development)
- [Architecture](#architecture)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## Features

✨ **Real-time Messaging** - WebSocket-powered instant message delivery with live status updates

📱 **Multi-Platform** - Native mobile apps (iOS/Android) and responsive web interface from a single codebase

🔐 **Secure Authentication** - Clerk integration for passwordless authentication and session management

👥 **Online Presence** - See who's online in real-time with instant status updates when users connect/disconnect

💬 **Chat Management** - Create conversations, track message history, and manage participants

🎨 **Modern UI** - Beautiful interfaces with NativeWind (mobile) and Tailwind CSS (web)

📊 **Error Tracking** - Sentry integration for production monitoring and debugging

🚀 **Developer Friendly** - TypeScript throughout, hot reload support, clear architecture separation

## Tech Stack

### Backend

- **Runtime**: [Bun](https://bun.com) - Fast all-in-one JavaScript runtime
- **Framework**: Express.js 5.2
- **Database**: MongoDB with Mongoose ODM
- **Real-time**: Socket.io 4.8
- **Authentication**: Clerk Express
- **Error Tracking**: Sentry

### Mobile

- **Framework**: React Native 0.81 with Expo
- **Routing**: Expo Router
- **State Management**: Zustand, React Query
- **Styling**: NativeWind (Tailwind CSS for React Native)
- **Authentication**: Clerk for React Native
- **UI Components**: Expo Vector Icons

### Web

- **Framework**: React 19 with Vite
- **Styling**: Tailwind CSS 4.1 with DaisyUI
- **Routing**: React Router 7.12
- **State Management**: Zustand, React Query
- **Authentication**: Clerk for React
- **Icons**: Lucide React

### Cross-platform

- **HTTP Client**: Axios
- **Real-time Client**: Socket.io Client
- **Type Safety**: TypeScript

## Project Structure

```
rn-livewire/
├── backend/                    # Express.js server
│   ├── src/
│   │   ├── app.ts             # Express app setup
│   │   ├── config/            # Database configuration
│   │   ├── controllers/       # Request handlers
│   │   ├── middleware/        # Authentication, error handling
│   │   ├── models/            # Mongoose schemas
│   │   ├── routes/            # API routes
│   │   ├── utils/             # Socket.io setup
│   │   └── scripts/           # Database seeding
│   └── index.ts               # Server entry point
│
├── mobile/                     # React Native + Expo
│   ├── app/                   # File-based routing
│   ├── components/            # Reusable components
│   ├── hooks/                 # Custom React hooks
│   ├── lib/                   # Utilities (axios, socket)
│   └── types/                 # TypeScript definitions
│
└── web/                        # React + Vite
    ├── src/
    │   ├── App.jsx            # Main app component
    │   ├── components/        # Reusable components
    │   ├── hooks/             # Custom React hooks
    │   ├── lib/               # Utilities (axios, socket)
    │   └── pages/             # Route pages
    └── index.html
```

## Prerequisites

- **Node.js** 18+ or **Bun** 1.3+
- **npm** or **yarn** or **bun** package manager
- **MongoDB** instance (local or MongoDB Atlas)
- **Clerk account** ([create one here](https://clerk.com))
- **Git**
- For mobile development: Android Studio/Emulator or Xcode/iOS Simulator (optional for web testing)

## Installation

### Backend Setup

1. Navigate to the backend directory:

```bash
cd backend
```

2. Install dependencies using Bun:

```bash
bun install
```

3. Create a `.env` file in the backend directory:

```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/rn-livewire
CLERK_SECRET_KEY=your_clerk_secret_key
FRONTEND_URL=http://localhost:5173
PORT=3000
```

4. Seed the database (optional):

```bash
bun src/scripts/seed.ts
```

### Mobile Setup

1. Navigate to the mobile directory:

```bash
cd mobile
```

2. Install dependencies:

```bash
npm install
```

3. Create an `.env` file in the mobile root:

```env
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
EXPO_PUBLIC_API_URL=http://localhost:3000
EXPO_PUBLIC_SOCKET_URL=http://localhost:3000
```

4. Start the development server:

```bash
npm start
```

### Web Setup

1. Navigate to the web directory:

```bash
cd web
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the web root:

```env
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
VITE_API_URL=http://localhost:3000
VITE_SOCKET_URL=http://localhost:3000
```

4. Start the development server:

```bash
npm run dev
```

## Configuration

### Environment Variables

#### Backend (`backend/.env`)

| Variable           | Description                         | Example                 |
| ------------------ | ----------------------------------- | ----------------------- |
| `MONGODB_URI`      | MongoDB connection string           | `mongodb+srv://...`     |
| `CLERK_SECRET_KEY` | Clerk secret key for authentication | From Clerk dashboard    |
| `FRONTEND_URL`     | Frontend application URL            | `http://localhost:5173` |
| `PORT`             | Server port                         | `3000`                  |

#### Mobile (`mobile/.env`)

| Variable                            | Description           | Example                 |
| ----------------------------------- | --------------------- | ----------------------- |
| `EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY` | Clerk publishable key | From Clerk dashboard    |
| `EXPO_PUBLIC_API_URL`               | Backend API base URL  | `http://localhost:3000` |
| `EXPO_PUBLIC_SOCKET_URL`            | Socket.io server URL  | `http://localhost:3000` |

#### Web (`web/.env`)

| Variable                     | Description           | Example                 |
| ---------------------------- | --------------------- | ----------------------- |
| `VITE_CLERK_PUBLISHABLE_KEY` | Clerk publishable key | From Clerk dashboard    |
| `VITE_API_URL`               | Backend API base URL  | `http://localhost:3000` |
| `VITE_SOCKET_URL`            | Socket.io server URL  | `http://localhost:3000` |

## Running Locally

### Start All Services

1. **Backend** (Terminal 1):

```bash
cd backend
bun run dev
# Server runs at http://localhost:3000
```

2. **Web** (Terminal 2):

```bash
cd web
npm run dev
# Web runs at http://localhost:5173
```

3. **Mobile** (Terminal 3):

```bash
cd mobile
npm start
# Press 'w' for web, 'i' for iOS simulator, 'a' for Android emulator
```

### Test the Application

1. Open the web app at `http://localhost:5173`
2. Sign in with your Clerk credentials
3. Create a new chat or select an existing one
4. Send a message and see real-time updates
5. Open mobile app or another web instance to test real-time synchronization

## Development

### Code Structure

- **Backend**: Controllers handle business logic, routes define endpoints, models define MongoDB schemas, socket handlers manage real-time events
- **Mobile**: Hooks manage state and API calls, components render UI, lib folder contains shared utilities
- **Web**: Pages contain route components, hooks manage state and API calls, components are reusable UI elements

### Key Endpoints

See [backend/README.md](backend/README.md) for detailed API documentation.

### Socket Events

The application uses Socket.io for real-time communication:

- `connection` - User connects to the server
- `online-users` - Receive list of currently online users
- `new-message` - Receive new message from chat
- `disconnect` - User disconnects from the server

### Adding New Features

1. Create database models in `backend/src/models/`
2. Add controllers in `backend/src/controllers/`
3. Define routes in `backend/src/routes/`
4. Add API hooks in `mobile/hooks/` and `web/src/hooks/`
5. Create UI components in `mobile/components/` and `web/src/components/`

## Architecture

### Real-time Communication Flow

```
Mobile/Web Client
    ↓
    ├→ HTTP Requests (Axios) → Backend Express Server
    │                              ↓
    │                         MongoDB Database
    │
    ├→ Socket.io Connection → Backend Socket Server
    ↓                              ↓
Listen for events ←─────── Broadcast events to clients
```

### Authentication Flow

1. User signs up/logs in via Clerk UI
2. Clerk returns an authentication token
3. Token is stored securely (mobile: Expo Secure Store, web: localStorage)
4. Each API request includes the token in headers
5. Socket.io connection authenticated with token in handshake

## Contributing

We welcome contributions! To contribute:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

### Development Guidelines

- Use TypeScript for type safety
- Follow existing code style and patterns
- Write meaningful commit messages
- Test features locally before submitting PRs
- Keep commits atomic and focused

## Support

### Getting Help

- **Issues**: Report bugs or request features via [GitHub Issues](../../issues)
- **Documentation**: Check individual README files in each directory
- **Socket.io Events**: See [backend/src/utils/socket.ts](backend/src/utils/socket.ts)
- **Clerk Docs**: [Clerk Authentication](https://clerk.com/docs)

### Troubleshooting

**Connection Issues**

- Ensure backend is running on the correct port
- Verify environment variables are set correctly
- Check CORS configuration in `backend/src/app.ts`

**Authentication Errors**

- Verify Clerk keys are correct in environment variables
- Check token expiration in Clerk dashboard

**Database Connection**

- Verify MongoDB URI is correct
- Check database credentials
- Ensure network access is allowed (MongoDB Atlas)

## 📬 Connect with me

<a href="https://www.linkedin.com/in/sergiy-antonyuk/" target="_blank">
<img alt="Sergiy Antonyuk | LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white" />
</a>

#### 🙏 Acknowledgements

A heartfelt thank you to [Codesistency](https://www.youtube.com/@codesistency/featured) for his invaluable contributions

**Made with ❤️ by the SxidSvit**
