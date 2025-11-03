# Project Structure (2025 Best Practices)

Modern pnpm monorepo structure for the Trello clone project management app.

## Quick Overview

```
project-management-app/
├── apps/
│   ├── client/          # React frontend (Vite + TypeScript)
│   └── server/          # Express backend (Node + TypeScript + Prisma)
│
├── packages/
│   ├── shared-types/    # Common TypeScript types
│   ├── validation/      # Zod schemas (shared validation)
│   ├── config/          # Shared configs (ESLint, TS)
│   └── constants/       # App constants
│
├── tools/               # Build scripts & generators
├── docs/                # Documentation
├── .github/             # CI/CD workflows
│
├── pnpm-workspace.yaml  # Workspace config
└── package.json         # Root package.json
```

## Client App Structure

```
apps/client/
├── src/
│   ├── components/      # React components (Board, List, Card, common, layout)
│   ├── pages/           # Route pages (Dashboard, BoardView, Login, etc.)
│   ├── hooks/           # Custom hooks (useBoards, useCards, useDragAndDrop)
│   ├── lib/             # TanStack Query setup, Zustand stores
│   ├── services/        # API calls (Axios) and Socket.io
│   ├── utils/           # Helper functions
│   └── App.tsx
│
├── package.json
├── vite.config.ts
└── tsconfig.json
```

## Server App Structure

```
apps/server/
├── src/
│   ├── controllers/     # HTTP handlers (Express-dependent)
│   ├── services/        # Business logic (framework-agnostic)
│   ├── repositories/    # Data access (Prisma-dependent)
│   ├── routes/          # API routes
│   ├── middleware/      # Auth, validation, error handling
│   ├── socket/          # WebSocket handlers
│   ├── config/          # Configuration
│   └── server.ts
│
├── prisma/
│   ├── schema.prisma
│   └── migrations/
│
└── package.json
```

## Why This Structure?

### Monorepo Benefits
- **Code sharing**: Types and validation shared between client/server
- **Single source of truth**: One repo, consistent versioning
- **Efficient**: pnpm workspaces with symlinks, fast installs

### Layered Backend (Controllers → Services → Repositories)
- **Controllers**: Handle HTTP requests/responses (thin layer)
- **Services**: Core business logic (portable, testable)
- **Repositories**: Database operations with Prisma

This separation means you can swap Express for Fastify/NestJS by only changing controllers.

### Client Architecture
- **TanStack Query**: Manages ALL server state (no Redux needed)
- **Zustand**: Only for UI state (modals, theme)
- **@dnd-kit**: Modern drag & drop (touch + keyboard support)

## Key Files

### Root Configuration

```
pnpm-workspace.yaml       # Defines workspace packages
package.json              # Root scripts (dev, build, test)
turbo.json                # Build caching (optional)
tsconfig.json             # Base TypeScript config
```

### Workspace Dependencies

Use `workspace:*` for internal packages:

```json
// apps/client/package.json
{
  "dependencies": {
    "@repo/shared-types": "workspace:*",
    "@repo/validation": "workspace:*"
  }
}
```

## Development Commands

```bash
# Install all dependencies
pnpm install

# Start both client and server
pnpm dev

# Run specific app
pnpm --filter client dev
pnpm --filter server dev

# Build everything
pnpm build

# Run tests
pnpm test

# Database migrations
pnpm --filter server prisma:migrate
```

## Naming Conventions

- **Components**: PascalCase (`BoardCard.tsx`)
- **Files**: camelCase (`useBoards.ts`)
- **Constants**: UPPER_SNAKE_CASE (`API_BASE_URL`)
- **Folders**: kebab-case or PascalCase (be consistent)

## Import Paths

Configure path aliases in `tsconfig.json`:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/components/*": ["src/components/*"],
      "@/hooks/*": ["src/hooks/*"],
      "@/lib/*": ["src/lib/*"]
    }
  }
}
```

Then import like:
```typescript
import { Button } from '@/components/common';
import { useBoards } from '@/hooks';
```

## Adding a New Feature

1. **Backend first**:
   - Update Prisma schema → migrate
   - Add repository function
   - Write service logic
   - Create controller
   - Add route
   - Write tests

2. **Frontend**:
   - Add TypeScript types to `packages/shared-types`
   - Create API service function
   - Build components
   - Add TanStack Query hook
   - Create page (if needed)
   - Add route

3. **Validation**:
   - Create Zod schema in `packages/validation`
   - Use in both server middleware and client forms

## Environment Variables

### Client (`.env`)
```bash
VITE_API_URL=http://localhost:3000
VITE_WS_URL=ws://localhost:3000
```

### Server (`.env`)
```bash
DATABASE_URL=postgresql://user:pass@localhost:5432/dbname
JWT_SECRET=your-secret-key
JWT_EXPIRES_IN=7d
PORT=3000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
```

## Testing Structure

```
apps/client/
└── src/
    └── __tests__/          # Tests co-located with code
        ├── components/
        ├── hooks/
        └── utils/

apps/server/
└── tests/
    ├── unit/               # Service/util tests
    ├── integration/        # API endpoint tests
    └── e2e/                # Full flow tests
```

## Production Build

```bash
pnpm build                  # Builds all apps and packages

# Output:
dist/
├── client/                 # Static files for CDN/Vercel
└── server/                 # Compiled Node.js app
```

## Next Steps

See [CLAUDE.md](./CLAUDE.md) for:
- Detailed tech stack decisions
- API endpoints
- Database schema
- Implementation patterns

---

**Keep it simple. Add complexity only when needed.**
