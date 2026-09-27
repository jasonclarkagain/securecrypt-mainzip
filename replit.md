# SecureCrypt - File Encryption/Decryption Application

## Overview

SecureCrypt is a full-stack web application that provides secure client-side file encryption and decryption capabilities. The application uses military-grade AES-256-GCM encryption with PBKDF2 key derivation, ensuring that all cryptographic operations happen in the browser without server-side file storage.

## User Preferences

```
Preferred communication style: Simple, everyday language.
```

## System Architecture

### Full-Stack Architecture
- **Frontend**: React SPA with TypeScript, built with Vite
- **Backend**: Express.js server with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Deployment**: Node.js with ESM modules

### Technology Stack
- **Frontend Framework**: React 18 with TypeScript
- **Build Tool**: Vite with hot module replacement
- **UI Components**: Radix UI primitives with shadcn/ui
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: React Query for server state, React hooks for local state
- **Routing**: Wouter for lightweight client-side routing

### Backend Stack
- **Runtime**: Node.js with ESM modules
- **Framework**: Express.js
- **Database**: PostgreSQL via Neon serverless (integrated)
- **ORM**: Drizzle with type-safe queries
- **Session Management**: PostgreSQL session store

## Key Components

### Client-Side Encryption Engine
- **Algorithm**: AES-256-GCM for authenticated encryption
- **Key Derivation**: PBKDF2 with 100,000 iterations and SHA-256
- **Security Features**: Random salt generation, secure IV generation
- **File Handling**: Supports multiple file types with size validation (100MB limit)

### User Interface Components
- **Encryption Panel**: Drag-and-drop file upload with batch processing
- **Decryption Panel**: Encrypted file handling with progress tracking
- **Security Dashboard**: Real-time security status and encryption history
- **Password Strength Indicator**: Visual feedback for password complexity

### API Endpoints
- `POST /api/log-encryption`: Logs encryption activity to PostgreSQL database
- `POST /api/validate-file`: Validates file metadata before processing
- `GET /api/security-status`: Returns current security configuration

### Database Schema
- **Users Table**: Stores user accounts with encrypted passwords
- **Encryption Logs Table**: Tracks all encryption/decryption activities with timestamps

## Data Flow

### Encryption Process
1. User selects files through drag-and-drop interface
2. Files are validated for size and type restrictions
3. Password strength is evaluated with real-time feedback
4. Files are encrypted client-side using Web Crypto API
5. Encrypted data is serialized and downloaded as .enc files
6. Activity is logged to the server for audit purposes

### Decryption Process
1. User uploads .enc file and enters password
2. File is deserialized and validated
3. Decryption occurs client-side with progress tracking
4. Original file is reconstructed and made available for download
5. Decryption activity is logged for security monitoring

## External Dependencies

### Frontend Dependencies
- **React Ecosystem**: React, React DOM, React Query for state management
- **UI Framework**: Radix UI components with shadcn/ui styling
- **Crypto Operations**: Web Crypto API (native browser support)
- **File Handling**: Native File API with drag-and-drop support

### Backend Dependencies
- **Database**: Neon PostgreSQL serverless with connection pooling
- **ORM**: Drizzle ORM with Zod schema validation
- **Session Management**: connect-pg-simple for PostgreSQL sessions
- **Development**: tsx for TypeScript execution, esbuild for production builds

## Deployment Strategy

### Development Environment
- **Dev Server**: Vite dev server with HMR and error overlay
- **Database**: Drizzle push for schema migrations
- **Process Management**: tsx for TypeScript execution with hot reload

### Production Build
- **Frontend**: Vite build with optimized asset bundling
- **Backend**: esbuild compilation to single ESM bundle
- **Database**: Drizzle migrations with PostgreSQL
- **Deployment**: Node.js process serving static files and API

### Security Considerations
- **Client-Side Only**: No server-side file storage or processing
- **Memory Management**: Sensitive data is cleared after use
- **Session Security**: PostgreSQL-backed sessions with secure cookies
- **Input Validation**: File size limits and type restrictions enforced

### Environment Configuration
- **Database**: Requires `DATABASE_URL` environment variable
- **Development**: Replit-specific tooling for cloud development
- **Production**: Optimized builds with external package bundling