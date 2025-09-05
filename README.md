# 📌 ESLint + Prettier Universal Setup (AntFu Style)

This setup works for **all types of JavaScript/TypeScript projects**:  
✅ Vanilla JavaScript  
✅ React or Others Frame-Work  
✅ TypeScript  
✅ Node.js / Express

It follows **AntFu JavaScript Style Guide** with **Prettier** for formatting.  
Every section is commented — just **uncomment what you need** depending on the project.

---

## 🚀 Installation

```bash
pnpm add -D eslint prettier @antfu/eslint-config
```

---

## ⚙️ Configuration

### 1. `eslint.config.js`

```JavaScript
// eslint.config.js
import antfu from '@antfu/eslint-config';

export default antfu({
  // Your custom rules and overrides can go here.
  // For example, to enable React support:
  // react: true,
  node: true,
  // -------- Core Features --------

  // Enables stylistic rules for formatting.
  // Set to `true` to use Antfu's default style, or an object to customize.
  // Set to `false` to disable all stylistic rules if you only want error checking.

  stylistic: {
    indent: 2,
    quotes: 'single', // Use single quotes of string
    semi: true, // Use semicolons at the end of statements
  },

  // Or to disable a specific rule:
  rules: {
    'no-console': 'warn',
  },

  // For Svelte, Vue, etc., you can enable them here:
  // vue: true,
  // svelte: true,

  // By default, it automatically detects your environment.
  // You can manually specify if needed.
  typescript: true,
  jsonc: true,
  yml: true,

  // ... your other config
  ignores: [
    '**/node_modules/**',
    '**/dist/**',
    '**/build/**',
    '**/coverage/**',
    '**/.next/**',
  ],
});

```

---

### 2. `.prettierrc.json`

```json
{
  "$schema": "https://json.schemastore.org/prettierrc",
  "semi": true,
  "tabWidth": 2,
  "singleQuote": true,
  "printWidth": 80,
  "trailingComma": "all",
  "arrowParens": "avoid"
}
```

---

### 3. `.prettierignore`

```
# .prettierignore

# ==> Dependencies
node_modules/

# ==> Build and Distribution Output
dist/
build/
out/
coverage/
.next/
.nuxt/
.svelte-kit/
.vercel/

# ==> Package lockfiles (to avoid formatting conflicts with package managers)
package-lock.json
yarn.lock
pnpm-lock.yaml

# ==> Logs
logs/
*.log

# ==> Cache files
.prettiercache
.eslintcache
.parcel-cache

# ==> Local Environment Variables
.env
.env.local
```

---

### 4. `.gitignore`

```
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*

# Dependency directories
node_modules/
jspm_packages/

# Build outputs
dist/
build/
.cache/
.next/
out/

# TypeScript cache
*.tsbuildinfo

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# IDEs & Editors
.vscode/
.idea/
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

# Environment variables
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# Coverage & testing
coverage/
*.lcov

# OS files
.DS_Store
Thumbs.db

# Optional: Lock files (if you don’t want them in repo)
# package-lock.json
# yarn.lock
# pnpm-lock.yaml

```

---

### 5. `package.json` Scripts

```jsonc
"scripts": {
  "lint": "eslint .",          // Run ESLint check
  "lint:fix": "eslint . --fix",// Auto-fix ESLint issues
  "format": "prettier --write ." // Format with Prettier
}
```

---

## 🔧 Usage

- **Check linting**

```bash
pnpm lint
```

- **Fix linting automatically**

```bash
pnpm lint:fix
```

- **Format code with Prettier**

```bash
pnpm format
```

---

## 📌 Which parts to use?

- **Vanilla JS project** → Default
- **React project** → Uncomment React rules
- **TypeScript project** → Uncomment TypeScript rules
- **Node/Express project** → Uncomment Node rules

---

✅ Now you have a **single ESLint + Prettier setup** you can use in any project.
