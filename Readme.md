# Cat Search Application 🐾

![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange)
![Vue](https://img.shields.io/badge/Vue-Frontend-green)
![Node.js](https://img.shields.io/badge/Node.js-Backend-brightgreen)

A full-stack application for managing and searching cat information with:

- **Vue.js Frontend** - Modern, responsive web interface
- **Node.js Backend** - RESTful API service
- **MySQL Database** - Persistent data storage
- **phpMyAdmin** - Database management GUI

## 🌟 Features

- Dockerized development environment
- Automatic health checks for database
- Persistent data storage
- Hot-reloading during development
- Git submodule architecture

## 🚀 Quick Start

### Prerequisites

- Docker Engine 20.10+
- Docker Compose 1.29+
- Git 2.20+

````bash
# Clone with submodules
git clone --recurse-submodules https://github.com/yourusername/cat-search.git
cd cat-search

# Start services
docker-compose up -d


### **Docker Compose Explanation**

## 🐳 Docker Compose Explained

```yaml
version: '3.8'
services:
  mysql:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: admin123
      MYSQL_DATABASE: cat_search_db
    healthcheck:
      test: ["CMD", "mysqladmin", "ping"]
      interval: 5s
      timeout: 10s
      retries: 5
    volumes:
      - mysql-data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    depends_on:
      - mysql

  backend:
    build: ./backend/Api_Cats
    ports:
      - "3000:3000"
    volumes:
      - ./backend/Api_Cats:/usr/src/app
      - /usr/src/app/node_modules

  frontend:
    build: ./frontend/front-end_api_cats
    environment:
      VITE_API_BASE_URL: http://backend:3000
    ports:
      - "5173:5173"

volumes:
  mysql-data:
````

### **Maintenance Section**

## 🔧 Maintenance Commands

````bash
# Update submodules
git submodule update --remote

# Clean Docker resources (WARNING: removes unused containers/images)
docker system prune -a --volumes

# Check service status
docker-compose ps

# View backend logs
docker-compose logs -f backend

### **Project Structure**
```markdown
## 📂 Project Structure
cat-search/
├── backend/ # Node.js API (submodule)
│ ├── src/ # Source code
│ └── .env # Environment variables
├── frontend/ # Vue.js app (submodule)
│ ├── src/ # Vue components
│ └── vite.config.js # Build configuration
├── docker-compose.yaml
└── README.md
````

## Clean all containers

```bash
 cd app

 sudo docker-compose down

 sudo docker system prune -a --volumes

 sudo docker-compose up -d OR  sudo docker-compose up

```

## 🔒 Security Notes

- Always change default credentials in production
- Use environment variables for sensitive data
- Regularly update your Docker images
- Never commit .env files to version control
