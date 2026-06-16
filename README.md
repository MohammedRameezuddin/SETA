# SETA RepairHub - Unified Repair Marketplace Platform

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/seta-repairhub/repairhub/actions)
[![Website](https://img.shields.io/badge/website-live-brightgreen.svg)](https://seta-ai-frontend.vercel.app)
[![Deployment](https://img.shields.io/badge/deployment-Vercel-blue.svg)](https://vercel.com)

## Live Demo

🌐 **Production Website**: [https://seta-ai-frontend.vercel.app](https://seta-ai-frontend.vercel.app)

### Access Portals Directly:
- **Customer Portal**: [https://seta-ai-frontend.vercel.app/repairhub/customer](https://seta-ai-frontend.vercel.app/repairhub/customer)
- **Technician Portal**: [https://seta-ai-frontend.vercel.app/repairhub/technician](https://seta-ai-frontend.vercel.app/repairhub/technician)
- **Admin Portal**: [https://seta-ai-frontend.vercel.app/repairhub/admin](https://seta-ai-frontend.vercel.app/repairhub/admin)

## Overview

SETA RepairHub is a comprehensive repair marketplace platform that connects customers with qualified technicians for electronics repair services. The platform enables customers to easily request repairs, select from qualified technicians, track job progress in real-time, and complete secure payments - all within a single integrated system.

## Key Features

### Customer Portal
- **Intelligent Repair Requests**: AI-assisted issue diagnosis and technician matching
- **Technician Selection**: View nearby technicians with ratings, pricing, and availability
- **Real-time Tracking**: Live updates on job status from pickup to delivery
- **Secure Payments**: Multiple payment options with escrow protection
- **Quality Assurance**: Post-completion feedback and warranty management

### Technician Portal
- **Job Management**: Comprehensive workflow from pickup to delivery
- **Diagnostic Tools**: AI-assisted diagnosis and repair suggestions
- **Inventory Management**: Parts tracking and supplier integration
- **Earnings Dashboard**: Payment tracking and commission management
- **Performance Analytics**: Rating tracking and job completion metrics

### Admin Features
- **User Management**: Customer and technician verification
- **Fraud Prevention**: IMEI validation and suspicious activity detection
- **Dispute Resolution**: Escalation and mediation tools
- **Business Analytics**: Revenue tracking and performance metrics
- **System Configuration**: Platform settings and policy management

## System Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Customers     │    │  Technicians    │    │     Admins      │
│   (Web/Mobile)  │    │   (Mobile App)  │    │   (Web Portal)  │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │      API Gateway        │
                    │      (FastAPI)          │
                    └────────────┬────────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
┌───────▼────────┐     ┌────────▼────────┐    ┌──────────▼───────┐
│  PostgreSQL    │     │     Redis       │    │   AWS S3         │
│   Database     │     │    Caching      │    │  File Storage    │
└────────────────┘     └─────────────────┘    └──────────────────┘
```

## Technology Stack

### Frontend
- **Framework**: React with Vite
- **State Management**: Redux Toolkit
- **UI Library**: Tailwind CSS
- **Real-time**: Socket.IO
- **Maps**: Leaflet.js

### Backend
- **Framework**: FastAPI (Python 3.9+)
- **Database**: PostgreSQL with SQLAlchemy ORM
- **Caching**: Redis
- **Authentication**: Clerk
- **File Storage**: AWS S3
- **Background Jobs**: Celery

### Mobile
- **Framework**: React Native
- **State Management**: Redux Toolkit
- **Navigation**: React Navigation

### Infrastructure
- **Hosting**: AWS (EC2, RDS, S3, ElastiCache)
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Monitoring**: Prometheus + Grafana
- **CI/CD**: GitHub Actions

## Quick Start

### Prerequisites
- Node.js 16+
- Python 3.9+
- PostgreSQL 13+
- Redis 6+
- Docker (optional, for containerized deployment)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/seta-repairhub/repairhub.git
cd repairhub
```

2. **Install frontend dependencies:**
```bash
npm install
```

3. **Install backend dependencies:**
```bash
cd backend
pip install -r requirements.txt
```

4. **Set up environment variables:**
```bash
# Copy and configure environment files
cp .env.example .env
cp backend/.env.example backend/.env
```

5. **Start the development servers:**
```bash
# Terminal 1: Start frontend
npm run dev

# Terminal 2: Start backend
cd backend
uvicorn main:app --reload

# Terminal 3: Start worker (if needed)
celery -A app.celery worker --loglevel=info
```

### Database Setup
```bash
# Create database
createdb repairhub

# Run migrations
cd backend
alembic upgrade head
```

## API Documentation

Comprehensive API documentation is available at:
- **Local**: http://localhost:8000/docs
- **Production**: https://api.setarepairhub.com/docs

See [API_DOCUMENTATION.md](API_DOCUMENTATION.md) for detailed API specifications.

## Project Structure

```
repairhub/
├── backend/                 # FastAPI backend
│   ├── routers/            # API route handlers
│   ├── services/           # Business logic
│   ├── models/             # Data models
│   ├── database/           # Database configuration
│   ├── utils/              # Utility functions
│   └── main.py            # Application entry point
├── src/                    # Frontend source code
│   ├── components/         # React components
│   ├── pages/              # Page components
│   ├── services/           # API service clients
│   ├── hooks/              # Custom React hooks
│   └── utils/              # Frontend utilities
├── mobile/                 # React Native mobile app
├── docs/                   # Documentation
└── tests/                  # Test suites
```

## Development Guidelines

### Code Standards
- **Frontend**: Follow Airbnb JavaScript Style Guide
- **Backend**: Follow PEP 8 Python Style Guide
- **Testing**: Maintain 80%+ code coverage
- **Documentation**: Keep API docs and code comments up to date

### Git Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a pull request

### Pull Request Process
1. Ensure all tests pass
2. Update documentation if needed
3. Follow the PR template
4. Request review from team members

## Testing

### Running Tests
```bash
# Frontend unit tests
npm run test:unit

# Frontend E2E tests
npm run test:e2e

# Backend tests
cd backend
pytest

# Integration tests
npm run test:integration
```

### Test Coverage
```bash
# Generate coverage report
npm run test:coverage
```

See [TESTING_STRATEGY.md](TESTING_STRATEGY.md) for comprehensive testing guidelines.

## Deployment

### Production Deployment
```bash
# Build frontend for production
npm run build

# Deploy backend
cd backend
gunicorn main:app -w 4 -b 0.0.0.0:8000
```

See [DEPLOYMENT_OPERATIONS.md](DEPLOYMENT_OPERATIONS.md) for detailed deployment procedures.

## Monitoring and Maintenance

### Health Checks
- **API Health**: `GET /health`
- **Database**: Connection and query performance
- **Cache**: Redis connectivity and performance
- **File Storage**: S3 bucket accessibility

### Logging
- Structured JSON logging for all services
- Centralized log aggregation with ELK stack
- Real-time monitoring with Grafana dashboards

See [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md) for complete system architecture details.

## Security

### Authentication
- OAuth 2.0 integration with Clerk
- JWT token management
- Role-based access control

### Data Protection
- AES-256 encryption for sensitive data
- TLS 1.3 for all communications
- Regular security audits

### Compliance
- GDPR compliant data handling
- PCI DSS compliant payment processing
- HIPAA considerations for sensitive information

See [SECURITY.md](SECURITY.md) for detailed security documentation.

## Contributing

We welcome contributions from the community! Please read our [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support, please open an issue on GitHub or contact our team at support@setarepairhub.com.

## Acknowledgments

- Thanks to all contributors who have helped build this platform
- Special recognition to the open-source community for the tools and libraries we depend on
- Gratitude to our early adopters and beta testers for their valuable feedback

## Project Documentation

For comprehensive information about the system, please refer to the following documentation:

- [SETA_REPAIRHUB_REVIEW.md](SETA_REPAIRHUB_REVIEW.md) - System review and enhancement plan
- [SETA_IMPLEMENTATION_PLAN.md](SETA_IMPLEMENTATION_PLAN.md) - Detailed implementation roadmap
- [DATABASE_SCHEMA.md](DATABASE_SCHEMA.md) - Complete database design
- [API_DOCUMENTATION.md](API_DOCUMENTATION.md) - RESTful API specifications
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md) - System architecture details
- [TESTING_STRATEGY.md](TESTING_STRATEGY.md) - Comprehensive testing approach
- [DEPLOYMENT_OPERATIONS.md](DEPLOYMENT_OPERATIONS.md) - Deployment and operations guide

## Getting Started with Current Implementation

The current implementation includes:

1. **Working Customer Portal**:
   - Create repair requests
   - View technician matches
   - Track job progress

2. **Functional Technician Portal**:
   - Accept/reject jobs
   - Update job status
   - Manage work completion

3. **Basic Admin Features**:
   - Technician application review
   - Dashboard statistics

To run the current implementation:

1. Start the backend server:
```bash
cd backend
python main.py
```

2. Start the frontend development server:
```bash
npm run dev
```

3. Visit `http://localhost:5176` in your browser

The system will automatically connect to the backend running on `http://localhost:8006`.
---

## 🤖 Contribution Agent

An automated GitHub Actions workflow maintains a daily contribution streak by making meaningful, pre-configured changes to the repository.

### How It Works

| | |
|-|-|
| **Schedule** | Runs at **1:00 AM IST** every day (`cron: '30 19 * * *'` UTC) |
| **Manual trigger** | `Actions → Contribution Agent → Run workflow` |
| **Target** | 10 commits per day by default (configurable: 10 / 15 / 20) |
| **Hard cap** | Never more than 20 commits per run |
| **Fallback** | If the task queue is empty, makes 1 maintenance commit to `CONTRIBUTIONS_TRACKER.txt` |

### Task Queue

Pending tasks live in `.github/contribution-tasks.json`. To add more work:

```json
{
  "id": "task-NNN",
  "type": "docs",
  "description": "Short description (used as the commit message)",
  "file": "path/to/file.md",
  "action": "create_file",
  "content": "# File heading\n\nBody text here.",
  "status": "pending"
}
```

**Supported `action` values:**

| Action | What it does |
|--------|--------------|
| `create_file` | Creates the file if it does not yet exist |
| `append_to_file` | Appends `content` to the end of the file |
| `prepend_to_file` | Inserts `content` at the beginning of the file |

### Observability

* **Job summary** – a Markdown table is written to the Actions run page after every execution.
* **Log artifact** – the full run log is uploaded as `contribution-log-YYYY-MM-DD` with 30-day retention.

### Required Permissions

The workflow uses the built-in `GITHUB_TOKEN` with `contents: write`. No extra secrets are needed.

> Full documentation: [`docs/guides/contribution-agent.md`](docs/guides/contribution-agent.md)
