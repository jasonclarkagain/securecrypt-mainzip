# Contributing to SecureCrypt

Thank you for your interest in contributing to SecureCrypt! This document provides guidelines for contributing to this security-focused project.

## 🔒 Security First

Since this is a security application, all contributions must maintain the highest standards:

- **Code Review Required**: All changes must be reviewed by maintainers
- **Security Testing**: Encryption/decryption functionality must be thoroughly tested
- **No Vulnerabilities**: Run security scans before submitting PRs
- **Documentation**: Security-related changes require detailed documentation

## 🚀 Getting Started

1. Fork the repository
2. Clone your fork locally
3. Create a new branch for your feature/fix
4. Make your changes
5. Test thoroughly
6. Submit a pull request

## 📋 Development Guidelines

### Code Standards
- Follow TypeScript best practices
- Use the existing ESLint and Prettier configurations
- Maintain 100% type safety
- Write descriptive commit messages

### Testing Requirements
- Test all encryption/decryption operations
- Verify password strength validation
- Check file upload/download functionality
- Ensure database operations work correctly

### Security Requirements
- Never log sensitive data (passwords, file contents)
- Validate all user inputs
- Use secure random number generation
- Clear sensitive data from memory after use

## 🔧 Development Setup

```bash
# Install dependencies
npm install

# Set up environment
cp .env.example .env
# Edit .env with your database credentials

# Push database schema
npm run db:push

# Start development server
npm run dev
```

## 📝 Pull Request Process

1. **Branch Naming**: Use descriptive names like `feature/add-batch-encryption` or `fix/password-validation`

2. **Commit Messages**: Follow conventional commits format:
   ```
   feat: add batch file encryption support
   fix: resolve password strength indicator bug
   docs: update API documentation
   security: patch XSS vulnerability
   ```

3. **PR Description**: Include:
   - What changes were made
   - Why the changes were necessary
   - How to test the changes
   - Any security implications

4. **Testing**: Ensure all tests pass and add new tests for new features

## 🛡️ Security Contributions

### Reporting Security Issues
- **DO NOT** create public issues for security vulnerabilities
- Email security issues to: [security@yourproject.com]
- Include detailed steps to reproduce
- Allow time for patching before public disclosure

### Security Review Checklist
- [ ] No hardcoded secrets or keys
- [ ] Input validation on all user data
- [ ] Proper error handling without information leakage
- [ ] Secure random number generation
- [ ] Memory cleared after cryptographic operations
- [ ] No client-side storage of sensitive data

## 📊 Code Review Criteria

### Functionality
- [ ] Code works as intended
- [ ] No breaking changes to existing features
- [ ] Proper error handling
- [ ] Performance considerations

### Security
- [ ] No security vulnerabilities introduced
- [ ] Follows secure coding practices
- [ ] Cryptographic operations are correct
- [ ] Input validation is comprehensive

### Code Quality
- [ ] TypeScript types are correct
- [ ] Code is well-documented
- [ ] Follows project conventions
- [ ] No console.log statements in production code

## 🔍 Areas for Contribution

### High Priority
- Enhanced password policy enforcement
- Additional file format support
- Performance optimizations
- Accessibility improvements

### Medium Priority
- UI/UX enhancements
- Additional encryption algorithms
- Batch operation improvements
- Mobile responsiveness

### Documentation
- API documentation improvements
- Security best practices guide
- Deployment guides
- Video tutorials

## 📚 Resources

- [Web Crypto API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API)
- [OWASP Cryptographic Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)
- [React TypeScript Best Practices](https://react-typescript-cheatsheet.netlify.app/)
- [Drizzle ORM Documentation](https://orm.drizzle.team/)

## ❓ Questions?

If you have questions about contributing:
1. Check existing issues and discussions
2. Create a new issue with the `question` label
3. Join our community discussions

## 📜 Code of Conduct

This project follows a strict code of conduct:
- Be respectful and professional
- Focus on constructive feedback
- Prioritize security and user safety
- Follow responsible disclosure for security issues

Thank you for helping make SecureCrypt more secure and better for everyone!