# Service Credentials Documentation

This document lists the credentials required to connect to services defined in `docker-compose.yml`, including Laravel .env configuration.

## Services

### MySQL
- **Host**: `mysql` (within Docker network) or `localhost`
- **Port**: `3306`
- **Username**: `root`
- **Password**: `rootpassword`
- **Connection URL**: `mysql://root:rootpassword@mysql:3306`

### Redis
- **Host**: `redis` (within Docker network) or `localhost`
- **Port**: `6379`
- **No authentication required**

### RabbitMQ
- **Host**: `rabbitmq` (within Docker network) or `localhost`
- **Management UI Port**: `15673`
- **AMQP Port**: `5673`
- **Default Username**: `guest`
- **Default Password**: `guest`
- **Management URL**: `http://localhost:15673`

### phpMyAdmin
- **URL**: `http://localhost:8080`
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