# PHP MySQL CRUD Docker

This project is a dockerized version of the PHP MySQL CRUD application. It uses Docker and Docker Compose to set up a development environment with PHP, Apache, MySQL, and phpMyAdmin.

## Prerequisites

- Docker
- Docker Compose

## Project Structure

```
.
├── database
│   └── script.sql
├── logs
│   └── apache2
├── php-mysql-crud
│   ├── db.php
│   ├── delete_task.php
│   ├── edit.php
│   ├── includes
│   │   ├── footer.php
│   │   └── header.php
│   ├── index.php
│   └── save_task.php
├── .env
├── docker-compose.yml
├── Dockerfile.db
├── Dockerfile.www
└── README.md
```

## Configuration

1. Copy `.env.example` to `.env` and adjust the values as needed:

```
DB_NAME=php_mysql_crud
DB_USER=user
DB_PASSWORD=password
DB_ROOT_PASSWORD=rootpassword
WEB_PORT=8080
DB_PORT=3306
PMA_PORT=8081
```

## Usage

1. Build and start the containers:

```bash
docker-compose up -d --build
```

2. Access the application:
   - Web application: http://localhost:8080
   - phpMyAdmin: http://localhost:8081

3. To stop the containers:

```bash
docker-compose down
```

## Services

- `www`: Apache web server with PHP
- `db`: MySQL database
- `phpmyadmin`: phpMyAdmin for database management

## Persistence

The MySQL data is persisted in a named volume `db_data`. This ensures that your data remains intact even if you remove the containers.

## Networking

The services are connected through a bridge network named `app-network`.

## Customization

- To change the web server port, modify the `WEB_PORT` in the `.env` file.
- To change the database configuration, modify the respective variables in the `.env` file.

## Troubleshooting

If you encounter any issues:

1. Check the logs:

```bash
docker-compose logs
```

2. Ensure all required ports are available on your host machine.
3. Make sure you have the latest versions of Docker and Docker Compose installed.

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)
