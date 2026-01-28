# 🍳 FridgeChef

**Transform your leftover ingredients into delicious recipes with AI**

FridgeChef is a full-stack web application that helps you create amazing recipes from whatever ingredients you have on hand. Powered by OpenAI's GPT, it generates personalized, step-by-step cooking instructions tailored to your preferences and skill level.

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)](https://expressjs.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)](https://openai.com/)

## ✨ Features

- 🤖 **AI-Powered Recipe Generation** - Get creative recipe ideas from your available ingredients
- 📖 **Detailed Cooking Guidance** - Step-by-step instructions with pro tips and techniques
- 📚 **Recipe History** - Save and organize all your generated recipes
- ❤️ **Like & Rate** - Keep track of your favorite recipes with likes and ratings
- 👤 **User Profiles** - Customize preferences, dietary restrictions, and cooking skill level
- 🎨 **Dark Mode** - Easy on the eyes with beautiful dark theme support
- 📱 **Responsive Design** - Works seamlessly on desktop, tablet, and mobile
- 🔐 **Secure Authentication** - JWT-based user authentication and session management
- 💾 **Cloud Database** - PostgreSQL persistence with Neon serverless database
- ⚡ **Auto-Scroll UX** - Smooth navigation to recipe details when selected

## 🚀 Quick Start

### Interactive Setup (Recommended)

```bash
# Clone the repository
git clone https://github.com/Chirag8405/FridgeChef_FSD.git
cd FridgeChef_FSD

# Run the interactive setup wizard
./setup-database.sh

# Install dependencies
npm install

# Build and start
npm run build
npm start
```

Visit **http://localhost:3000** and start cooking! 🎉

### Manual Setup

1. **Clone and Install**
   ```bash
   git clone https://github.com/Chirag8405/FridgeChef_FSD.git
   cd FridgeChef_FSD
   npm install
   ```

2. **Setup Environment**
   ```bash
   cp .env.example .env
   nano .env  # Add your credentials
   ```

3. **Configure Database** (see [Database Setup Guide](./DATABASE_SETUP.md))
   - Sign up at [Neon](https://neon.tech) (free tier available)
   - Copy your connection string to `.env`

4. **Add API Keys**
   - Get OpenAI API key from [platform.openai.com](https://platform.openai.com/api-keys)
   - Generate JWT secret: `openssl rand -base64 32`

5. **Run the Application**
   ```bash
   npm run build
   npm start
   ```

## 🔧 Environment Variables

Create a `.env` file with these variables:

```bash
# Database (Required for persistence)
DATABASE_URL=postgresql://user:password@host:5432/database?sslmode=require

# OpenAI API (Required for AI recipe generation)
OPENAI_API_KEY=sk-your-key-here

# Authentication (Required)
JWT_SECRET=your-super-secret-key-minimum-32-characters

# Server Configuration (Optional)
PORT=3000
NODE_ENV=production
```

See [`.env.example`](./.env.example) for a complete template with detailed comments.

## 📖 Documentation

| Document | Description |
|----------|-------------|
| [🚀 Quick Start](./QUICK_START.md) | One-page quick reference to get started |
| [🗄️ Database Setup](./DATABASE_SETUP.md) | Complete guide for Neon, Supabase, or Railway |
| [✨ Production Features](./PRODUCTION_IMPROVEMENTS.md) | All implemented features and enhancements |
| [🐳 Deployment Guide](./DEPLOYMENT.md) | Docker, CI/CD, and cloud deployment options |
## 🏗️ Tech Stack

### Frontend
- **React 18** - Modern UI library with hooks
- **TypeScript** - Type-safe development
- **Vite** - Lightning-fast build tool
- **TailwindCSS** - Utility-first styling
- **shadcn/ui** - Beautiful component library
- **React Router** - Client-side routing

### Backend
- **Express.js** - Fast, minimalist web framework
- **Node.js** - JavaScript runtime
- **TypeScript** - Type-safe backend code
- **OpenAI GPT-4** - AI recipe generation
- **JWT** - Secure authentication

### Database & Storage
- **PostgreSQL** - Robust relational database
- **Neon** - Serverless PostgreSQL platform
- **Redis** - Caching layer (Docker setup)

### DevOps & Deployment
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **GitHub Actions** - CI/CD automation
- **Vercel** - Serverless deployment platform
- **Lighthouse CI** - Automated performance testing

## 📁 Project Structure

```
FridgeChef/
├── client/                 # React frontend application
│   ├── components/         # Reusable UI components
│   │   ├── ui/            # shadcn/ui components
│   │   └── Layout.tsx     # Main layout wrapper
│   ├── pages/             # Page components
│   │   ├── Dashboard.tsx  # Home dashboard
│   │   ├── GenerateRecipe.tsx  # Recipe generation
│   │   ├── History.tsx    # Recipe history
│   │   └── Profile.tsx    # User profile
│   ├── contexts/          # React contexts
│   │   ├── AuthContext.tsx     # Authentication state
│   │   └── RecipeContext.tsx   # Recipe management
│   ├── lib/               # Utilities and helpers
│   └── hooks/             # Custom React hooks
│
├── server/                # Express backend application
│   ├── routes/            # API route handlers
│   │   ├── auth.ts        # Authentication endpoints
│   │   ├── recipes.ts     # Recipe CRUD operations
│   │   └── health.ts      # Health check endpoints
│   ├── services/          # Business logic
│   │   └── openai.ts      # OpenAI integration
│   ├── database.ts        # Database connection & schema
│   └── index.ts           # Express server setup
│
├── shared/                # Shared types and utilities
│   └── api.ts            # API types and interfaces
│
├── public/                # Static assets
├── dist/                  # Build output
├── .github/workflows/     # GitHub Actions CI/CD
├── docker-compose.yml     # Docker services configuration
├── Dockerfile            # Container definition
└── vercel.json           # Vercel deployment config
```

## 🔌 API Endpoints

### Authentication
```
POST   /api/auth/register          Register new user
POST   /api/auth/login             User login
POST   /api/auth/logout            User logout
GET    /api/auth/me                Get current user info
```

### Recipes
```
POST   /api/recipes/generate       Generate AI recipes from ingredients
GET    /api/recipes/history        Get user's recipe history
GET    /api/recipes/:id            Get single recipe details
DELETE /api/recipes/:id            Delete a recipe
POST   /api/recipes/like           Like/unlike a recipe
POST   /api/recipes/rate           Rate a recipe (1-5 stars)
POST   /api/recipes/:id/detailed-explanation  Get detailed cooking guidance
```

### Profile
```
GET    /api/profile                Get user profile and stats
PUT    /api/profile                Update user profile and preferences
```

### Dashboard
```
GET    /api/dashboard              Get dashboard data (trending, stats)
```

### Health & Monitoring
```
GET    /api/health                 Health check endpoint
GET    /api/ready                  Readiness check for K8s
```

## 🐳 Deployment Options

### Local Development
```bash
npm run dev          # Start dev server with hot reload
npm run build        # Build for production
npm start            # Start production server
npm run typecheck    # Run TypeScript type checking
```

### Docker Deployment
```bash
# Build and run with Docker Compose
docker-compose up --build -d

# View logs
docker-compose logs -f

# Stop containers
docker-compose down
```

### Cloud Deployment (Vercel)
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy to production
vercel --prod

# Deploy preview
vercel
```

## 🧪 Testing

```bash
# Run type checking
npm run typecheck

# Run tests (coming soon)
npm test

# Check code formatting
npm run format.fix
```

## 🗄️ Database Schema

The application uses PostgreSQL with the following main tables:

- **users** - User accounts and authentication
- **recipes** - AI-generated recipe data
- **sessions** - User session management
- **recipe_likes** - User recipe likes
- **recipe_ratings** - Recipe reviews and ratings
- **user_ingredients** - User's ingredient inventory

Schema is automatically initialized on first run. See [DATABASE_SETUP.md](./DATABASE_SETUP.md) for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) for the GPT API
- [Neon](https://neon.tech/) for serverless PostgreSQL
- [Vercel](https://vercel.com/) for hosting and deployment
- [shadcn/ui](https://ui.shadcn.com/) for beautiful components
- All the amazing open-source libraries that made this possible

## 📧 Contact

**Priya Prasad** - [@priyaprasad25178-ctrl](https://github.com/priyaprasad25178)

Project Link: [https://github.com/Chirag8405/FridgeChef_FSD](https://github.com/Chirag8405/FridgeChef_FSD)

---

<div align="center">

Made by [Chirag](https://github.com/priyaprasad25178)

⭐ Star this repo if you find it helpful!

</div>
