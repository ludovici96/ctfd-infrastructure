# Software Provisioning and Configuration Management

A multi-VM infrastructure setup for CTFd platform using Vagrant and Ansible for automated provisioning and configuration management.

## Project Overview

This project implements a complete CTFd platform infrastructure with the following components:
- Redis for caching
- PostgreSQL database
- CTFd application server
- Nginx reverse proxy

## Architecture

The infrastructure consists of four VMs:
- Redis VM (192.168.56.10)
- PostgreSQL DB VM (192.168.56.11)
- CTFd Application VM (192.168.56.12)
- Nginx Proxy VM (192.168.56.13)

## Prerequisites

- Vagrant
- VirtualBox
- Ansible
- Git

## Setup

1. Clone the repository:
```bash
git clone https://github.com/ludovici96/ctfd-infrastructure.git
cd ctfd-infrastructure
```

2. Start the virtual machines:
```bash
vagrant up
```

## Project Structure

```
/
├── Vagrantfile                  # VM configuration
├── ansible/
│   ├── inventory/              # Ansible inventory files
│   ├── playbook.yml           # Main playbook
│   ├── group_vars/            # Variable definitions
│   └── roles/                 # Role-specific tasks
│       ├── common/           # Common configurations
│       ├── redis/            # Redis server setup
│       ├── postgresql/       # Database setup
│       ├── ctfd/            # CTFd application
│       └── nginx/           # Nginx reverse proxy
└── README.md
```

## Components

- **Redis**: Provides caching services for CTFd
- **PostgreSQL**: Main database for CTFd platform
- **CTFd**: The CTF platform application server
- **Nginx**: Reverse proxy and load balancer

## Usage

1. Access the CTFd platform through: http://localhost
2. The platform is proxied through Nginx on port 80
3. Database and Redis services are internally accessible

## Configuration

Key configurations can be modified in:
- `ansible/group_vars/all/vars.yml` for global settings
- Individual role directories for component-specific settings

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License


