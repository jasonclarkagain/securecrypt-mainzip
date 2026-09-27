# Deployment Guide

This guide covers deploying SecureCrypt to various platforms.

## 🚀 Platform Options

### Replit (Recommended for Development)
1. Fork this repository to your Replit account
2. Configure environment variables in Secrets
3. Run `npm run db:push` to set up database
4. Use `npm run dev` to start the application

### Vercel (Recommended for Production)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Configure build settings:
   ```
   Build Command: npm run build
   Output Directory: dist
   Install Command: npm install
   ```
4. Deploy automatically on push to main branch

### Railway
1. Connect your GitHub repository to Railway
2. Add PostgreSQL database service
3. Configure environment variables
4. Deploy with automatic builds

### Docker (Self-Hosted)
Create `Dockerfile`:
```dockerfile
FROM node:20-alpine

WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

EXPOSE 5000
CMD ["npm", "start"]
```

## 🔧 Environment Variables

Required variables for all deployments:

```bash
# Database
DATABASE_URL=postgresql://username:password@hostname:port/database
PGHOST=hostname
PGPORT=5432
PGUSER=username
PGPASSWORD=password
PGDATABASE=database

# Application
NODE_ENV=production
SESSION_SECRET=your-super-secret-session-key
```

## 📊 Database Setup

### Neon (Recommended)
1. Create account at [neon.tech](https://neon.tech)
2. Create new project
3. Copy connection string to `DATABASE_URL`
4. Run `npm run db:push` to create tables

### Supabase
1. Create project at [supabase.com](https://supabase.com)
2. Get PostgreSQL connection details
3. Configure environment variables
4. Run database migrations

### Self-Hosted PostgreSQL
1. Install PostgreSQL on your server
2. Create database and user
3. Configure connection details
4. Ensure network access and security

## 🛡️ Security Configuration

### HTTPS Setup
- Enable HTTPS for all production deployments
- Use SSL certificates (Let's Encrypt recommended)
- Redirect HTTP to HTTPS

### CORS Configuration
Update `server/index.ts` for production domains:
```typescript
app.use(cors({
  origin: ['https://yourdomain.com'],
  credentials: true
}));
```

### Rate Limiting
Add rate limiting for production:
```bash
npm install express-rate-limit
```

## 📈 Performance Optimization

### Client-Side
- Enable gzip compression
- Configure CDN for static assets
- Implement service worker for caching
- Optimize bundle size with tree shaking

### Server-Side
- Use connection pooling for database
- Implement Redis for session storage
- Configure horizontal scaling
- Set up health checks

## 🔍 Monitoring

### Application Monitoring
- Set up error tracking (Sentry recommended)
- Monitor performance metrics
- Configure alerts for downtime
- Track user engagement

### Security Monitoring
- Monitor for failed encryption attempts
- Track unusual file upload patterns
- Set up alerts for security events
- Regular security audits

## 🚦 CI/CD Pipeline

Example GitHub Actions workflow (`.github/workflows/deploy.yml`):

```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '20'
        cache: 'npm'
    
    - name: Install dependencies
      run: npm ci
    
    - name: Run tests
      run: npm test
    
    - name: Build application
      run: npm run build
    
    - name: Deploy to Vercel
      uses: amondnet/vercel-action@v20
      with:
        vercel-token: ${{ secrets.VERCEL_TOKEN }}
        vercel-org-id: ${{ secrets.ORG_ID }}
        vercel-project-id: ${{ secrets.PROJECT_ID }}
```

## 📋 Pre-Deployment Checklist

### Security
- [ ] All environment variables configured
- [ ] HTTPS enabled
- [ ] Database access restricted
- [ ] Rate limiting implemented
- [ ] CORS properly configured

### Performance
- [ ] Build optimization enabled
- [ ] Static assets optimized
- [ ] Database queries optimized
- [ ] Caching configured
- [ ] CDN configured

### Monitoring
- [ ] Error tracking set up
- [ ] Performance monitoring enabled
- [ ] Health checks configured
- [ ] Backup strategy implemented
- [ ] Recovery procedures documented

## 🆘 Troubleshooting

### Common Issues

**Database Connection Errors**
- Verify connection string format
- Check network access and firewall rules
- Ensure database exists and user has permissions

**Build Failures**
- Clear node_modules and reinstall
- Check Node.js version compatibility
- Verify all environment variables are set

**Performance Issues**
- Monitor database query performance
- Check for memory leaks
- Optimize file upload handling
- Configure appropriate server resources

### Support Resources
- GitHub Issues for bug reports
- Documentation wiki
- Community Discord/Slack
- Security contact for vulnerabilities

---

For additional help with deployment, please check our documentation or create an issue on GitHub.