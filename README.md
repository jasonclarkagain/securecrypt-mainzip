# SecureCrypt - Military-Grade File Encryption Tool

A professional web-based file encryption application using AES-256-GCM with client-side processing for maximum security.

## 🔒 Features

- **Military-Grade Encryption**: AES-256-GCM with authenticated encryption
- **Client-Side Processing**: All encryption happens in your browser - no server storage
- **PBKDF2 Key Derivation**: 100,000 iterations with SHA-256 for secure password-based encryption
- **Professional Interface**: Drag-and-drop file upload with real-time progress tracking
- **Password Strength Validation**: Real-time feedback on password complexity
- **Audit Trail**: PostgreSQL database logging for compliance and security monitoring
- **File History**: Track recent encryption/decryption operations
- **Multiple File Support**: Encrypt multiple files simultaneously

## 🛡️ Security Features

- **Zero Server Storage**: Files never leave your browser during encryption
- **Random Salt Generation**: Unique salt for each encryption operation
- **Secure IV Generation**: Cryptographically secure initialization vectors
- **Memory Management**: Sensitive data cleared after operations
- **File Size Validation**: 100MB limit with comprehensive type checking

## 🚀 Quick Start

### Prerequisites

- Node.js 20+ 
- PostgreSQL database
- Modern web browser with Web Crypto API support

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/securecrypt.git
cd securecrypt
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your database credentials
```

4. Push database schema:
```bash
npm run db:push
```

5. Start the development server:
```bash
npm run dev
```

6. Open your browser to `http://localhost:5000`

## 🏗️ Technology Stack

### Frontend
- **React 18** with TypeScript
- **Vite** for development and building
- **Tailwind CSS** for styling
- **Radix UI** components with shadcn/ui
- **React Query** for state management
- **Wouter** for client-side routing

### Backend
- **Express.js** server with TypeScript
- **PostgreSQL** with Neon serverless
- **Drizzle ORM** for type-safe database queries
- **Web Crypto API** for encryption operations

## 📊 Database Schema

### Users Table
```sql
- id: Primary key
- username: Unique username
- passwordHash: Encrypted password
- createdAt: Account creation timestamp
```

### Encryption Logs Table
```sql
- id: Primary key
- filename: Original filename
- fileSize: File size in bytes
- encryptedAt: Encryption timestamp
- decryptedAt: Decryption timestamp (optional)
- ipAddress: Client IP address
- success: Operation success status
```

## 🔧 API Endpoints

- `POST /api/log-encryption` - Log encryption activity
- `POST /api/validate-file` - Validate file metadata
- `GET /api/security-status` - Get current security configuration

## 🔐 Encryption Process

1. **File Upload**: Drag-and-drop or browse files (max 100MB each)
2. **Password Creation**: Enter strong password with real-time validation
3. **Client-Side Encryption**: 
   - Generate random 16-byte salt
   - Derive key using PBKDF2 (100,000 iterations)
   - Generate random 12-byte IV
   - Encrypt with AES-256-GCM
   - Serialize salt + IV + encrypted data
4. **Download**: Receive `.enc` file for secure storage
5. **Audit Logging**: Activity logged to database

## 🛠️ Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run db:push` - Push database schema changes
- `npm run db:studio` - Open Drizzle Studio

### Project Structure

```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # UI components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utility libraries
│   │   └── pages/          # Route components
├── server/                 # Express backend
│   ├── db.ts              # Database connection
│   ├── routes.ts          # API routes
│   └── storage.ts         # Data access layer
├── shared/                 # Shared types and schemas
│   └── schema.ts          # Drizzle database schema
└── drizzle.config.ts      # Database configuration
```

## 🔒 Security Considerations

- **Client-Side Only**: No server-side file processing or storage
- **Memory Safety**: Sensitive data cleared after operations
- **Password Requirements**: Enforced strong password policies
- **File Validation**: Size and type restrictions
- **Audit Trail**: Complete operation logging for compliance

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## ⚠️ Security Notice

This application is designed for legitimate file encryption purposes. The developers are not responsible for any misuse of this software. Always follow applicable laws and regulations when using encryption tools.

## 📧 Support

For questions or issues, please open a GitHub issue or contact the maintainers.

---

**Built with security and privacy in mind** 🔐