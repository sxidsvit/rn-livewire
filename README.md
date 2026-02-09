# RN Livewire

[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react)](https://react.dev/)
[![React Native](https://img.shields.io/badge/React%20Native-0.81-61DAFB?logo=react)](https://reactnative.dev/)
[![Socket.io](https://img.shields.io/badge/Socket.io-4.8-black?logo=socketdotio)](https://socket.io)

## Project Overview

**RN Livewire** is a full-stack, real-time chat application built with modern web and mobile technologies. It features seamless communication across **web** and **mobile** platforms with instant message delivery, user presence, and Clerk-based authentication. The architecture consists of a robust Node.js backend, a React web client, and a React Native mobile app—all communicating in real-time via WebSockets.

---

## Key Features

- **Real-time Messaging** — Instant message delivery powered by Socket.io
- **Cross-Platform Support** — Native mobile (iOS/Android) and web applications
- **Secure Authentication** — Clerk integration for robust user authentication
- **User Presence** — See who's online and active in real-time
- **Chat Management** — Create, list, and manage conversations
- **Responsive Design** — TailwindCSS styling for modern, accessible UI
- **Type-Safe Development** — Full TypeScript support across all platforms
- **Production Ready** — Configured with Clerk auth, CORS, error handling, and Sentry error tracking

---

## Quick Start

### Prerequisites

Ensure you have the following installed:

- **Bun** (v1.3.4+) — for backend runtime
- **Node.js** (v18+) and **npm/yarn** — for web and mobile development
- **Expo CLI** — for mobile development
- **Git** — for version control

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/sxidsvit/rn-livewire.git
cd rn-livewire
```

#### 2. Backend Setup

```bash
cd backend
bun install
```

Create a `.env` file in the `backend/` directory:

```env
DATABASE_URL=your_mongodb_connection_string
CLERK_WEBHOOK_SECRET=your_clerk_webhook_secret
FRONTEND_URL=http://localhost:5173
```

Start the development server:

```bash
bun run dev
```

The backend will be available at `http://localhost:3000`.

#### 3. Web Application Setup

```bash
cd ../web
npm install
```

Start the development server:

```bash
npm run dev
```

The web app will be available at `http://localhost:5173`.

#### 4. Mobile Application Setup

```bash
cd ../mobile
npm install
```

Start the Expo development server:

```bash
npm start
```

To run on Android:

```bash
npm run android
```

To run on iOS:

```bash
npm run ios
```

---

## Project Structure

```
rn-livewire/
├── backend/               # Express.js + Node.ts API server
│   ├── src/
│   │   ├── app.ts        # Express setup & middleware
│   │   ├── config/       # Database & environment config
│   │   ├── controllers/  # Route handlers
│   │   ├── middleware/   # Auth & error handling
│   │   ├── models/       # MongoDB schemas
│   │   ├── routes/       # API endpoints
│   │   ├── utils/        # Socket.io & helpers
│   │   └── scripts/      # Database seed scripts
│   └── package.json
│
├── web/                   # Vite + React web client
│   ├── src/
│   │   ├── App.jsx       # Main app component
│   │   ├── components/   # Reusable React components
│   │   ├── hooks/        # Custom React hooks
│   │   ├── lib/          # Axios & Socket.io setup
│   │   └── pages/        # Page components
│   └── package.json
│
└── mobile/                # Expo + React Native app
    ├── app/              # Expo Router file-based routing
    ├── components/       # React Native components
    ├── hooks/            # Custom hooks
    ├── lib/              # Socket.io & Axios config
    ├── types/            # TypeScript definitions
    └── package.json
```

---

## Technology Stack

|         Layer         | Technology              | Purpose                      |
| :-------------------: | :---------------------- | :--------------------------- |
|  **Frontend (Web)**   | React 19, Vite          | Fast web application         |
| **Frontend (Mobile)** | React Native 0.81, Expo | Cross-platform mobile app    |
|      **Backend**      | Express 5, Bun          | Lightweight, fast API server |
|     **Database**      | MongoDB, Mongoose       | NoSQL data persistence       |
|     **Real-time**     | Socket.io               | WebSocket communication      |
|  **Authentication**   | Clerk                   | Secure user management       |
|      **Styling**      | TailwindCSS, NativeWind | Utility-first CSS framework  |
| **State Management**  | Zustand                 | Lightweight state management |
|    **HTTP Client**    | Axios                   | Promise-based API requests   |
|  **Error Tracking**   | Sentry                  | Application monitoring       |

---

## API Endpoints

The backend provides the following route groups:

- **Authentication** — `/auth/*` — User login, logout, and session management
- **Chats** — `/chats/*` — Create, list, and manage conversations
- **Messages** — `/messages/*` — Send, retrieve, and manage messages
- **Users** — `/users/*` — User profiles and management

All endpoints require Clerk authentication via middleware.

---

## Environment Variables

### Backend (`.env`)

```env
DATABASE_URL=mongodb+srv://user:password@cluster.mongodb.net/livewire
CLERK_WEBHOOK_SECRET=your_clerk_secret_key
FRONTEND_URL=http://localhost:5173
PORT=3000
```

### Web (`.env.local`)

```env
VITE_API_URL=http://localhost:3000
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_public_key
```

### Mobile (`.env`)

```env
EXPO_PUBLIC_API_URL=http://localhost:3000
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_public_key
```

---

## Development Workflow

### Running All Services Concurrently

You can use a process manager like **concurrently** or start each service in a separate terminal:

**Terminal 1 — Backend:**

```bash
cd backend && bun run dev
```

**Terminal 2 — Web:**

```bash
cd web && npm run dev
```

**Terminal 3 — Mobile:**

```bash
cd mobile && npm start
```

### Building for Production

**Backend:**

```bash
cd backend && bun run build
```

**Web:**

```bash
cd web && npm run build
```

**Mobile:**

```bash
cd mobile && expo build
```

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

For major changes, please open an issue first to discuss what you'd like to change.

---

## Troubleshooting

### Backend Connection Issues

> **Ensure MongoDB is running and the `DATABASE_URL` is correct.** Check that all required environment variables are set.

### WebSocket Connection Failed

> **Verify that the backend is running and accessible.** Check CORS settings in `backend/src/app.ts` to ensure both web and mobile origins are whitelisted.

### Port Already in Use

- Backend (3000): `lsof -i :3000` (macOS/Linux) or `netstat -ano | findstr :3000` (Windows)
- Web (5173): `lsof -i :5173` (macOS/Linux) or `netstat -ano | findstr :5173` (Windows)

---

## Resources

- [Backend Documentation](./backend/README.md)
- [Web Documentation](./web/README.md)
- [Mobile Documentation](./mobile/README.md)
- [Clerk Authentication Docs](https://clerk.com/docs)
- [Socket.io Documentation](https://socket.io/docs/)

---

### 📬 Connect with me

<a href="https://www.linkedin.com/in/sergiy-antonyuk/" target="_blank">
<img alt="Sergiy Antonyuk | LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white" />
</a>

#### 🙏 Acknowledgements

A heartfelt thank you to [Codesistency](https://www.youtube.com/@codesistency/featured) for his invaluable contributions

---

**Built with ❤️ for real-time communication**
