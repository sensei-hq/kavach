# Kavach

> Focus on what truly matters: crafting exceptional applications. Kavach provides a set of components and utility functions that effortlessly integrate authentication and role-based route protection into your app, without compromising its performance or flexibility.

[![Maintainability](https://qlty.sh/gh/sensei-hq/projects/kavach/maintainability.svg)](https://qlty.sh/gh/sensei-hq/projects/kavach)
[![Code Coverage](https://qlty.sh/gh/sensei-hq/projects/kavach/coverage.svg)](https://qlty.sh/gh/sensei-hq/projects/kavach)
![GitHub last commit](https://img.shields.io/github/last-commit/sensei-hq/kavach)

![kavach](kavach.svg)

## What

Kavach is a drop-in authentication framework for SvelteKit. It provides:

- A unified API across multiple auth platforms
- Declarative route protection
- Pre-built UI components

So you can add secure authentication to your app in minutes, not days.

## Why

- **Platform-agnostic** — Switch between Supabase, Firebase, Auth0, Amplify, or Convex by swapping one adapter
- **Declarative route protection** — Define rules once; no scattered `if (!user)` checks
- **Type-safe** — Full TypeScript support with centralized types
- **Server + Client** — Unified session management across browser and server

## Quick Start

```bash
# Create a SvelteKit project
sv create my-app
cd my-app

# Follow the guided prompts to add Kavach to your project
bunx @kavach/cli init
bun run dev
```

## Supported Adapters

| Provider    | Adapter Package            | Capabilities                 | Status |
| ----------- | -------------------------- | ---------------------------- | ------ |
| Supabase    | `@kavach/adapter-supabase` | Auth, Data, Storage, Logging | ✓      |
| Firebase    | `@kavach/adapter-firebase` | Auth                         | ✓      |
| Auth0       | `@kavach/adapter-auth0`    | Auth                         | ✓      |
| AWS Amplify | `@kavach/adapter-amplify`  | Auth                         | ✓      |
| Convex      | `@kavach/adapter-convex`   | Auth                         | ✓      |

## To Do

- [ ] Data, Storage & Logging to convex and Firebase
- [ ] External storage providers
- [ ] External logger api
- [ ] External data api
- [ ] Mix and match Auth, Data, Storage & Logging (ex Amplify + S3 + Custom Backend)

## Packages

### Core

- [`kavach`](solution/packages/kavach) — Core auth: session management, credential flows, SvelteKit hooks
- [`@kavach/sentry`](solution/packages/sentry) — Role-based route protection (RBAC)

### CLI & Vite

- [`@kavach/cli`](solution/packages/cli) — CLI for scaffolding Kavach into SvelteKit projects
- [`@kavach/vite`](solution/packages/vite) — Vite plugin for code generation

### Utilities

- [`@kavach/logger`](solution/packages/logger) — Structured context-scoped logging
- [`@kavach/cookie`](solution/packages/cookie) — Cookie serialize/deserialize (ESM fork of jshttp/cookie)
- [`@kavach/hashing`](solution/packages/hashing) — MD5 hashing for Gravatar
- [`@kavach/query`](solution/packages/query) — Adapter-agnostic query filter parser

### UI

- [`@kavach/ui`](solution/packages/ui) — Pre-built auth components, cached logins, smart layout

### Adapters

- [`@kavach/adapter-supabase`](solution/adapters/supabase) — Supabase authentication and data operations
- [`@kavach/adapter-firebase`](solution/adapters/firebase) — Firebase authentication
- [`@kavach/adapter-auth0`](solution/adapters/auth0) — Auth0 authentication
- [`@kavach/adapter-amplify`](solution/adapters/amplify) — AWS Amplify authentication
- [`@kavach/adapter-convex`](solution/adapters/convex) — Convex authentication

## Route Configuration

Routes are protected by default. Configure public routes in `kavach.config.js`:

```js
export default {
  routes: {
    public: ['/login', '/register'],
    roles: {
      admin: { home: '/admin' },
      user: { home: '/dashboard' }
    }
  }
}
```

## Learn More

- [Documentation](docs/README.md)
- [Kavach Website](https://kavach.sensei-hq.com)

## License

MIT © [Jerry Thomas](https://github.com/jerrythomas)
