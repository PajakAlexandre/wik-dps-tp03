# wik-dps-tp03

This Docker Compose app is designed to demonstrate load balancing of a Rust-based API service using a Docker container and an Nginx reverse proxy. It consists of the following components:

- A Rust API service container.
- An Nginx reverse proxy container.
- Configuration files for Nginx and Rust API service.

## Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Project Description

This project aims to demonstrate load balancing with the following steps:

1. Create a Docker Compose file with a service based on the Dockerfile created in the TP WIK-DPS-TP02.
2. Increase the number of replicas to 4 for this service.
3. Modify the Docker Compose to add an Nginx reverse proxy. Expose only the reverse proxy on your host on port 8080.
4. Configure Nginx (nginx.conf) to load balance requests to the service based on your image.
5. Modify the code of your API to log the hostname on every request to /ping. Launch your `docker-compose.yaml` and observe the load balancing effect.

## Project Structure

### Dockerfile

The `Dockerfile` sets up a Rust environment and compiles the Rust API service. It creates a lightweight container for the API service and runs it.

### `docker-compose.yaml`

The `docker-compose.yaml` file defines the services and their configurations. The main services are:

- **api**: Rust API service with multiple replicas.
- **nginx**: Nginx as a reverse proxy.

### `nginx.conf`

The `nginx.conf` file configures Nginx to load balance requests to the Rust API service. It listens on port 80 and forwards requests to the API service.

### Updated API Code

The updated Rust API code logs the hostname for every request made to the `/ping` endpoint. It responds with an HTTP 200 response, including the hostname and request headers.

## Usage

1. Clone this repository:

   ```bash
   git clone https://github.com/your-repo/wik-dps-tp03.git
   cd wik-dps-tp03
    ```
2. Build and start the containers:
   ```bash
   docker compose up -d --build
   ```
   
3. Access the API: Open your web browser and go to http://localhost:8080/ping.
4. Monitor the logs: Run `docker compose logs -f` to monitor the logs for the API service and Nginx. As you send requests to the /ping endpoint, observe the logs in the API service to see the hostname of the server handling the request.

## Bonus

[See the bonus README.md](bonus/README.md) for instructions on how to set up a WordPress environment with multiple WordPress instances, a MariaDB database, Redis for caching, and Nginx as a reverse proxy. It is designed for high availability and performance.