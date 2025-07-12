# EcoBin - AI-Powered Waste Management App

## Overview

EcoBin is a comprehensive waste management application that combines AI-powered scanning, smart scheduling, community engagement, and educational features to promote sustainable waste disposal practices. The application features a modern React frontend with a Node.js/Express backend, utilizing PostgreSQL for data persistence and implementing Replit's authentication system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with shadcn/ui components
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite for fast development and optimized builds

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL storage

### Database Design
- **Primary Database**: PostgreSQL via Neon serverless
- **Schema Management**: Drizzle migrations
- **Key Tables**:
  - Users (authentication and profile data)
  - Waste entries (tracking user waste disposal)
  - Pickup schedules (waste collection appointments)
  - Community reports (environmental issue reporting)
  - Cleanup events (community activities)
  - Challenges and rewards (gamification)

## Key Components

### 1. Authentication System
- **Implementation**: Replit Auth with OpenID Connect
- **Session Storage**: PostgreSQL-backed sessions
- **User Management**: Automatic user creation and profile management
- **Security**: HTTP-only cookies with secure session handling

### 2. AI-Powered Waste Scanner
- **Purpose**: Identify waste types and provide disposal guidance
- **Technology**: Planned integration with Gemini AI API
- **Features**: Camera capture, image analysis, disposal recommendations
- **User Flow**: Scan item → AI analysis → disposal instructions → optional waste entry logging

### 3. Smart Scheduling System
- **Functionality**: Schedule waste pickups by type and location
- **Types Supported**: Organic, plastic, e-waste, hazardous, bulk waste
- **Features**: Calendar integration, location tracking, status updates
- **User Interface**: Form-based scheduling with date/time picker

### 4. Community Features
- **Reporting**: Geotagged environmental issue reporting
- **Events**: Community cleanup event management
- **Gamification**: Points, badges, and leaderboards
- **Social**: User engagement through challenges and rewards

### 5. Analytics Dashboard
- **Personal Metrics**: Waste generation tracking, carbon footprint
- **Visualizations**: Charts and graphs for waste patterns
- **Progress Tracking**: Environmental impact measurement
- **Recommendations**: Personalized sustainability suggestions

## Data Flow

### User Authentication Flow
1. User accesses protected route
2. Middleware checks for valid session
3. If unauthenticated, redirects to Replit Auth
4. On successful auth, creates/updates user profile
5. Establishes session and redirects to dashboard

### Waste Entry Flow
1. User logs waste disposal (manual or via scanner)
2. Data validated against Zod schema
3. Entry stored in PostgreSQL with user association
4. Analytics recalculated for dashboard updates
5. Points awarded based on waste type and quantity

### Scheduling Flow
1. User selects waste type and preferred date/time
2. System validates availability and user location
3. Schedule entry created with pending status
4. Notifications sent for confirmation and tracking
5. Status updates throughout pickup process

## External Dependencies

### Core Dependencies
- **Database**: Neon PostgreSQL serverless
- **Authentication**: Replit Auth service
- **UI Components**: Radix UI primitives with shadcn/ui
- **Icons**: Lucide React icons
- **Date Handling**: date-fns for date manipulation

### Development Dependencies
- **Build System**: Vite with TypeScript support
- **Code Quality**: ESLint, TypeScript compiler
- **Styling**: Tailwind CSS with PostCSS
- **Development Tools**: tsx for TypeScript execution

### Planned Integrations
- **AI Service**: Gemini AI API for waste recognition
- **Maps**: Location services for pickup scheduling
- **Notifications**: Push notifications for schedule updates

## Deployment Strategy

### Build Process
1. **Frontend**: Vite builds React app to `dist/public`
2. **Backend**: esbuild bundles server code to `dist/index.js`
3. **Database**: Drizzle migrations applied via `db:push` command
4. **Assets**: Static assets served from build directory

### Production Configuration
- **Environment**: Node.js production mode
- **Process Management**: Single process with Express static serving
- **Database**: Connection pooling with Neon serverless
- **Sessions**: PostgreSQL session store for scalability

### Development Setup
- **Hot Reload**: Vite HMR for frontend changes
- **Server Restart**: tsx with nodemon-like behavior
- **Database**: Live connection to Neon development instance
- **Authentication**: Replit Auth in development mode

### Environmental Variables
- `DATABASE_URL`: PostgreSQL connection string
- `SESSION_SECRET`: Session encryption key
- `REPL_ID`: Replit authentication identifier
- `REPLIT_DOMAINS`: Allowed domains for auth
- `ISSUER_URL`: OpenID Connect issuer URL

The application is designed as a full-stack TypeScript application with a focus on developer experience, user engagement, and environmental impact tracking. The architecture supports both development and production deployment on Replit's infrastructure while maintaining the flexibility to extend with additional AI and mapping services.