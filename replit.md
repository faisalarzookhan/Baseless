# Baseless - Server Management Platform

## Overview

Baseless is a comprehensive server management platform built as a modern alternative to traditional hosting control panels like cPanel. It provides a clean, intuitive web interface for managing hosting accounts, domains, databases, files, and server resources. The system is designed to be the "easiest" hosting control panel solution, emphasizing simplicity and user experience.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Framework**: Shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with CSS custom properties for theming
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for client-side routing
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Schema Management**: Drizzle Kit for migrations
- **API Architecture**: RESTful API with type-safe endpoints

### Build Configuration
- **Monorepo Structure**: Shared types and schemas between client and server
- **Development**: Hot module replacement with Vite dev server
- **Production**: Optimized builds with esbuild for server bundling
- **TypeScript**: Strict type checking with path mapping for imports

## Key Components

### Database Schema
The system uses a comprehensive relational database schema with the following main entities:
- **Users**: User accounts with authentication and package assignments
- **Hosting Packages**: Resource allocation plans (disk space, bandwidth, databases, etc.)
- **Domains**: Primary, addon, subdomain, and alias domain management
- **Email Accounts**: Email account management with quotas
- **Databases**: PostgreSQL database management
- **File Entries**: File system representation for web-based file management
- **Server Stats**: System monitoring and resource usage tracking

### Frontend Pages
- **Dashboard**: Server overview with health metrics and statistics
- **User Accounts**: Complete user management with creation, editing, and resource monitoring
- **Hosting Packages**: Package management for resource allocation
- **File Manager**: Web-based file system management
- **Placeholder Pages**: Prepared structure for domain, email, database, monitoring, backup, and security management

### API Endpoints
RESTful API structure with full CRUD operations for:
- User management (`/api/users`)
- Hosting package management (`/api/hosting-packages`)
- Domain management (prepared structure)
- Email account management (prepared structure)
- Database management (prepared structure)
- File system operations (prepared structure)
- Server statistics (prepared structure)

## Data Flow

### Client-Server Communication
1. **Frontend**: React components make API calls using TanStack Query
2. **API Layer**: Express.js routes handle HTTP requests with validation
3. **Database**: Drizzle ORM provides type-safe database operations
4. **Response**: JSON responses with proper error handling and status codes

### State Management
1. **Server State**: TanStack Query manages server data with caching and synchronization
2. **Form State**: React Hook Form handles form validation and submission
3. **UI State**: Local React state for component-level interactions
4. **Global State**: Context providers for theme and authentication (prepared)

### Data Validation
- **Schema Validation**: Zod schemas shared between client and server
- **Type Safety**: TypeScript ensures compile-time type checking
- **Runtime Validation**: Server-side validation using Drizzle-Zod integration

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL database connection
- **drizzle-orm**: Type-safe database operations
- **@tanstack/react-query**: Server state management
- **react-hook-form**: Form handling and validation
- **zod**: Schema validation

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library
- **class-variance-authority**: Utility for managing CSS class variants

### Development Dependencies
- **vite**: Fast build tool and dev server
- **tsx**: TypeScript execution for development
- **esbuild**: Fast bundler for production builds

## Deployment Strategy

### Development Environment
- **Local Development**: Vite dev server with hot module replacement
- **Database**: Neon Database connection via environment variables
- **Type Checking**: Continuous TypeScript compilation
- **Script**: `npm run dev` for development server

### Production Build
- **Client Build**: Vite builds optimized static assets
- **Server Build**: esbuild bundles server code for Node.js
- **Database Migrations**: Drizzle Kit handles schema migrations
- **Environment**: Production-ready with `NODE_ENV=production`

### Database Management
- **Migrations**: Stored in `/migrations` directory
- **Schema**: Centralized in `shared/schema.ts`
- **Connection**: Environment-based configuration
- **Commands**: `npm run db:push` for schema updates

## Recent Changes

- **July 04, 2025**: Completed Replit Auth integration
  - Implemented OpenID Connect authentication with Replit
  - Updated database schema for string-based user IDs (from Replit)
  - Created landing page for non-authenticated users
  - Added user profile display and logout functionality
  - Updated frontend to use TanStack Query for auth state management

- **July 04, 2025**: Implemented Quick Action Floating Button
  - Created floating action button (FAB) with gradient design and animations
  - Added quick access to common hosting actions (Users, Packages, Domains, etc.)
  - Implemented keyboard shortcuts for all actions (Ctrl+U, Ctrl+P, Ctrl+D, etc.)
  - Added contextual actions that appear based on current page
  - Enhanced tooltips showing action names and keyboard shortcuts
  - Integrated FAB into Layout component for all authenticated pages

## Authentication Architecture

### Replit Auth Integration
- **Authentication Provider**: Replit OpenID Connect
- **Session Management**: PostgreSQL-based session storage with connect-pg-simple
- **User Storage**: Database-backed user management with automatic user upsert
- **Frontend Auth**: TanStack Query for authentication state
- **Protected Routes**: Component-based route protection

### User Flow
1. **Unauthenticated**: Users see landing page with "Get Started" button
2. **Login**: Clicking login redirects to `/api/login` (Replit OAuth flow)
3. **Callback**: Replit handles authentication and redirects back
4. **Authenticated**: Users access full hosting control panel
5. **Logout**: Users can logout via sidebar button (`/api/logout`)

## Changelog

```
Changelog:
- July 04, 2025. Initial setup
- July 04, 2025. Completed Replit Auth integration
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
```