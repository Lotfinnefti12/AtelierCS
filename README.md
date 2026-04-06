# Symfony 8 Development Container

A complete development environment for Symfony 8 with MySQL/PostgreSQL, including academic documentation and curl testing examples.

## Quick Start

1. **Clone and Setup**
   ```bash
   git clone <repository-url>
   cd symfony-dev-container
   ```

2. **Copy Environment Configuration**
   ```bash
   cp .env.example .env
   # Edit .env to configure your database and settings
   ```

3. **Start Development Environment**
   ```bash
   docker-compose up -d
   ```

4. **Access Services**
   - **Symfony App**: http://localhost:8000
   - **phpMyAdmin**: http://localhost:8080
   - **MySQL**: localhost:3306
   - **PostgreSQL**: localhost:5432

## Features

- **Symfony 8 Framework** with latest PHP 8.4
- **Database Flexibility**: Switch between MySQL and PostgreSQL
- **Development Tools**: phpMyAdmin, workspace container with tools
- **Xdebug Support**: Integrated debugging capabilities
- **Academic Documentation**: Complete setup and usage guide
- **REST API Testing**: Curl examples for API testing

## Database Configuration

### Switching Databases

1. **Edit .env file**
   ```bash
   DATABASE_TYPE=mysql  # or 'postgres'
   ```

2. **Restart Services**
   ```bash
   docker-compose down
   docker-compose up -d
   ```

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_TYPE` | Database type (mysql/postgres) | mysql |
| `DATABASE_NAME` | Database name | symfony_db |
| `DATABASE_USER` | Database user | symfony |
| `DATABASE_PASSWORD` | Database password | symfony |
| `DATABASE_ROOT_PASSWORD` | Root password (MySQL) | secret |

## Development Workflow

### Using Workspace Container

```bash
# Access workspace
docker-compose exec workspace bash

# Run Symfony commands
php bin/console doctrine:migrations:migrate
php bin/console make:entity
php bin/console make:controller
```

### API Development

1. **Create Entity**
   ```bash
docker-compose exec workspace bash
php bin/console make:entity Product
```

2. **Generate API**
   ```bash
   php bin/console make:crud Product
   ```

3. **Test API**
   ```bash
   curl http://localhost:8000/api/products
   ```

## Academic Documentation

Complete documentation is available in the `academic-documentation/` directory:

- `symfony-docker-setup.md` - Setup and configuration guide
- `mysql-configuration.md` - Database setup and management
- `curl-testing-guide.md` - API testing with curl examples

## Services

| Service | Port | Description |
|---------|------|-------------|
| Symfony App | 8000 | Main application |
| phpMyAdmin | 8080 | Database administration |
| MySQL | 3306 | MySQL database |
| PostgreSQL | 5432 | PostgreSQL database |

## Development Commands

```bash
# Start all services
docker-compose up -d

# Stop all services
docker-compose down

# View logs
docker-compose logs -f

# Access workspace
docker-compose exec workspace bash

# Run database migrations
docker-compose exec php-fpm php bin/console doctrine:migrations:migrate

# Clear cache
docker-compose exec php-fpm php bin/console cache:clear
```

## Security Considerations

- **Environment Variables**: Store sensitive data in .env files
- **Database Users**: Use specific users instead of root
- **SSL/TLS**: Configure SSL for production
- **Input Validation**: Validate all user inputs
- **Authentication**: Implement proper authentication mechanisms

## Performance Optimization

- **Database Indexing**: Create appropriate indexes
- **Caching**: Implement caching strategies
- **Image Optimization**: Use optimized Docker images
- **Resource Limits**: Set appropriate resource limits

## Troubleshooting

### Common Issues

1. **Database Connection Issues**
   - Check DATABASE_TYPE in .env
   - Verify database service is running
   - Check port mappings

2. **Permission Issues**
   - Ensure proper file permissions
   - Check user configurations in containers

3. **Cache Issues**
   - Clear Symfony cache
   - Rebuild containers if needed

### Logs

```bash
# View all logs
docker-compose logs

# View specific service logs
docker-compose logs -f php-fpm
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details."# AtelierCS" 
