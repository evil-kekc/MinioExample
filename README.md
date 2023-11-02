# MinIO and NGINX Docker Compose Usage

This example demonstrates how to set up MinIO, an open-source object storage server, alongside NGINX for reverse proxying, using Docker Compose.

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone this repository to your local machine.

2. Create a `.env` file in the root directory (the same level as your Docker Compose files) with the following content:

    ```
    LOGIN=your_username
    PASSWORD=your_password
    DOMAIN=your_domain
    ```

    Replace `your_username`, `your_password`, and `your_domain` with your desired MinIO credentials and domain.

3. Run the following command to start MinIO and NGINX:

    For MinIO and NGINX combined:
    ```bash
    docker-compose -f docker-compose.minio-nginx.yml up -d
    ```

    For MinIO only:
    ```bash
    docker-compose -f docker-compose.minio.yml up -d
    ```

4. Once the containers are running:
    - Access MinIO web interface at `http://localhost:9000` or `http://your_domain:9000` in your web browser.
    - Access NGINX at `http://localhost` or `http://your_domain`.

## Configuration

- The MinIO server is configured to use ports 9000 and 9001. NGINX is set to listen on ports 80 and 443.

- The `MINIO_ROOT_USER` and `MINIO_ROOT_PASSWORD` environment variables for MinIO are set based on the values provided in the `.env` file.

- Data for MinIO is stored in the `/data/minio` directory on the host machine.

- NGINX configuration can be found in the `app.conf` file. Adjust the configuration as needed.

## Accessing MinIO

- **Web Interface**: Visit `http://localhost:9000` or `http://your_domain:9000` in your web browser to access the MinIO web interface.

- **S3-Compatible API**: Use the endpoint `http://localhost:9000` or `http://your_domain:9000` for S3 API operations.

## Accessing NGINX

- NGINX serves at `http://localhost` or `http://your_domain`.

## Stopping the Containers

To stop MinIO and NGINX, run:

```bash
docker-compose -f docker-compose.minio-nginx.yml down
```
or 
```bash
docker-compose -f docker-compose.minio.yml down
```

This will stop and remove the containers.

## Note

* Ensure the directories specified for volumes exist on your host machine or adjust them accordingly.
* NGINX is configured as a reverse proxy to MinIO, allowing access to MinIO via the NGINX endpoint.
* Customize the `.env` file and configurations based on your specific requirements.
* For further information and advanced configurations, refer to the official documentation for MinIO and NGINX.

Enjoy using [MinIO](https://docs.min.io/) and [NGINX](https://nginx.org/en/docs/) for your object storage and proxying needs!