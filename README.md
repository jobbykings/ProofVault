# Proofvault

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)
![Version](https://img.shields.io/badge/version-1.0.0-orange.svg)

ProofVault is a decentralized system that captures real-world sensor events — like door access, motion, fire, or vibration — and logs them immutably on-chain. Designed for environments where trust, traceability, and proof of physical occurrence are critical, it acts as a cryptographic black box for the physical world.

## 🌟 Features

- **Decentralized Event Logging**: Capture sensor data and store it immutably on blockchain
- **Multi-Sensor Support**: Door access, motion detection, fire alarms, vibration sensors
- **Cryptographic Proof**: Each event is cryptographically signed and timestamped
- **Real-time Monitoring**: Live dashboard for sensor status and event history
- **Tamper-Proof**: Once logged, events cannot be altered or deleted
- **API Access**: RESTful API for integration with existing systems

## 🚀 Quick Start

### Prerequisites

- Node.js 16.0 or higher
- npm or yarn
- Stellar wallet (Freighter, Ledger, etc.)
- Supported sensor hardware

### Installation

```bash
# Clone the repository
git clone https://github.com/JobCharis/Proofvault.git
cd Proofvault

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Edit .env with your configuration

# Run the application
npm start
```

### Configuration

Create a `.env` file with the following variables:

```env
# Stellar Configuration
STELLAR_NETWORK=public
HORIZON_URL=https://horizon.stellar.org
SECRET_KEY=your_stellar_secret_key
PUBLIC_KEY=your_stellar_public_key

# Sensor Configuration
SENSOR_API_KEY=your_sensor_api_key
SENSOR_ENDPOINT=http://localhost:8080

# Application Settings
PORT=3000
NODE_ENV=production
```

## 📖 Usage

### Adding a New Sensor

```javascript
const proofvault = require('proofvault');

// Initialize sensor
const sensor = await proofvault.addSensor({
  type: 'motion',
  location: 'Entrance Hall',
  threshold: 0.8
});

// Start monitoring
sensor.startMonitoring();
```

### Querying Events

```javascript
// Get events from last 24 hours
const events = await proofvault.getEvents({
  startTime: Date.now() - 24 * 60 * 60 * 1000,
  endTime: Date.now(),
  sensorType: 'motion'
});
```

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Physical      │    │   ProofVault    │    │   Blockchain    │
│   Sensors       │───▶│   Gateway       │───▶│   Network       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌─────────────────┐
                       │   Monitoring    │
                       │   Dashboard     │
                       └─────────────────┘
```

## 🔧 Technology Stack

- **Backend**: Node.js, Express.js
- **Blockchain**: Stellar, Soroban Smart Contracts
- **Database**: MongoDB (for caching)
- **Frontend**: React.js
- **IoT**: MQTT, WebSockets
- **Security**: JWT, Stellar SDK

## 🧪 Testing

```bash
# Run unit tests
npm test

# Run integration tests
npm run test:integration

# Run with coverage
npm run test:coverage
```

## 📊 Roadmap

- [ ] Support for additional blockchain networks
- [ ] Mobile application for remote monitoring
- [ ] Advanced analytics and ML-based anomaly detection
- [ ] Hardware SDK for custom sensor development
- [ ] Multi-tenant support for organizations

## 🤝 Contributing

We welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### Development Setup

```bash
# Install development dependencies
npm install --dev

# Set up pre-commit hooks
npm run setup:hooks

# Start development server
npm run dev
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Stellar Development Foundation for blockchain infrastructure
- Soroban for secure smart contract templates
- The Stellar community for tools and support
- All contributors who help improve this project

## 📞 Support

- 📧 Email: support@proofvault.io
- 💬 Discord: [Join our community](https://discord.gg/proofvault)
- 🐛 Issues: [GitHub Issues](https://github.com/JobCharis/Proofvault/issues)

## 🔗 Links

- [Website](https://proofvault.io)
- [Documentation](https://docs.proofvault.io)
- [Demo](https://demo.proofvault.io)

---

**Built with ❤️ for a more transparent and trustworthy world**
