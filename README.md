# Digital Pathshala 🎓

A modern **learning management system (LMS)** frontend built with React and Vite. Digital Pathshala lets students sign up, sign in, and track their course progress from a clean, responsive dashboard.

> **Demo app** — authentication and course data are powered by a mock API that persists to `localStorage`. No backend is required to run it.

---

## ✨ Features

- 🔐 **Authentication flow** — register, login (email *or* username), and password reset
- 🔑 **Protected routes** — the dashboard is only accessible to signed-in users, with redirect-back support
- ⚡ **Persistent sessions** — a mock JWT-style token keeps you logged in across refreshes (1-hour expiry)
- 📊 **Learning dashboard** — overall progress stats, per-course progress bars, and lesson counts
- 👋 **Google sign-in button** — simulated OAuth flow for demonstration
- 👤 **Session context** — global auth state via React Context (`useAuth`)
- 📱 **Responsive styling** — hand-written CSS with a clean, mobile-friendly layout
- 🧪 **Seeded demo account** — ready to explore on first launch

---

## 🛠 Tech Stack

| Technology | Purpose |
| --- | --- |
| [React 19](https://react.dev/) | UI library |
| [Vite 8](https://vite.dev/) | Dev server & build tool |
| [React Router 7](https://reactrouter.com/) | Client-side routing |
| [ESLint 10](https://eslint.org/) | Linting |
| Plain CSS | Styling |

No UI framework, state library, or backend is used — just React, Context, and the platform.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) 20.19+ or 22.12+
- npm (bundled with Node.js)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Srijana-rai/Digital-Pathshala.git
cd Digital-Pathshala

# 2. Install dependencies
npm install

# 3. Start the dev server
npm run dev
```

Open the URL printed in the terminal (usually <http://localhost:5173>) to view the app.

### Available Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite dev server with hot module replacement |
| `npm run build` | Build the production bundle into `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint over the project |

---

## 🔑 Demo Credentials

A demo student account is seeded automatically on first load:

| Field | Value |
| --- | --- |
| Email | `demo@dplms.com` |
| Username | `demo` |
| Password | `password123` |

You can also click **Continue with Google** to sign in with the simulated Google account, or create a brand-new account via **Register**.

---

## 🗺 Routes

| Path | Page | Access |
| --- | --- | --- |
| `/` | Redirects to `/dashboard` | — |
| `/login` | Sign in | Public |
| `/register` | Create account | Public |
| `/forgot-password` | Request a password reset | Public |
| `/dashboard` | Learning dashboard | 🔒 Protected |

Unauthenticated users visiting `/dashboard` are redirected to `/login` and sent back after signing in.

---

## 📁 Project Structure

```
Digital Pathshala website/
├── public/
│   ├── favicon.svg
│   └── icons.svg
├── src/
│   ├── api/
│   │   └── mockApi.js          # Mock backend: users, auth, courses (localStorage)
│   ├── assets/                 # Images
│   ├── components/
│   │   ├── DashboardLayout.jsx # Top bar + dashboard shell
│   │   ├── GoogleButton.jsx    # Google sign-in button
│   │   ├── Logo.jsx            # Brand logo
│   │   └── ProtectedRoute.jsx  # Route guard
│   ├── context/
│   │   └── AuthContext.jsx     # Global auth state (useAuth)
│   ├── pages/
│   │   ├── Dashboard.jsx       # Progress overview + course cards
│   │   ├── ForgotPassword.jsx
│   │   ├── Login.jsx
│   │   └── Register.jsx
│   ├── App.jsx                 # Routes
│   ├── index.css               # Global styles
│   └── main.jsx                # App entry point
├── index.html
├── eslint.config.js
├── package.json
└── vite.config.js
```

---

## 🧠 How the Mock API Works

`src/api/mockApi.js` simulates a real backend so the UI can be built and demoed without a server:

- **Users** are stored under `dplms_users` and the **session token** under `dplms_session` in `localStorage`.
- The "token" is a base64-encoded JSON payload with a 1-hour expiry — **it is not secure** and exists for demonstration only.
- `mockApi.me()` restores the session on page load; expired tokens are cleared automatically.
- Artificial delays are added so loading states behave like a real network.
- `getCourses()` returns sample course progress data for the dashboard.

When you're ready to connect a real backend, replace the functions in `mockApi.js` with `fetch()` calls — the signatures are designed to stay the same.

---

## ⚠️ Notes & Limitations

- This is a **frontend demo**: passwords are stored in plain text in `localStorage` and the token is not a real JWT. Do not use this auth implementation in production.
- The Google sign-in button is **simulated**; no real OAuth is performed.
- The password-reset flow only shows a confirmation message — no email is sent.
- Course data is static mock data.

---

## 🔮 Possible Next Steps

- Connect a real API (e.g., Node/Express, Supabase, Firebase)
- Integrate real Google OAuth
- Add a course detail page, lesson player, and quiz support
- Persist and display per-user progress
- Add dark mode and richer accessibility features

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to open an issue or submit a pull request.

1. Fork the project
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m "Add amazing feature"`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

No license has been specified for this project yet. If you plan to share it publicly, consider adding one (e.g., the [MIT License](https://opensource.org/licenses/MIT)).

---

<p align="center">Built with ❤️ for learners — <strong>Digital Pathshala</strong></p>
