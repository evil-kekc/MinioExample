# MinIO Docker Usage Example

This example demonstrates how to set up MinIO, an open-source object storage server, using Docker Compose.

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone this repository to your local machine.

2. Create a `.env` file in the root directory (the same level as your `docker-compose.yml`) with the following content:

    ```
    LOGIN=your_username
    PASSWORD=your_password
    ```

   Replace `your_username` and `your_password` with your desired MinIO credentials.

3. Run the following command to start MinIO:

    ```bash
    docker-compose up -d
    ```

4. Once MinIO is running, you can access the web interface at `http://localhost:9000` in your web browser. Log in using
   the credentials you set in the `.env` file.

## Configuration

- The MinIO server is configured to use ports 9000 and 9001. You can access the server and the MinIO Console at these
  ports.

- The `MINIO_ROOT_USER` and `MINIO_ROOT_PASSWORD` environment variables are set based on the values provided in
  the `.env` file.

- Data is stored in the `/data/minio` directory on the host machine.

## Accessing MinIO

- **Web Interface**: Visit [http://localhost:9000](http://localhost:9000) in your web browser to access the MinIO web
  interface.

- **S3-Compatible API**: Use the endpoint `http://localhost:9000` for S3 API operations. You can use various
  S3-compatible libraries and tools to interact with the server.

## Stopping MinIO

To stop MinIO, run:

```bash
docker-compose down
```

This will stop and remove the MinIO containers.

## Customization

- Adjust the `.env` file to change the login credentials and other environment variables as needed.

Modify the `docker-compose.yml` file to change ports, volumes, or other configurations based on your requirements.

## Note

- Ensure the directory specified for volumes (`/data/minio` in this case) exists on your host machine or adjust it
  accordingly.

- This setup uses a specific MinIO release version. You can change the MinIO image tag to use a different release by
  modifying the `image` field in the `docker-compose.yml`.

For further information and advanced configurations, refer to the [MinIO Documentation](https://min.io/docs/minio/kubernetes/upstream/index.html?ref=docs-redirect).
