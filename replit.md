# Overview

This is a full-stack web application built with Express.js and React that manages contact registration for WhatsApp groups. The application allows users to register their contact information through a public form and automatically redirects them to a WhatsApp group. It includes an admin panel for managing contacts and configuring the WhatsApp group link.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and production builds
- **Routing**: Wouter for client-side routing
- **UI Framework**: Radix UI components with shadcn/ui design system
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Form Handling**: React Hook Form with Zod validation

## Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM configured for PostgreSQL
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Session Management**: PostgreSQL-based sessions using connect-pg-simple
- **Validation**: Zod schemas for request/response validation
- **Development**: Hot module replacement with Vite integration

## Data Storage
- **Primary Database**: PostgreSQL via Neon Database
- **Development Fallback**: In-memory storage for testing
- **Schema Management**: Drizzle migrations with push-to-database strategy
- **Session Storage**: PostgreSQL-based session store
- **Settings Storage**: Key-value pairs for application configuration (WhatsApp link, name suffix)

# Key Components

## Database Schema
- **Contacts Table**: Stores user registration data (name, phone, country code, timestamps)
- **Settings Table**: Key-value store for application configuration (WhatsApp links, etc.)

## API Endpoints
- `POST /api/contacts` - Public contact registration
- `GET /api/whatsapp-link` - Retrieve WhatsApp group link
- `GET /api/admin/contacts` - Admin contact listing
- `PUT /api/admin/contacts/:id` - Admin contact editing
- `DELETE /api/admin/contacts/:id` - Admin contact deletion
- `DELETE /api/admin/contacts` - Bulk contact deletion
- `POST /api/admin/auth` - Admin authentication
- `PUT /api/admin/whatsapp-link` - Admin WhatsApp link management
- `GET /api/admin/name-suffix` - Retrieve current name suffix setting
- `POST /api/admin/name-suffix` - Update name suffix setting

## User Interface Pages
- **Public Home** (`/`) - Contact registration form
- **Success Page** (`/success`) - Registration confirmation with WhatsApp link
- **Admin Login** (`/admin`) - Authentication for admin access
- **Admin Dashboard** (`/admin/dashboard`) - Contact management interface

## Business Logic Features
- Configurable name suffix addition to contact names (default: "k.1🔥")
- Duplicate detection by name and phone number
- Country code selection with flag display (Haiti +509 as default)
- CSV export functionality for contacts
- WhatsApp group link configuration
- Contact search functionality by name or phone number
- Dark mode theme with modern gradient design

# Data Flow

## Public Registration Flow
1. User fills registration form with name, phone, and country
2. Frontend validates input using Zod schemas
3. Backend checks for duplicates and adds name suffix
4. Contact is stored in database
5. User is redirected to success page with WhatsApp link

## Admin Management Flow
1. Admin authenticates with password
2. Dashboard loads contact list via React Query
3. Admin can edit, delete, or export contacts
4. Admin can update WhatsApp group link
5. All changes are immediately reflected in the UI

# External Dependencies

## Core Framework Dependencies
- **@neondatabase/serverless** - Neon PostgreSQL database driver
- **drizzle-orm** & **drizzle-kit** - Database ORM and migration tools
- **@tanstack/react-query** - Server state management
- **react-hook-form** & **@hookform/resolvers** - Form management
- **zod** & **drizzle-zod** - Runtime validation

## UI Component Dependencies
- **@radix-ui/** packages - Accessible UI primitives
- **tailwindcss** - Utility-first CSS framework
- **class-variance-authority** & **clsx** - CSS class management
- **lucide-react** - Icon library
- **react-icons** - Additional icons (WhatsApp)

## Development Dependencies
- **vite** - Build tool and development server
- **tsx** - TypeScript execution for Node.js
- **esbuild** - Production bundling for server

# Deployment Strategy

## Build Process
- **Frontend**: Vite builds React app to `dist/public`
- **Backend**: esbuild bundles server code to `dist/index.js`
- **Database**: Drizzle pushes schema changes to PostgreSQL

## Environment Configuration
- **DATABASE_URL** - PostgreSQL connection string (required)
- **NODE_ENV** - Environment mode (development/production)
- **REPL_ID** - Replit-specific environment detection

## Production Setup
- Single Node.js process serving both API and static files
- PostgreSQL database with automatic migrations
- Session-based authentication for admin access
- Static file serving with Vite-generated assets

## Development Features
- Hot module replacement for frontend
- TypeScript compilation for both client and server
- Automatic database schema synchronization
- Request logging middleware for API debugging
