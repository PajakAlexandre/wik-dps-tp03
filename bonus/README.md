# Bonus wik-dps-tp03

This Docker Compose app sets up a WordPress environment with multiple WordPress instances, a MariaDB database, Redis for caching, and Nginx as a reverse proxy. It is designed for high availability and performance.

## Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/PajakAlexandre/wik-dps-tp03.git
   cd wik-dps-tp03/bonus
    ```

2. Create a .env file in the project directory with the following environment variables:

   ```bash
    WP_DB_NAME=mywordpressdb
    WP_DB_USER=mywordpressuser
    WP_DB_PASSWORD=mywordpresspassword
    WP_DB_PREFIX=wp_
   ```

## Configuration

### `docker-compose.yaml`

The `docker-compose.yaml` file defines the services and their configurations. The main services are:

- wordpress-service: WordPress with PHP 8.0 FPM on Alpine, configured with environment variables, Redis caching, and multiple replicas.
- mariadb: MariaDB for the WordPress database.
- redis: Redis for caching.
- nginx: Nginx as a reverse proxy.

### `nginx.conf`

The `nginx.conf` file configures the Nginx reverse proxy. It defines an upstream server for load balancing WordPress instances and sets up PHP handling for WordPress.

### `wordpress.ini`

The `wordpress.ini` file contains PHP configuration settings for WordPress, including file uploads, upload size limits, memory limits, and execution time.

## Usage

1. Access WordPress: Open your web browser and go to http://localhost:8080.

2. Set up WordPress: Follow the WordPress setup wizard to configure your site.

3. Scale WordPress: You can scale the number of WordPress instances by changing the replicas value in the docker-compose.yaml file.

    ```yaml
    deploy:
      replicas: 4
    ```
4. Customize WordPress: You can modify the `nginx.conf` and `wordpress.ini` files to adjust Nginx and PHP configurations.

