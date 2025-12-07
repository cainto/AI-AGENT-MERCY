# Angel AI - Symptom Checker & Health Navigator

## Overview

Angel AI is a medical symptom analysis web application that provides informational guidance to users based on their reported symptoms. The application prioritizes patient safety through emergency symptom detection and offers differential diagnosis predictions with confidence scoring. Built as a full-stack TypeScript application, it uses AI-powered symptom analysis to help users understand when to seek medical care while emphasizing that it is not a substitute for professional medical advice.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript using Vite as the build tool
- Single-page application (SPA) with client-side routing via Wouter
- Component library based on Radix UI primitives with shadcn/ui styling system
- Tailwind CSS for utility-first styling with custom design tokens
- State management through React hooks and TanStack Query for server state

**Key Design Principles**:
- Medical trust-focused UI with pink accent color scheme (#FFE5F0, #FFB3D9)
- Safety-first approach with prominent emergency warning system
- Clean, accessible interface optimized for health information display
- No hero images - functional tool focused on immediate symptom input

**Component Structure**:
- `Header`: Fixed navigation with links to symptom checker, disease info, and FAQ
- `EmergencyBanner`: Collapsible warning banner with red/orange gradient for critical symptoms
- `SymptomInput`: Primary textarea interface for symptom description
- `ChatMessage`: Conversational display of user symptoms and AI analysis
- `FAQSection`: Accordion-based frequently asked questions
- `DiseaseList`: Expandable cards showing common conditions
- `DisclaimerBanner`: Persistent medical disclaimer across all AI responses

### Backend Architecture

**Server Framework**: Express.js with TypeScript
- HTTP server with JSON API endpoints
- Development mode uses Vite middleware for HMR
- Production serves static built client files
- Rate limiting and session management prepared (via dependencies)

**API Design**:
- `POST /api/chat`: Accepts symptom descriptions, returns AI analysis with emergency detection and differential diagnoses
- RESTful JSON responses with structured diagnostic information
- Error handling returns user-friendly messages

**AI Integration**:
- Google Generative AI (Gemini) for symptom analysis
- Custom system prompt defines emergency red flag detection logic
- Structured JSON responses ensure consistent parsing of diagnoses and recommendations
- Confidence scoring (0-100) for each predicted condition

**Red Flag Detection**: Critical symptoms trigger immediate emergency responses:
- Severe chest pain with radiating symptoms
- Difficulty breathing or shortness of breath
- Sudden confusion or loss of consciousness
- Sudden numbness/weakness (stroke indicators)
- Severe thunderclap headache
- Uncontrolled bleeding
- Anaphylaxis symptoms (facial/throat swelling)

### Data Storage Solutions

**Current Implementation**: In-memory storage via `MemStorage` class
- User data stored in JavaScript Map structure
- No persistence across server restarts
- UUID-based user identification

**Database Schema** (Drizzle ORM configured for PostgreSQL):
- `users` table with id, username, password fields
- Schema defined using Drizzle ORM with Zod validation
- Migration directory structure prepared for schema evolution
- Connection configured via `DATABASE_URL` environment variable

**Migration Path**: Application is structured to easily transition from in-memory to PostgreSQL persistence by implementing database-backed storage methods while maintaining the `IStorage` interface contract.

### Authentication and Authorization

**Prepared Infrastructure**:
- Passport.js with local strategy dependencies installed
- Express session management configured (connect-pg-simple for PostgreSQL sessions)
- Password hashing capability via installed dependencies
- User schema includes username/password fields with unique constraints

**Current State**: Authentication endpoints not yet implemented; storage interface provides user CRUD methods ready for auth integration.

### External Dependencies

**Primary Services**:
- **Google Generative AI (Gemini)**: Core symptom analysis engine
  - API key required via `GEMINI_API_KEY` environment variable
  - Handles emergency detection and differential diagnosis generation
  - Returns structured JSON with conditions, confidence scores, and recommendations

**UI Component Libraries**:
- **Radix UI**: Headless accessible components (@radix-ui/react-*)
- **shadcn/ui**: Pre-styled component system built on Radix
- **Tailwind CSS**: Utility-first styling framework
- **Lucide React**: Icon library

**Development Tools**:
- **Vite**: Frontend build tool and dev server
- **Drizzle Kit**: Database migration tooling
- **ESBuild**: Server bundling for production
- **TanStack Query**: Async state management for API calls

**Runtime Dependencies**:
- **Express**: Web server framework
- **Drizzle ORM**: Type-safe database queries
- **Zod**: Runtime validation and schema definition
- **Wouter**: Lightweight client-side routing
- **date-fns**: Date manipulation utilities

**Database** (Configured but not required):
- PostgreSQL via `pg` driver
- Connection pooling and session storage prepared
- Optional - application functions with in-memory storage by default