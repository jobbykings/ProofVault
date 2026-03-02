# Contributing to Proofvault

Thank you for your interest in contributing to Proofvault! This document provides guidelines and information for contributors.

## 🚀 Getting Started

### Prerequisites

- Node.js 16.0 or higher
- Git
- Basic knowledge of JavaScript/TypeScript
- Familiarity with blockchain concepts (helpful but not required)

### Development Setup

1. **Fork the repository**
   ```bash
   # Fork the repository on GitHub, then clone your fork
   git clone https://github.com/YOUR_USERNAME/Proofvault.git
   cd Proofvault
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment**
   ```bash
   cp .env.example .env
   # Edit .env with your development configuration
   ```

4. **Start development**
   ```bash
   npm run dev
   ```

## 📋 How to Contribute

### Reporting Bugs

- Use the [GitHub Issues](https://github.com/JobCharis/Proofvault/issues) page
- Provide a clear and descriptive title
- Include steps to reproduce the issue
- Add relevant error messages, screenshots, or logs
- Specify your environment (OS, Node.js version, etc.)

### Suggesting Features

- Open an issue with the "enhancement" label
- Provide a clear description of the feature
- Explain the use case and why it would be valuable
- Consider whether it fits the project's scope and goals

### Submitting Pull Requests

1. **Create a new branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

2. **Make your changes**
   - Follow the existing code style and conventions
   - Add tests for new functionality
   - Update documentation as needed

3. **Run tests**
   ```bash
   npm test
   npm run lint
   ```

4. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add your feature description"
   ```

5. **Push and create PR**
   ```bash
   git push origin feature/your-feature-name
   # Create a pull request on GitHub
   ```

## 📝 Code Style Guidelines

### JavaScript/TypeScript

- Use ES6+ features
- Follow [StandardJS](https://standardjs.com/) style guide
- Use meaningful variable and function names
- Add JSDoc comments for functions and classes

### Example Code Style

```javascript
/**
 * Adds a new sensor to the Proofvault system
 * @param {Object} sensorConfig - Sensor configuration object
 * @param {string} sensorConfig.type - Type of sensor (motion, door, fire, etc.)
 * @param {string} sensorConfig.location - Physical location of the sensor
 * @param {number} sensorConfig.threshold - Sensitivity threshold
 * @returns {Promise<Sensor>} Returns the created sensor instance
 */
async function addSensor(sensorConfig) {
  validateSensorConfig(sensorConfig)
  
  const sensor = new Sensor(sensorConfig)
  await sensor.initialize()
  
  return sensor
}
```

### Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

- `feat:` for new features
- `fix:` for bug fixes
- `docs:` for documentation changes
- `style:` for code style changes
- `refactor:` for code refactoring
- `test:` for adding or updating tests
- `chore:` for maintenance tasks

Examples:
```
feat: add support for vibration sensors
fix: resolve memory leak in event processing
docs: update API documentation
```

## 🧪 Testing

### Running Tests

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- sensor.test.js

# Run tests in watch mode
npm run test:watch
```

### Writing Tests

- Write unit tests for all new functions
- Add integration tests for API endpoints
- Test error cases and edge conditions
- Aim for high code coverage (>80%)

### Test Structure

```javascript
const { expect } = require('chai')
const Proofvault = require('../src/proofvault')

describe('Sensor Management', () => {
  let proofvault

  beforeEach(() => {
    proofvault = new Proofvault()
  })

  describe('addSensor', () => {
    it('should add a new sensor successfully', async () => {
      const sensorConfig = {
        type: 'motion',
        location: 'Test Room',
        threshold: 0.8
      }

      const sensor = await proofvault.addSensor(sensorConfig)
      
      expect(sensor).to.have.property('id')
      expect(sensor.type).to.equal('motion')
    })

    it('should throw error for invalid sensor type', async () => {
      const sensorConfig = {
        type: 'invalid',
        location: 'Test Room'
      }

      try {
        await proofvault.addSensor(sensorConfig)
        expect.fail('Should have thrown an error')
      } catch (error) {
        expect(error.message).to.include('Invalid sensor type')
      }
    })
  })
})
```

## 📚 Documentation

### Updating Documentation

- Keep README.md up to date with new features
- Update API documentation for any API changes
- Add inline code comments for complex logic
- Create examples for new functionality

### Documentation Structure

```
docs/
├── api/           # API documentation
├── guides/        # User guides and tutorials
├── examples/      # Code examples
└── architecture/  # System architecture docs
```

## 🔧 Development Tools

### Recommended VS Code Extensions

- ES7+ React/Redux/React-Native snippets
- Prettier - Code formatter
- ESLint
- GitLens
- Thunder Client (for API testing)

### Useful Scripts

```bash
# Format code
npm run format

# Run linter
npm run lint

# Build for production
npm run build

# Start development server with hot reload
npm run dev
```

## 🤝 Code Review Process

### Review Guidelines

- All PRs require at least one approval
- Ensure tests pass and coverage is maintained
- Check for security vulnerabilities
- Verify documentation is updated
- Ensure code follows project conventions

### Review Checklist

- [ ] Code follows style guidelines
- [ ] Tests are included and passing
- [ ] Documentation is updated
- [ ] No breaking changes (or clearly documented)
- [ ] Security considerations addressed
- [ ] Performance impact considered

## 🏆 Recognition

Contributors will be recognized in:

- README.md contributors section
- Release notes for significant contributions
- Project website (when available)
- Annual contributor highlights

## 📞 Getting Help

- **Discord**: Join our development community
- **GitHub Issues**: For bugs and feature requests
- **Email**: dev@proofvault.io for development questions

## 📄 License

By contributing to this project, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Proofvault! Your help makes decentralized sensor logging more accessible and secure for everyone. 🚀
