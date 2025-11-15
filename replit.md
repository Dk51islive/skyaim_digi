# Momentum Agency - Project Documentation

## Overview

Momentum is a modern digital agency website built as a single-page application showcasing services, portfolio work, client testimonials, and providing contact functionality. The application demonstrates contemporary web design principles with a focus on professional aesthetics, performance, and user experience. It features a clean, confidence-inspiring design inspired by leading digital agencies like Vercel and Linear, combined with creative studio polish.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server, providing fast HMR (Hot Module Replacement)
- Wouter for lightweight client-side routing (single-page application)
- TanStack Query (React Query) for server state management

**UI Component System**
- Radix UI primitives as the foundation for accessible, unstyled components
- shadcn/ui design system (New York style variant) for pre-built, customizable components
- Tailwind CSS for utility-first styling with custom design tokens
- Class Variance Authority (CVA) for managing component variants

**Design Principles**
- Typography hierarchy using Inter (body/UI) and Space Grotesk (display/headlines) from Google Fonts
- Consistent spacing system based on Tailwind's 4px unit scale
- Custom CSS variables for theming with light/dark mode support
- Generous whitespace and bold typography for professional credibility
- Strategic use of elevation and borders for visual hierarchy

**State Management Strategy**
- React Query handles all server state (contact form submissions)
- Local component state via React hooks for UI interactions
- Form state managed by React Hook Form with Zod validation
- Toast notifications for user feedback

### Backend Architecture

**Server Framework**
- Express.js server with TypeScript
- Custom middleware for request logging and JSON parsing
- Vite integration for development with HMR support
- Static file serving in production mode

**API Design**
- RESTful endpoints with `/api` prefix
- Contact form submission endpoint (`POST /api/contact`)
- Admin endpoint for retrieving submissions (`GET /api/contact`)
- JSON request/response format with standardized error handling
- Zod schema validation on incoming requests

**Storage Layer**
- In-memory storage implementation (`MemStorage`) as the current data persistence layer
- Designed with an `IStorage` interface for future database implementation
- Drizzle ORM configured for PostgreSQL (ready for migration from in-memory to database)
- Schema definitions using Drizzle with Zod integration for type safety

**Rationale**: The in-memory storage provides a working prototype without external dependencies. The abstracted storage interface allows seamless migration to PostgreSQL by swapping the storage implementation without changing business logic.

### Data Storage Solutions

**Current Implementation**
- In-memory Map-based storage for users and contact submissions
- UUID-based primary keys using Node's crypto module
- Timestamp tracking for submission chronology

**Database Schema (Prepared for PostgreSQL Migration)**
- `users` table: id (UUID), username (unique), password
- `contact_submissions` table: id (UUID), name, email, message, created_at
- Drizzle schema definitions in `shared/schema.ts` provide single source of truth
- Automatic SQL migration generation via drizzle-kit

**Migration Path**: The codebase is structured to easily transition from in-memory to PostgreSQL by:
1. Setting `DATABASE_URL` environment variable
2. Running database migrations (`npm run db:push`)
3. Implementing database-backed storage class
4. No changes required to API routes or frontend code

### External Dependencies

**Third-Party UI Libraries**
- Radix UI: Accessible component primitives (accordion, dialog, dropdown, etc.)
- Lucide React: Icon library for consistent iconography
- React Icons: Additional icon set (Simple Icons for brand logos)
- Embla Carousel: Touch-friendly carousel component
- date-fns: Date manipulation and formatting

**Development & Build Tools**
- TypeScript: Type safety across full stack
- Vite: Fast development server and optimized production builds
- esbuild: Server-side bundling for production
- PostCSS with Autoprefixer: CSS processing
- Tailwind CSS: Utility-first styling

**Database & ORM**
- Drizzle ORM: Type-safe SQL query builder
- drizzle-zod: Bridge between Drizzle schemas and Zod validation
- @neondatabase/serverless: PostgreSQL driver for serverless environments
- connect-pg-simple: PostgreSQL session store (available for future session management)

**Form & Validation**
- React Hook Form: Performant form state management
- Zod: Runtime type validation and schema definition
- @hookform/resolvers: Integration bridge between React Hook Form and Zod

**Analytics & Tracking**
- Google Analytics 4 (GA4) integration with consent management
- Cookie consent banner with localStorage-based preference tracking
- Custom analytics wrapper for GDPR/privacy compliance
- Page view tracking with Wouter route integration

**Rationale for Key Choices**:
- **Drizzle over Prisma**: Lighter weight, better TypeScript inference, and direct SQL control
- **Wouter over React Router**: Smaller bundle size (1.2kb) suitable for single-page site
- **shadcn/ui over component library**: Provides ownership of components while maintaining consistency
- **In-memory storage first**: Allows rapid prototyping and easy local development before database setup

**Future Integration Points**
- Mailgun or similar email service for contact form notifications (infrastructure prepared, credentials needed)
- PostgreSQL database (schema and ORM fully configured)
- Session management (connect-pg-simple already in dependencies)