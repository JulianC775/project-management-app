# Project Structure & Folder Management Plan

This document outlines the complete folder structure and organization strategy for the Project Management App.

## Directory Tree

```
project-management-app/
│
├── client/                          # Frontend React Application
│   ├── public/                      # Static assets served directly
│   │   ├── favicon.ico
│   │   ├── robots.txt
│   │   └── manifest.json
│   │
│   ├── src/
│   │   ├── assets/                  # Images, fonts, icons
│   │   │   ├── images/
│   │   │   │   ├── logo.svg
│   │   │   │   ├── default-avatar.png
│   │   │   │   └── backgrounds/    # Board background images
│   │   │   ├── icons/              # SVG icons
│   │   │   └── fonts/              # Custom fonts
│   │   │
│   │   ├── components/             # React components
│   │   │   ├── Board/
│   │   │   │   ├── Board.tsx
│   │   │   │   ├── BoardCard.tsx   # Board preview card
│   │   │   │   ├── BoardHeader.tsx
│   │   │   │   ├── BoardMenu.tsx
│   │   │   │   ├── CreateBoardModal.tsx
│   │   │   │   └── index.ts        # Barrel export
│   │   │   │
│   │   │   ├── List/
│   │   │   │   ├── List.tsx
│   │   │   │   ├── ListHeader.tsx
│   │   │   │   ├── ListMenu.tsx
│   │   │   │   ├── CreateListForm.tsx
│   │   │   │   └── index.ts
│   │   │   │
│   │   │   ├── Card/
│   │   │   │   ├── Card.tsx
│   │   │   │   ├── CardModal.tsx    # Full card details
│   │   │   │   ├── CardLabels.tsx
│   │   │   │   ├── CardMembers.tsx
│   │   │   │   ├── CardChecklist.tsx
│   │   │   │   ├── CardComments.tsx
│   │   │   │   ├── CardAttachments.tsx
│   │   │   │   ├── CreateCardForm.tsx
│   │   │   │   └── index.ts
│   │   │   │
│   │   │   ├── common/              # Reusable UI components
│   │   │   │   ├── Button/
│   │   │   │   │   ├── Button.tsx
│   │   │   │   │   ├── IconButton.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Input/
│   │   │   │   │   ├── Input.tsx
│   │   │   │   │   ├── TextArea.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Modal/
│   │   │   │   │   ├── Modal.tsx
│   │   │   │   │   ├── ModalHeader.tsx
│   │   │   │   │   ├── ModalBody.tsx
│   │   │   │   │   ├── ModalFooter.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Dropdown/
│   │   │   │   │   ├── Dropdown.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Avatar/
│   │   │   │   │   ├── Avatar.tsx
│   │   │   │   │   ├── AvatarGroup.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Spinner/
│   │   │   │   │   ├── Spinner.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Toast/
│   │   │   │   │   ├── Toast.tsx
│   │   │   │   │   ├── ToastContainer.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   └── index.ts
│   │   │   │
│   │   │   ├── layout/              # Layout components
│   │   │   │   ├── Header/
│   │   │   │   │   ├── Header.tsx
│   │   │   │   │   ├── UserMenu.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── Sidebar/
│   │   │   │   │   ├── Sidebar.tsx
│   │   │   │   │   ├── SidebarItem.tsx
│   │   │   │   │   └── index.ts
│   │   │   │   ├── MainLayout.tsx
│   │   │   │   ├── AuthLayout.tsx
│   │   │   │   └── index.ts
│   │   │   │
│   │   │   └── index.ts             # Global component exports
│   │   │
│   │   ├── hooks/                   # Custom React hooks
│   │   │   ├── useAuth.ts           # Authentication hook
│   │   │   ├── useBoards.ts         # Board operations
│   │   │   ├── useLists.ts          # List operations
│   │   │   ├── useCards.ts          # Card operations
│   │   │   ├── useDragAndDrop.ts    # Drag & drop logic
│   │   │   ├── useSocket.ts         # WebSocket connection
│   │   │   ├── useDebounce.ts       # Debounce utility
│   │   │   ├── useLocalStorage.ts   # Local storage
│   │   │   ├── useClickOutside.ts   # Click outside detection
│   │   │   └── index.ts
│   │   │
│   │   ├── pages/                   # Route pages/views
│   │   │   ├── Home/
│   │   │   │   ├── Home.tsx
│   │   │   │   └── index.ts
│   │   │   ├── Dashboard/
│   │   │   │   ├── Dashboard.tsx    # Board list view
│   │   │   │   └── index.ts
│   │   │   ├── BoardView/
│   │   │   │   ├── BoardView.tsx    # Main board view
│   │   │   │   └── index.ts
│   │   │   ├── Login/
│   │   │   │   ├── Login.tsx
│   │   │   │   └── index.ts
│   │   │   ├── Register/
│   │   │   │   ├── Register.tsx
│   │   │   │   └── index.ts
│   │   │   ├── Profile/
│   │   │   │   ├── Profile.tsx
│   │   │   │   └── index.ts
│   │   │   ├── NotFound/
│   │   │   │   ├── NotFound.tsx
│   │   │   │   └── index.ts
│   │   │   └── index.ts
│   │   │
│   │   ├── services/                # API service layer
│   │   │   ├── api/
│   │   │   │   ├── client.ts        # Axios instance config
│   │   │   │   ├── auth.api.ts      # Auth endpoints
│   │   │   │   ├── boards.api.ts    # Board endpoints
│   │   │   │   ├── lists.api.ts     # List endpoints
│   │   │   │   ├── cards.api.ts     # Card endpoints
│   │   │   │   └── index.ts
│   │   │   ├── socket/
│   │   │   │   ├── socket.ts        # Socket.io client setup
│   │   │   │   ├── events.ts        # Socket event handlers
│   │   │   │   └── index.ts
│   │   │   └── index.ts
│   │   │
│   │   ├── store/                   # Redux store
│   │   │   ├── slices/
│   │   │   │   ├── authSlice.ts     # Auth state
│   │   │   │   ├── boardsSlice.ts   # Boards state
│   │   │   │   ├── uiSlice.ts       # UI state (modals, etc.)
│   │   │   │   └── index.ts
│   │   │   ├── store.ts             # Store configuration
│   │   │   ├── hooks.ts             # Typed hooks (useAppDispatch, etc.)
│   │   │   └── index.ts
│   │   │
│   │   ├── types/                   # TypeScript types
│   │   │   ├── models.ts            # Data models (User, Board, etc.)
│   │   │   ├── api.ts               # API request/response types
│   │   │   ├── components.ts        # Component prop types
│   │   │   ├── store.ts             # Redux state types
│   │   │   └── index.ts
│   │   │
│   │   ├── utils/                   # Helper functions
│   │   │   ├── validation.ts        # Form validation schemas
│   │   │   ├── formatters.ts        # Date, text formatters
│   │   │   ├── constants.ts         # App constants
│   │   │   ├── storage.ts           # LocalStorage helpers
│   │   │   ├── colors.ts            # Color utilities
│   │   │   └── index.ts
│   │   │
│   │   ├── styles/                  # Global styles
│   │   │   ├── index.css            # Main styles, Tailwind imports
│   │   │   ├── variables.css        # CSS variables
│   │   │   └── animations.css       # Custom animations
│   │   │
│   │   ├── App.tsx                  # Root component
│   │   ├── main.tsx                 # Entry point
│   │   └── vite-env.d.ts           # Vite type definitions
│   │
│   ├── .env.example                # Example environment variables
│   ├── .eslintrc.json              # ESLint config
│   ├── .prettierrc                 # Prettier config
│   ├── index.html                  # HTML entry point
│   ├── package.json
│   ├── postcss.config.js           # PostCSS config (Tailwind)
│   ├── tailwind.config.js          # Tailwind CSS config
│   ├── tsconfig.json               # TypeScript config
│   ├── tsconfig.node.json          # TypeScript config for Node
│   └── vite.config.ts              # Vite configuration
│
├── server/                          # Backend Node.js Application
│   ├── src/
│   │   ├── config/                  # Configuration files
│   │   │   ├── database.ts          # Database connection
│   │   │   ├── jwt.ts               # JWT configuration
│   │   │   ├── cors.ts              # CORS configuration
│   │   │   ├── socket.ts            # Socket.io configuration
│   │   │   └── index.ts
│   │   │
│   │   ├── controllers/             # Route controllers
│   │   │   ├── auth.controller.ts   # Auth logic
│   │   │   ├── boards.controller.ts # Board CRUD
│   │   │   ├── lists.controller.ts  # List CRUD
│   │   │   ├── cards.controller.ts  # Card CRUD
│   │   │   ├── users.controller.ts  # User operations
│   │   │   └── index.ts
│   │   │
│   │   ├── middleware/              # Express middleware
│   │   │   ├── auth.middleware.ts   # JWT verification
│   │   │   ├── validate.middleware.ts # Request validation
│   │   │   ├── error.middleware.ts  # Error handling
│   │   │   ├── logger.middleware.ts # Request logging
│   │   │   ├── rateLimit.middleware.ts # Rate limiting
│   │   │   └── index.ts
│   │   │
│   │   ├── routes/                  # API routes
│   │   │   ├── auth.routes.ts       # Auth routes
│   │   │   ├── boards.routes.ts     # Board routes
│   │   │   ├── lists.routes.ts      # List routes
│   │   │   ├── cards.routes.ts      # Card routes
│   │   │   ├── users.routes.ts      # User routes
│   │   │   ├── index.ts             # Route aggregation
│   │   │   └── v1.routes.ts         # API v1 router
│   │   │
│   │   ├── services/                # Business logic
│   │   │   ├── auth.service.ts      # Auth business logic
│   │   │   ├── boards.service.ts    # Board business logic
│   │   │   ├── lists.service.ts     # List business logic
│   │   │   ├── cards.service.ts     # Card business logic
│   │   │   ├── users.service.ts     # User business logic
│   │   │   ├── email.service.ts     # Email notifications
│   │   │   └── index.ts
│   │   │
│   │   ├── socket/                  # WebSocket handlers
│   │   │   ├── handlers/
│   │   │   │   ├── board.handler.ts
│   │   │   │   ├── card.handler.ts
│   │   │   │   ├── list.handler.ts
│   │   │   │   └── index.ts
│   │   │   ├── socket.ts            # Socket.io setup
│   │   │   └── index.ts
│   │   │
│   │   ├── types/                   # TypeScript types
│   │   │   ├── express.d.ts         # Express type extensions
│   │   │   ├── models.ts            # Data model types
│   │   │   ├── requests.ts          # Request body types
│   │   │   ├── responses.ts         # Response types
│   │   │   └── index.ts
│   │   │
│   │   ├── utils/                   # Helper functions
│   │   │   ├── validation/
│   │   │   │   ├── auth.validation.ts
│   │   │   │   ├── board.validation.ts
│   │   │   │   ├── list.validation.ts
│   │   │   │   ├── card.validation.ts
│   │   │   │   └── index.ts
│   │   │   ├── password.ts          # Password hashing
│   │   │   ├── jwt.ts               # JWT utilities
│   │   │   ├── errors.ts            # Custom error classes
│   │   │   ├── logger.ts            # Winston logger
│   │   │   └── index.ts
│   │   │
│   │   └── server.ts                # Entry point & Express setup
│   │
│   ├── prisma/
│   │   ├── migrations/              # Database migrations
│   │   │   └── migration_lock.toml
│   │   ├── schema.prisma            # Prisma schema definition
│   │   └── seed.ts                  # Database seeding script
│   │
│   ├── tests/                       # Server tests
│   │   ├── unit/
│   │   │   ├── services/
│   │   │   └── utils/
│   │   ├── integration/
│   │   │   ├── auth.test.ts
│   │   │   ├── boards.test.ts
│   │   │   └── cards.test.ts
│   │   └── setup.ts
│   │
│   ├── .env.example                # Example environment variables
│   ├── .eslintrc.json              # ESLint config
│   ├── .prettierrc                 # Prettier config
│   ├── package.json
│   ├── tsconfig.json               # TypeScript config
│   └── nodemon.json                # Nodemon config
│
├── shared/                          # Shared code between client/server
│   ├── types/
│   │   ├── user.types.ts
│   │   ├── board.types.ts
│   │   ├── list.types.ts
│   │   ├── card.types.ts
│   │   └── index.ts
│   ├── constants/
│   │   ├── roles.ts
│   │   ├── permissions.ts
│   │   └── index.ts
│   └── package.json
│
├── docs/                            # Documentation
│   ├── API.md                       # API documentation
│   ├── DEPLOYMENT.md                # Deployment guide
│   ├── CONTRIBUTING.md              # Contribution guidelines
│   ├── ARCHITECTURE.md              # Architecture decisions
│   └── images/                      # Documentation images
│
├── .github/                         # GitHub specific files
│   ├── workflows/
│   │   ├── ci.yml                   # CI pipeline
│   │   ├── deploy.yml               # Deployment pipeline
│   │   └── test.yml                 # Test pipeline
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── pull_request_template.md
│
├── .husky/                          # Git hooks
│   ├── pre-commit                   # Run linting before commit
│   └── pre-push                     # Run tests before push
│
├── .vscode/                         # VSCode settings
│   ├── settings.json                # Workspace settings
│   ├── extensions.json              # Recommended extensions
│   └── launch.json                  # Debug configurations
│
├── .gitignore                       # Git ignore rules
├── .prettierignore                  # Prettier ignore rules
├── CLAUDE.md                        # AI assistant context
├── LICENSE                          # MIT License
├── package.json                     # Root package.json (workspaces)
├── pnpm-workspace.yaml             # PNPM workspaces config (optional)
├── PROJECT_STRUCTURE.md            # This file
└── README.md                        # Project documentation
```

## Folder Purposes

### Client Structure

#### `/client/src/components/`
Organized by feature and reusability:
- **Feature folders** (Board, List, Card): Domain-specific components
- **common/**: Reusable UI components used across features
- **layout/**: Application layout and navigation components
- Each component folder includes index.ts for clean imports

#### `/client/src/hooks/`
Custom React hooks for:
- Data fetching and mutations
- Business logic reuse
- Side effects management
- State management patterns

#### `/client/src/pages/`
Route-level components:
- One folder per route
- Contains page component and any page-specific logic
- Composes smaller components from `/components/`

#### `/client/src/services/`
External integrations:
- **api/**: HTTP API calls with Axios
- **socket/**: WebSocket real-time communication
- Abstracts network layer from components

#### `/client/src/store/`
Redux state management:
- **slices/**: Feature-based state slices
- **store.ts**: Store configuration with middleware
- **hooks.ts**: Typed Redux hooks

#### `/client/src/types/`
TypeScript definitions:
- Shared interfaces and types
- API contracts
- Component props

#### `/client/src/utils/`
Pure utility functions:
- Validation logic
- Formatters
- Constants
- Helper functions

### Server Structure

#### `/server/src/controllers/`
Request handlers:
- Receive requests
- Call services
- Send responses
- Thin layer - business logic goes in services

#### `/server/src/services/`
Business logic layer:
- Core application logic
- Database operations via Prisma
- Data transformations
- Complex operations

#### `/server/src/middleware/`
Express middleware:
- Authentication/Authorization
- Request validation
- Error handling
- Logging
- Rate limiting

#### `/server/src/routes/`
API route definitions:
- Map URLs to controllers
- Apply middleware
- Version management (v1, v2, etc.)

#### `/server/src/socket/`
WebSocket handlers:
- Real-time event handling
- Socket.io room management
- Event broadcasting

#### `/server/src/utils/`
Utility functions:
- Validation schemas
- JWT helpers
- Password hashing
- Custom error classes
- Logger setup

#### `/server/prisma/`
Database management:
- **schema.prisma**: Database schema
- **migrations/**: Version-controlled schema changes
- **seed.ts**: Sample data for development

### Shared Structure

#### `/shared/`
Code shared between client and server:
- Type definitions
- Constants
- Validation schemas
- Ensures consistency across full stack

## File Naming Conventions

### Components
- **PascalCase** for component files: `BoardCard.tsx`
- **camelCase** for non-component files: `utils.ts`
- Use `index.ts` for barrel exports

### Tests
- Match source file name with `.test.ts` or `.spec.ts` suffix
- Example: `auth.service.ts` → `auth.service.test.ts`

### Configuration Files
- Use standard naming: `.eslintrc.json`, `tsconfig.json`
- kebab-case for custom configs: `jest.config.js`

## Import Structure

### Absolute Imports
Configure path aliases in `tsconfig.json`:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/components/*": ["src/components/*"],
      "@/hooks/*": ["src/hooks/*"],
      "@/services/*": ["src/services/*"],
      "@/store/*": ["src/store/*"],
      "@/types/*": ["src/types/*"],
      "@/utils/*": ["src/utils/*"]
    }
  }
}
```

### Import Order
1. External libraries (React, etc.)
2. Internal absolute imports (@/...)
3. Relative imports (../, ./)
4. Type imports
5. Styles

Example:
```typescript
import React, { useState } from 'react';
import { useNavigate } from 'react-router-dom';

import { Button } from '@/components/common';
import { useAuth } from '@/hooks';
import { loginUser } from '@/services/api';

import { LoginFormData } from './types';
import styles from './Login.module.css';
```

## Development Workflow

### Adding a New Feature

1. **Plan the feature** - Update CLAUDE.md if needed
2. **Create types** - Add TypeScript interfaces
3. **Backend first**:
   - Update Prisma schema
   - Create migration
   - Add service layer logic
   - Create controller
   - Add routes
   - Write tests
4. **Frontend**:
   - Create API service functions
   - Build components
   - Add Redux slice if needed
   - Create pages
   - Add routes
   - Write tests

### Code Organization Best Practices

1. **Single Responsibility**: Each file/function does one thing
2. **Barrel Exports**: Use index.ts to simplify imports
3. **Co-location**: Keep related files together
4. **Type Safety**: Define types before implementation
5. **Test Coverage**: Write tests alongside code
6. **Documentation**: Add JSDoc comments for complex logic

## Environment Setup

### Client Environment Variables
```bash
VITE_API_URL=http://localhost:3000
VITE_WS_URL=ws://localhost:3000
VITE_APP_NAME=Project Management App
```

### Server Environment Variables
```bash
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/db_name

# JWT
JWT_SECRET=your-secret-key
JWT_EXPIRES_IN=7d

# Server
PORT=3000
NODE_ENV=development

# CORS
CORS_ORIGIN=http://localhost:5173

# Email (optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-password
```

## Build & Deployment Structure

### Production Build Output
```
dist/
├── client/              # Frontend static files
│   ├── assets/
│   ├── index.html
│   └── ...
└── server/              # Compiled backend code
    ├── src/
    └── server.js
```

### Docker Structure (Optional)
```
docker/
├── Dockerfile.client
├── Dockerfile.server
└── docker-compose.yml
```

## Monitoring File Size

Keep bundle sizes manageable:
- Client bundle: < 500KB (gzipped)
- Use code splitting for routes
- Lazy load heavy components
- Optimize images and assets

## Next Steps

1. Initialize client with Vite + React + TypeScript
2. Initialize server with Express + TypeScript
3. Set up Prisma with PostgreSQL
4. Configure ESLint, Prettier, Husky
5. Create base folder structure
6. Set up package.json scripts
7. Begin implementing authentication

---

This structure provides:
- Clear separation of concerns
- Scalability for future features
- Easy navigation and maintenance
- Consistent organization patterns
- Type safety throughout the stack
