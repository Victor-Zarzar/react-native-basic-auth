<h1 align="center" id="header">
  React Native Basic Auth
</h1>
<p align="center">
  <img src="https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React Native">
  <img src="https://img.shields.io/badge/Expo-000020?style=for-the-badge&logo=expo&logoColor=white" alt="Expo">
  <img src="https://img.shields.io/badge/Expo_SDK-55-000020?style=for-the-badge&logo=expo&logoColor=white" alt="Expo SDK 55">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Expo_Router-000000?style=for-the-badge&logo=expo&logoColor=white" alt="Expo Router">
  <img src="https://img.shields.io/badge/NativeWind-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="NativeWind">
  <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/Drizzle-C5F74F?style=for-the-badge&logo=drizzle&logoColor=black" alt="Drizzle ORM">
  <img src="https://img.shields.io/badge/Bun-000000?style=for-the-badge&logo=bun&logoColor=white" alt="Bun">
</p>
<p align="center">
  A <strong>starter boilerplate</strong> for authentication in React Native, built with Expo Router, NativeWind, Drizzle ORM, and SQLite. Includes sign up, sign in, sign out, forgot password, and reset password flows — designed as a solid foundation to build on, not a production-ready solution out of the box.
</p>

> ⚠️ **This is a starting point.** Before shipping to production, review the [Security Considerations](#security-considerations) section below. Several intentional simplifications were made to keep this boilerplate approachable.

---

<h2 id="stack">
  Tech Stack
</h2>
<p>
<img src="https://github.com/tandpfun/skill-icons/blob/main/icons/React-Dark.svg" width="48" title="React Native">
<img src="https://github.com/tandpfun/skill-icons/blob/main/icons/TypeScript.svg" width="48" title="TypeScript">
<img src="https://github.com/tandpfun/skill-icons/blob/main/icons/TailwindCSS-Dark.svg" width="48" title="NativeWind">
<img src="https://github.com/tandpfun/skill-icons/blob/main/icons/SQLite.svg" width="48" title="SQLite">
</p>

---

<h2 id="security-considerations">
  Security Considerations
</h2>

This project is intentionally simplified. Before using it as a base for a real-world app, you should address the following:

### Password Hashing

Passwords are hashed using **`react-native-argon2`** with Argon2id, which is the current recommendation from [OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html) and [RFC 9106](https://www.rfc-editor.org/rfc/rfc9106).

### Other Areas to Improve Before Production

- **Password reset tokens** — currently passed via route params (visible in navigation). Consider storing them only server-side or using a deeper link strategy.
- **Session management** — sessions are stored in SQLite with no expiry. Add a `expiresAt` column and invalidate stale sessions.
- **Input validation** — add stricter password rules (min length, complexity) via Zod schemas.
- **Rate limiting** — no protection against brute-force login attempts exists in a local-first setup; consider adding attempt counters.
- **Token expiry** — reset tokens expire after 15 minutes by default; adjust as needed for your use case.
- **No email verification** — there is no email confirmation step on sign up.
- **Local-only** — this project uses SQLite with no backend. For multi-device or server-side auth, you will need to integrate a backend (e.g., Supabase, Firebase, or a custom API).

---

<h2 id="installation">
  Installation & Setup
</h2>

### 1. Clone the Repository

```bash
git clone https://github.com/Victor-Zarzar/react-native-basic-auth
cd react-native-basic-auth
```

### 2. Install Dependencies

```bash
bun i
```

### 3. Generate Database Migrations

```bash
bun run db:generate
```

### 4. Run the App

```bash
# iOS (native build)
bun run ios:native

# Android (native build)
bun run android:native
```

---

<h2 id="scripts">
  Available Scripts
</h2>

| Script                   | Description                                   |
| ------------------------ | --------------------------------------------- |
| `bun run android`        | Start on Android Emulator                     |
| `bun run ios`            | Start on iOS Simulator                        |
| `bun run web`            | Start on Web                                  |
| `bun run db:generate`    | Generate Drizzle ORM migration files          |
| `bun run upgrade-deps`   | Fix and align dependencies with Expo SDK      |
| `bun run prebuild`       | Rebuild native directories with Expo Prebuild |
| `bun run ios:native`     | Run native iOS build                          |
| `bun run android:native` | Run native Android build                      |
| `bun run lint`           | Check code with Biome                         |
| `bun run lint:fix`       | Auto-fix lint issues with Biome               |
| `bun run format`         | Format code with Biome                        |
| `bun run typecheck`      | Run TypeScript type checking                  |
| `bun test`               | Run tests with Bun                            |

---

<h2 id="core-technologies">
  Core Technologies
</h2>

- **React Native** – Cross-platform mobile framework
- **Expo SDK 55** – Development platform and tooling
- **Expo Router** – File-based routing
- **TypeScript** – Type-safe development
- **NativeWind** – Tailwind CSS for React Native
- **SQLite (Expo SQLite)** – Local persistent storage
- **Drizzle ORM** – Type-safe ORM for SQLite with migration support
- **React Native Argon2** – Argon2id password hashing
- **React Native Reusables** – Accessible UI component system

---

<h2 id="features">
  Key Features
</h2>

- Complete auth flow — Sign Up, Sign In, Sign Out, Forgot Password, Reset Password
- Local data persistence with SQLite via Expo SQLite
- Type-safe database queries with Drizzle ORM
- Drizzle Studio integration via `expo-drizzle-studio-plugin` for database inspection during development
- Password hashing with Argon2id via `react-native-argon2`
- Production-ready scalable structure
- File-based routing with Expo Router
- Dark mode support
- Reusable component system preconfigured
- Edge-to-edge support
- New Architecture enabled (Fabric + TurboModules)
- Cross-platform (iOS, Android, Web)

---

<h2 id="prerequisites">
  Prerequisites
</h2>

Before starting, ensure you have:

- Node.js (v24+)
- npm or Bun
- Expo CLI
- iOS Simulator (Mac) or Android Emulator
- Git

---

<h2 id="database">
  Database & Migrations
</h2>

This project uses **Drizzle ORM** on top of **Expo SQLite** for type-safe, local database operations.

### Generating Migrations

After modifying the schema, run:

```bash
bun run db:generate
```

This will generate SQL migration files inside the `drizzle/` folder using Drizzle Kit.

### Inspecting the Database with Drizzle Studio

With the development server running, press `Shift + M` in the terminal to open the Dev Tools menu, then select **`expo-drizzle-studio-plugin`** from the list. Drizzle Studio will open in a new browser tab, allowing you to browse and manage your local SQLite database visually.

> **Note:** This plugin is available during native development only (iOS/Android). It does not work on Web.

</br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/05dce4c2-72cd-46c9-afb9-d04146848ea2" width="1000" height="600" alt="SQL Drizzle Studio">
</p>

</br>

---

<h2 id="adding-components">
  Adding Components
</h2>

```bash
npx react-native-reusables/cli@latest add input textarea
```

Install all components:

```bash
npx react-native-reusables/cli@latest add --all
```

---

<h2 id="deployment">
  Deployment
</h2>

### Using EAS (Recommended)

```bash
npm install -g eas-cli
eas login
eas build
```

Documentation: https://docs.expo.dev/eas/

---

<h2 id="contributing">
  Contributing
</h2>

1. Fork the project
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

---

<h2 id="license">
  License
</h2>

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<h2 id="author">
  Author
</h2>

Victor Zarzar - [@Victor-Zarzar](https://github.com/Victor-Zarzar)

Project Link: [https://github.com/Victor-Zarzar/react-native-basic-auth](https://github.com/Victor-Zarzar/react-native-basic-auth)

---
