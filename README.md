# Docker setup for Project #

This project uses Docker to run **Nginx**, **PHP**, and **MySQL** services in a containerized environment, providing an isolated setup for development.

### Prerequisites ###

- **Docker**: installed on your machine. [Download Docker](https://docs.docker.com/get-docker/)
- **Composer**: required to manage PHP dependencies. Make sure it’s installed on your machine. [Download Composer](https://getcomposer.org/download/)

### Setup Instructions ###  

1. **Clone the repository:**

    ```bash  
    git clone git@github.com:ievasinke/docker-setup.git
    cd docker-setup
    ```  
  
2. **Create and configure environment variables**:

    Copy the `.env.example` file to create your `.env` file. Update it with any necessary environment variables, like database credentials:

    ```bash
    cp .env.example .env
    ```

3. **Build and start containers**:

    Use Docker Compose to build and start the containers:

    ```bash
    docker compose up --build
    ```

    This command will:
    - Download the required Docker images if they’re not already on your machine.
    - Build and launch containers for:
      - **Nginx** (`nginx:1.27`)
      - **PHP** (`php:8.2-fpm`)
      - **MySQL** (`mysql:8.0`)
  
## Configuration

- **Environment Variables**: 
  Ensure that you set all required environment variables in the `.env` file (e.g., `MYSQL_ROOT_PASSWORD`, `MYSQL_DATABASE`, etc.).

- **Ports**: 
  By default:
  - Nginx is accessible on `http://localhost:8080` (you can adjust the port in `docker-compose.yml` if needed).
  - MySQL is accessible on `localhost` using port `3306`.

## Accessing the Services

- **Nginx**: Visit [http://localhost:8080](http://localhost:8080) (or the port specified in `docker-compose.yml`).
- **MySQL**: Connect to MySQL via a MySQL client on `localhost` port `3306` (or the port specified in `docker-compose.yml`). Use the credentials specified in your `.env` file.

## Managing Containers

- **Stop the containers**:

    To stop and remove containers, networks, and volumes created by `up`:

    ```bash
    docker compose down
    ```

- **Rebuilding containers**:

    If you make changes to Dockerfile or dependencies, rebuild with:

    ```bash
    docker compose up --build
    ```
