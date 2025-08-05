# Service Credentials Documentation

This document lists the credentials and configuration for services defined in `docker-compose.yml`. All settings are configured via environment variables in `.env`.

## Environment Variables

Configure these in your `.env` file:
- `DB_PASSWORD`: MySQL root password
- `REDIS_PORT`: Redis port (default: 6379)
- `RABBITMQ_PORT`: RabbitMQ AMQP port (default: 5672)
- `RABBITMQ_MGMT_PORT`: RabbitMQ management port (default: 15672)
- `PHPMYADMIN_PORT`: phpMyAdmin web port (default: 8080)
- `REDISINSIGHT_PORT`: RedisInsight web port (default: 5540)

## Services

This document lists the credentials required to connect to services defined in `docker-compose.yml`, including Laravel .env configuration.

## Services

### MySQL
- **Host**: `mysql` (within Docker network) or `localhost`
- **Port**: `${DB_PORT}` (default: 3306)
- **Username**: `root`
- **Password**: Set via `DB_PASSWORD` in `.env`
- **Connection URL**: `mysql://root:${DB_PASSWORD}@mysql:${DB_PORT}`

### Redis
- **Host**: `redis` (within Docker network) or `localhost`
- **Port**: `${REDIS_PORT}` (default: 6379)
- **No authentication required**

### RabbitMQ
- **Host**: `rabbitmq` (within Docker network) or `localhost`
- **Management UI Port**: `${RABBITMQ_MGMT_PORT}` (default: 15672)
- **AMQP Port**: `${RABBITMQ_PORT}` (default: 5672)
- **Default Username**: `${RABBITMQ_LOGIN}` (default: guest)
- **Default Password**: `${RABBITMQ_PASSWORD}` (default: guest)
- **Management URL**: `http://localhost:${RABBITMQ_MGMT_PORT}`

### phpMyAdmin
- **URL**: `http://localhost:${PHPMYADMIN_PORT}`
- **MySQL Host**: `mysql` (auto-configured)
- **Uses MySQL credentials defined above**

### MongoDB
- **Host**: `mongodb` (within Docker network) or `localhost`
- **Port**: `27017`
- **No authentication required**
- **Connection URL**: `mongodb://mongodb:27017`

## Volumes
All services use Docker volumes for persistent storage:
- MySQL: `mysql_data`
- Redis: `redis_data`
- RabbitMQ: `rabbitmq_data`
- MongoDB: `mongo_data`

## Network
All services are connected to `dev_network` bridge network.