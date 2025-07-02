# Postal Installation Tools

Official installation and management tools for Postal mail server deployment and maintenance.

## 🚀 Features

- **📦 Standard Deployment** - Complete Postal server installation and setup
- **🔧 Repository Flexibility** - Support for different Postal source repositories
- **🌿 Environment Management** - Deploy across development, staging, and production
- **⚡ Automated Setup** - One-command bootstrap and configuration
- **🔄 Easy Updates** - Seamless upgrade management and version control

## 📋 Quick Start

### Installation
```bash
git clone git@github.com:PhishSpot/postal-install.git /opt/postal/install
sudo ln -s /opt/postal/install/bin/postal /usr/bin/postal
```

### Deployment Options
```bash
# Standard deployment (official repository)
postal bootstrap postal.yourdomain.com

# Custom repository (default main)
GITHUB_URL=https://github.com/PhishSpot/postal-server postal bootstrap postal.yourdomain.com

# Custom repository with specific branch
GITHUB_URL=https://github.com/PhishSpot/postal-server GITHUB_BRANCH=develop postal bootstrap develop.yourdomain.com
```

## 🛠️ Prerequisites

Install dependencies for your Postal version:

```bash
# For Postal v2
curl https://raw.githubusercontent.com/postalserver/install/main/prerequisites/install-ubuntu.v2.sh | bash

# For Postal v3  
curl https://raw.githubusercontent.com/postalserver/install/main/prerequisites/install-ubuntu.v3.sh | bash
```

**⚠️ Note:** These scripts use insecure passwords - not for production.

## 🔧 Environment Variables

| Variable | Description | Default | Example |
|----------|-------------|---------|---------|
| `GITHUB_URL` | Repository URL | `postalserver/postal` | `https://github.com/PhishSpot/postal-server` |
| `GITHUB_BRANCH` | Branch/version | `main` | `staging`, `develop` |

## 📚 Commands

### Core Operations
```bash
postal start                    # Start services
postal stop                     # Stop services
postal status                   # View status
postal logs [service]           # View logs
postal upgrade [version]        # Update installation
```

### Setup & Management
```bash
postal bootstrap hostname      # Initial setup
postal initialize              # Create database
postal make-user               # Create admin user
postal console                 # Rails console
```

## 🎯 Multi-Environment Setup

```bash
# Development environment
GITHUB_URL=https://github.com/PhishSpot/postal-server GITHUB_BRANCH=develop postal bootstrap develop.company.com

# Staging environment
GITHUB_URL=https://github.com/PhishSpot/postal-server GITHUB_BRANCH=staging postal bootstrap staging.company.com

# Production environment
GITHUB_URL=https://github.com/PhishSpot/postal-server GITHUB_BRANCH=main postal bootstrap mail.company.com
```

## 🔄 How It Works

### Version Management
- **Official Repository**: Uses GitHub releases (`postalserver/postal:3.3.4`)
- **Alternative Repository**: Uses branch names (`PhishSpot/postal-server:main`)

### Docker Configuration
The installer automatically configures `docker-compose.yml`:
```yaml
# Example: postalserver/postal:3.3.4
# Example: PhishSpot/postal-server:main
```

## 🆘 Troubleshooting

### Common Issues
```bash
# Repository access errors
ssh -T git@github.com

# Docker image verification
docker pull PhishSpot/postal-server:main

# Reset installation
postal stop && rm docker-compose.yml && postal upgrade
```

### Debug Commands
```bash
postal status              # Check services
postal logs web           # View web logs
postal bash web           # Container access
```

## 🔒 Security Notes

- Use secure repositories for production deployments
- Implement proper access controls
- Scan Docker images for vulnerabilities
- Use protected branches for production environments

## 📖 Documentation

For complete Postal documentation: [docs.postalserver.io](https://docs.postalserver.io)

---

**Professional installation tools for reliable Postal mail server deployment and management.**