# Project Management App

A modern, full-stack project management application inspired by Trello. Organize your work with boards, lists, and cards featuring drag-and-drop functionality and real-time collaboration.

![Project Status](https://img.shields.io/badge/status-in%20development-yellow)
![License](https://img.shields.io/badge/license-MIT-blue)

## Features

### Core Functionality
- **Boards**: Create and manage multiple project boards
- **Lists**: Organize tasks into customizable columns (To Do, In Progress, Done, etc.)
- **Cards**: Create detailed task cards with descriptions and metadata
- **Drag & Drop**: Intuitive card movement between lists
- **User Authentication**: Secure sign-up and login system
- **Real-time Sync**: Live updates across multiple users and devices

### Coming Soon
- Card details (checklists, due dates, attachments, comments)
- Board collaboration and sharing
- User roles and permissions
- Search and filtering
- Activity tracking
- Notifications
- Mobile responsive design

## Tech Stack

### Frontend
- **React 18+** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **Redux Toolkit** - State management
- **React Query** - Server state management
- **@dnd-kit** - Drag and drop functionality
- **Tailwind CSS** - Styling
- **React Router v6** - Routing

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **TypeScript** - Type safety
- **Prisma** - ORM and database toolkit
- **PostgreSQL** - Database
- **Socket.io** - Real-time communication
- **JWT** - Authentication
- **bcrypt** - Password hashing

### Development Tools
- **ESLint** - Linting
- **Prettier** - Code formatting
- **Vitest** - Unit testing
- **Playwright** - E2E testing
- **Husky** - Git hooks
- **lint-staged** - Pre-commit linting

## Prerequisites

Before you begin, ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v18 or higher)
- [PostgreSQL](https://www.postgresql.org/) (v14 or higher)
- [Git](https://git-scm.com/)
- npm or pnpm (comes with Node.js)

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/project-management-app.git
cd project-management-app
```

### 2. Install Dependencies

```bash
# Install root dependencies
npm install

# Install client dependencies
cd client
npm install

# Install server dependencies
cd ../server
npm install
cd ..
```

### 3. Environment Setup

Create `.env` files for both client and server:

**Client `.env`** (in `client/` directory):
```bash
VITE_API_URL=http://localhost:3000
VITE_WS_URL=ws://localhost:3000
```

**Server `.env`** (in `server/` directory):
```bash
DATABASE_URL=postgresql://username:password@localhost:5432/project_management_db
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
JWT_EXPIRES_IN=7d
PORT=3000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
```

### 4. Database Setup

```bash
cd server

# Create database
createdb project_management_db

# Run migrations
npx prisma migrate dev

# Generate Prisma client
npx prisma generate

# (Optional) Seed database with sample data
npm run seed
```

### 5. Start Development Servers

From the root directory:

```bash
# Start both client and server concurrently
npm run dev
```

Or start them separately:

```bash
# Terminal 1 - Start the backend server
cd server
npm run dev

# Terminal 2 - Start the frontend client
cd client
npm run dev
```

The application will be available at:
- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:3000
- **Prisma Studio** (Database GUI): `npx prisma studio` from server directory

## Project Structure

```
project-management-app/
├── client/                    # Frontend React application
│   ├── public/               # Static assets
│   ├── src/
│   │   ├── assets/          # Images, fonts, icons
│   │   ├── components/      # Reusable React components
│   │   │   ├── Board/      # Board-related components
│   │   │   ├── List/       # List-related components
│   │   │   ├── Card/       # Card-related components
│   │   │   ├── common/     # Shared UI components
│   │   │   └── layout/     # Layout components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── pages/          # Route pages/views
│   │   ├── services/       # API service layer
│   │   ├── store/          # Redux store and slices
│   │   ├── types/          # TypeScript type definitions
│   │   ├── utils/          # Helper functions
│   │   ├── App.tsx         # Root component
│   │   └── main.tsx        # Entry point
│   ├── .env.example
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.config.ts
│
├── server/                   # Backend Node.js application
│   ├── src/
│   │   ├── config/         # Configuration files
│   │   ├── controllers/    # Route controllers
│   │   ├── middleware/     # Express middleware
│   │   ├── models/         # Database models (Prisma)
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   ├── types/          # TypeScript type definitions
│   │   ├── utils/          # Helper functions
│   │   └── server.ts       # Entry point
│   ├── prisma/
│   │   ├── migrations/     # Database migrations
│   │   ├── schema.prisma   # Prisma schema
│   │   └── seed.ts         # Database seeding
│   ├── .env.example
│   ├── package.json
│   └── tsconfig.json
│
├── shared/                   # Shared code between client/server
│   └── types/               # Shared TypeScript types
│
├── docs/                     # Additional documentation
├── .gitignore
├── CLAUDE.md                # AI assistant context
├── LICENSE
├── package.json             # Root package.json (workspace)
└── README.md               # This file
```

## Available Scripts

### Root Directory
```bash
npm run dev          # Start both client and server
npm run build        # Build both client and server
npm run test         # Run all tests
npm run lint         # Lint all code
npm run format       # Format all code with Prettier
```

### Client Directory
```bash
npm run dev          # Start dev server (http://localhost:5173)
npm run build        # Build for production
npm run preview      # Preview production build
npm run test         # Run unit tests
npm run test:e2e     # Run E2E tests
npm run lint         # Run ESLint
```

### Server Directory
```bash
npm run dev          # Start dev server with hot reload
npm run build        # Compile TypeScript
npm start            # Start production server
npm run test         # Run tests
npm run prisma:studio # Open Prisma Studio
npm run prisma:migrate # Run database migrations
npm run seed         # Seed database
```

## API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user

### Board Endpoints
- `GET /api/boards` - Get all boards
- `GET /api/boards/:id` - Get board by ID
- `POST /api/boards` - Create new board
- `PATCH /api/boards/:id` - Update board
- `DELETE /api/boards/:id` - Delete board

### List Endpoints
- `POST /api/boards/:boardId/lists` - Create list
- `PATCH /api/lists/:id` - Update list
- `DELETE /api/lists/:id` - Delete list

### Card Endpoints
- `POST /api/lists/:listId/cards` - Create card
- `GET /api/cards/:id` - Get card details
- `PATCH /api/cards/:id` - Update card
- `DELETE /api/cards/:id` - Delete card
- `PATCH /api/cards/:id/move` - Move card to different list

For detailed API documentation, see [API.md](docs/API.md) (coming soon).

## Testing

### Run Unit Tests
```bash
npm run test
```

### Run E2E Tests
```bash
npm run test:e2e
```

### Test Coverage
```bash
npm run test:coverage
```

## Database Schema

The application uses PostgreSQL with Prisma ORM. Key entities:

- **User**: User accounts and authentication
- **Board**: Project boards/workspaces
- **List**: Columns within boards
- **Card**: Individual task items
- **Comment**: Card comments
- **Attachment**: File attachments on cards
- **BoardMember**: Board collaboration and permissions

View the complete schema in [server/prisma/schema.prisma](server/prisma/schema.prisma).

## Deployment

### Frontend (Vercel)
```bash
cd client
npm run build
# Deploy dist/ folder to Vercel
```

### Backend (Railway/Render)
```bash
cd server
npm run build
# Deploy to your preferred platform
```

### Environment Variables
Ensure all production environment variables are set:
- Database connection string
- JWT secret
- CORS origins
- API URLs

See [DEPLOYMENT.md](docs/DEPLOYMENT.md) for detailed deployment instructions (coming soon).

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Commit Convention
This project follows [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` New features
- `fix:` Bug fixes
- `docs:` Documentation changes
- `refactor:` Code refactoring
- `test:` Test updates
- `chore:` Build process or auxiliary tool changes

## Security

- Authentication via JWT tokens
- Password hashing with bcrypt
- Input validation on all endpoints
- SQL injection protection via Prisma
- XSS protection
- CORS configuration
- Rate limiting (coming soon)

Report security vulnerabilities to: security@yourapp.com

## Performance

- React.memo for expensive components
- Code splitting with React.lazy()
- Virtual scrolling for long lists
- Database query optimization
- Redis caching (coming soon)
- Image optimization

## Accessibility

- Keyboard navigation support
- ARIA labels for screen readers
- Focus management
- WCAG AA compliant color contrast
- Semantic HTML

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Roadmap

- [x] Project setup and planning
- [ ] User authentication
- [ ] Board CRUD operations
- [ ] List CRUD operations
- [ ] Card CRUD operations
- [ ] Drag and drop functionality
- [ ] Real-time updates with Socket.io
- [ ] Card details (description, checklist, etc.)
- [ ] Board collaboration
- [ ] Search and filter
- [ ] Mobile responsive design
- [ ] Dark mode
- [ ] Notifications
- [ ] Activity log

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by [Trello](https://trello.com)
- Built with [React](https://react.dev)
- Database powered by [Prisma](https://www.prisma.io)
- UI patterns from [shadcn/ui](https://ui.shadcn.com)

## Support

- Documentation: [docs/](docs/)
- Issues: [GitHub Issues](https://github.com/yourusername/project-management-app/issues)
- Discussions: [GitHub Discussions](https://github.com/yourusername/project-management-app/discussions)

## Authors

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

---

Made with ❤️ using React and Node.js
