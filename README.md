# Advanced Web Development Frameworks — Practical 8
## Lazy Loading and Performance Optimization (React + Vite)

- **Student Name**: Mihir Rathod
- **Student ID**: 24CS087
- **Course**: Advanced Web Development Frameworks (AWDF)
- **Repository**: [AWDF_Prac8_24CS087](https://github.com/Mihir-rathod-hub/AWDF_Prac8_24CS087.git)

---

## Overview

This repository contains the complete implementation of **Practical 8: Lazy Loading and Performance Optimization**. The application leverages modern React performance features—including dynamic code splitting with `React.lazy()` and asynchronous boundary handling with `<Suspense>`—to minimize initial bundle sizes and optimize time-to-interactive for route navigation.

---

## Key Features Implemented

### 1. Route-Based Code Splitting with `React.lazy()`
- Replaced monolithic eager page imports with on-demand dynamic imports for secondary routes:
  ```javascript
  const Projects = React.lazy(() => import('./components/Projects'));
  const Contact = React.lazy(() => import('./components/Contact'));
  ```
- Separates heavy components (`Projects` with GitHub API listing and `Contact` with interactive preview forms) into distinct JavaScript chunks loaded only when the user visits those routes.

### 2. Asynchronous Boundary Handling with `<Suspense>`
- Wrapped client-side `<Routes>` in `<Suspense fallback={<Spinner message="Loading..." />}>`.
- Renders an accessible, theme-styled loading indicator while lazy route chunks are downloaded asynchronously over the network.

### 3. Build & Bundle Optimization
- Production build via Vite splits code into discrete asset chunks:
  - `Contact-[hash].js` (~2.6 kB)
  - `Projects-[hash].js` (~4.3 kB)
  - Core vendor/index bundle (~295 kB)
- Prevents unused code from blocking initial page load on the Home and Task Manager views.

### 4. Preserved Application Capabilities
- **Full-Stack Task Manager**: Complete CRUD operations, real-time status filtering (`All`, `Pending`, `Completed`), instant text search, priority indicators, and accessible deletion modal.
- **Authentication**: JWT token management, persistent sessions, clean login and registration interfaces.
- **Responsive Layout**: Theme switcher (Light/Dark mode), navigation bar, and accessible UI components.

---

## Project Structure

```
AWDF_Prac8_24CS087/
├── public/                 # Static assets (favicons, SVG icons)
├── src/
│   ├── assets/             # Images and logos
│   ├── components/         # Reusable UI & Page components
│   │   ├── About.jsx       # Student profile & about section
│   │   ├── AuthCard.jsx    # Authentication card (Sign In & Create Account)
│   │   ├── AuthModal.jsx   # Modal container for authentication
│   │   ├── ConfirmModal.jsx# Accessible confirmation dialog
│   │   ├── Contact.jsx     # Contact form (Lazy loaded)
│   │   ├── ErrorMessage.jsx# Reusable error alert
│   │   ├── Footer.jsx      # Application footer
│   │   ├── Header.jsx      # Hero header component
│   │   ├── Home.jsx        # Landing page layout
│   │   ├── NavBar.jsx      # Navigation bar with theme toggle
│   │   ├── NotFound.jsx    # 404 Route fallback
│   │   ├── Projects.jsx    # GitHub Repositories view (Lazy loaded)
│   │   ├── RepoList.jsx    # Repository cards list
│   │   ├── Skills.jsx      # Technical skills matrix
│   │   ├── Spinner.jsx     # Loading spinner fallback for Suspense
│   │   ├── TaskForm.jsx    # Task creation & editing form
│   │   ├── TaskItem.jsx    # Individual task card
│   │   ├── TaskManager.jsx # Full-stack task management workspace
│   │   └── Toast.jsx       # Feedback notifications
│   ├── context/            # AuthContext & useAuth hook
│   ├── services/           # authService.js & taskService.js
│   ├── App.css             # Component styling & design tokens
│   ├── App.jsx             # React.lazy() routes & Suspense boundary
│   ├── index.css           # Global reset & CSS custom properties
│   └── main.jsx            # Application entry point
├── .gitignore              # Excluded files & directories
├── .oxlintrc.json          # Oxlint linter configuration
├── index.html              # HTML5 template
├── package.json            # Scripts & project dependencies
├── package-lock.json       # Deterministic dependency lockfile
├── README.md               # Practical 8 documentation
└── vite.config.js          # Vite build & development proxy configuration
```

---

## Getting Started

### Prerequisites
- Node.js (v18+)
- npm (v9+)

### Installation
```bash
npm install
```

### Development Server
```bash
npm run dev
# Application runs on http://localhost:5173
```

### Production Build
```bash
npm run build
# Compiles optimized, code-split assets into dist/
```

### Code Quality & Linting
```bash
npm run lint
# Runs oxlint across all source files
```
