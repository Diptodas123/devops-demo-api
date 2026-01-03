# DevOps Demo API

A production-ready RESTful API built with Node.js and Express, featuring authentication, role-based access control, and comprehensive security measures. Designed for containerized deployment with Docker and Kubernetes.

## 🚀 Features

- **Authentication & Authorization**: JWT-based authentication with role-based access control (RBAC)
- **Security**: Integrated security middleware with Arcjet, Helmet, and CORS
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Logging**: Winston logger with Morgan HTTP request logging
- **Validation**: Request validation using Zod schemas
- **Testing**: Jest test suite with code coverage reporting
- **Docker Support**: Multi-stage Docker builds for development and production
- **Hot Reload**: Development mode with Node.js watch mode
- **API Documentation**: RESTful API with clear endpoint structure

## 📋 Prerequisites

- Node.js (v18 or higher)
- PostgreSQL database
- Docker & Docker Compose (optional, for containerized deployment)

## 🛠️ Installation

1. Clone the repository:
```bash
git clone https://github.com/Diptodas123/kubernetes-demo-api.git
cd devops-demo-api
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
```

Edit `.env` with your configuration:
```env
# Server
PORT=3000
NODE_ENV=development

# Database
DATABASE_URL=your_postgresql_connection_string

# JWT
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=7d

# Cookies
COOKIE_SECRET=your_cookie_secret

# Arcjet (Security)
ARCJET_KEY=your_arcjet_key
```

4. Run database migrations:
```bash
npm run db:generate
npm run db:migrate
```

## 🚦 Running the Application

### Development Mode

```bash
# Local development with hot reload
npm run dev

# Docker development environment
npm run dev:docker
```

### Production Mode

```bash
# Local production
npm start

# Docker production environment
npm run prod:docker
```

### Database Management

```bash
# Generate migrations
npm run db:generate

# Run migrations
npm run db:migrate

# Open Drizzle Studio (Database GUI)
npm run db:studio
```

## 🧪 Testing

```bash
# Run tests
npm test

# Run tests with coverage
npm test -- --coverage
```

Coverage reports are generated in the `coverage/` directory.

## 📁 Project Structure

```
├── src/
│   ├── app.js                 # Express app configuration
│   ├── index.js              # Application entry point
│   ├── server.js             # Server setup
│   ├── config/               # Configuration files
│   │   ├── arcjet.js         # Arcjet security config
│   │   ├── database.js       # Database connection
│   │   └── logger.js         # Winston logger config
│   ├── controllers/          # Request handlers
│   │   ├── auth.controller.js
│   │   └── users.controller.js
│   ├── middleware/           # Custom middleware
│   │   ├── auth.middleware.js
│   │   ├── security.middleware.js
│   │   └── validation.middleware.js
│   ├── models/               # Database models
│   │   └── user.model.js
│   ├── routes/               # API routes
│   │   ├── auth.routes.js
│   │   └── users.route.js
│   ├── services/             # Business logic
│   │   ├── auth.service.js
│   │   └── users.service.js
│   ├── utils/                # Utility functions
│   │   ├── cookies.js
│   │   ├── format.js
│   │   └── jwt.js
│   └── validations/          # Zod validation schemas
│       ├── auth.validation.js
│       └── users.validation.js
├── tests/                    # Test files
├── drizzle/                  # Database migrations
├── scripts/                  # Deployment scripts
├── docker-compose.dev.yml    # Docker dev config
├── docker-compose.prod.yml   # Docker prod config
└── Dockerfile               # Docker image definition
```

## 🔌 API Endpoints

### Health Check

- `GET /health` - Health check endpoint
- `GET /api` - API status

### Authentication

- `POST /api/auth/sign-up` - User registration
- `POST /api/auth/sign-in` - User login
- `POST /api/auth/sign-out` - User logout

### Users (Protected Routes)

- `GET /api/users/` - Get all users (Admin only)
- `GET /api/users/:id` - Get user by ID
- `PATCH /api/users/:id` - Update user by ID
- `DELETE /api/users/:id` - Delete user by ID (Admin only)

## 🛡️ Security Features

- **Helmet**: Sets secure HTTP headers
- **CORS**: Cross-Origin Resource Sharing configuration
- **Arcjet**: Advanced security and rate limiting
- **JWT**: Secure token-based authentication
- **bcrypt**: Password hashing
- **Cookie Security**: HTTP-only cookies for token storage
- **Input Validation**: Zod schema validation on all inputs

## 🔧 Technologies Used

### Core
- **Express.js** - Web framework
- **PostgreSQL** - Database
- **Drizzle ORM** - Type-safe database operations

### Security
- **Arcjet** - Security and rate limiting
- **Helmet** - HTTP security headers
- **bcrypt** - Password hashing
- **jsonwebtoken** - JWT authentication

### Development
- **Jest** - Testing framework
- **ESLint** - Code linting
- **Prettier** - Code formatting
- **Winston** - Logging
- **Morgan** - HTTP request logging

## 🐳 Docker Deployment

### Development
```bash
docker-compose -f docker-compose.dev.yml up
```

### Production
```bash
docker-compose -f docker-compose.prod.yml up -d
```

## 📝 Code Quality

```bash
# Lint code
npm run lint

# Fix linting issues
npm run lint:fix

# Format code
npm run format

# Check formatting
npm run format:check
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
