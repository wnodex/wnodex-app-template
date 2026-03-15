# 🚀 wnodex-template

A robust, type-safe, and **package-manager agnostic** server template built with [wnodex](https://github.com/wnodex/wnodex). This template is designed for modern Node.js applications with a focus on developer experience, automation, and seamless production deployment.

## ✨ Features

- **Framework**: Powered by `wnodex` (Express-based).
- **Agnostic Automation**: Scripts detect and work with `pnpm`, `npm`, `yarn`, or `bun` automatically.
- **Git Hooks**: Managed by `lefthook` with local TypeScript scripts for linting and commit validation.
- **Bundling**: High-performance bundling via `esbuild`.
- **Database**: Integrated with `prisma` for type-safe database access.
- **Environment**: Secure variable management with `@dotenvx/dotenvx`.
- **Formatting & Linting**: Pre-configured with ESLint and Prettier.

---

## 🛠️ Global Requirements

While the project manages most dependencies locally, we recommend having the following installed globally for the best experience:

- **Node.js**: v22.0.0 or higher.
- **Package Manager**: [pnpm](https://pnpm.io/) is recommended, but `npm`, `yarn`, or `bun` are fully supported.
- **Global Packages**: We recommend installing these globally for CI/CD and script reliability:
  ```bash
  pnpm add -g lefthook eslint prettier cspell
  ```

---

## 🚀 Getting Started

### 1. Clone and Install

```bash
git clone <your-repo-url>
cd wnodex-app-template
pnpm install # or npm install, etc.
```

### 2. Environment Setup

Create a `.env` file in the root directory:

```bash
DATABASE_URL="postgres://user:password@localhost:5432/db"
NODE_ENV="development"
```

### 3. Initialize Git Hooks

```bash
npx lefthook install
```

---

## 📜 Automation Scripts

The scripts in this template are designed to be **Package Manager Agnostic**. You can run them with your preferred tool.

| Script                       | Description                                                                                 |
| :--------------------------- | :------------------------------------------------------------------------------------------ |
| `pnpm dev`                   | Starts the server in development mode with `tsx` watch.                                     |
| `pnpm build`                 | **Unified Build**: Syncs assets, runs `esbuild`, and generates a production `package.json`. |
| `pnpm sync`                  | Synchronizes client assets from the build directory to the server.                          |
| `pnpm lint:fmt`              | Runs ESLint and Prettier sequentially.                                                      |
| `pnpm prisma:generate`       | Generates the Prisma client based on the schema.                                            |
| `pnpm generate-package-json` | Manually triggers the production `package.json` generation.                                 |

---

## 📂 Project Structure

```text
├── .lefthook/           # Git hook scripts (TypeScript)
├── prisma/              # Database schema and migrations
├── scripts/             # Automation scripts (Agnostic)
│   ├── build.ts         # Main entry for the build pipeline
│   ├── sync.ts          # Asset synchronization logic
│   └── utils/           # Shared utilities (e.g., Pkg Manager detection)
├── src/
│   ├── configs/         # Wnodex and server configurations
│   ├── consts/          # Constants, paths, and environment flags
│   ├── controllers/     # Route handler logic
│   ├── routes/          # Express router definitions
│   └── main.ts          # Application entry point
├── lefthook.yml         # Git hooks configuration
└── tsconfig.json        # TypeScript configuration
```

---

## 📦 Production Deployment

The `pnpm build` command produces a production-ready `dist/` directory.

1. Run the build:
   ```bash
   pnpm build
   ```
2. The `dist` folder will contain:
   - `main.js`: The bundled server.
   - `package.json`: A slimmed-down version for production.
3. Install production dependencies:
   ```bash
   cd dist
   npm install --omit=dev
   ```
4. Start the server:
   ```bash
   node main.js
   ```

---

## 🤝 Contributing

1. Ensure your commit messages follow the **Conventional Commits** specification.
2. The `pre-commit` hook will automatically lint and format your code.

Happy coding with **wnodex**! 🥂

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for more details.
