
# Insurance Premium Prediction FastAPI Application with Docker

## 1. Project Overview

This project runs a Python FastAPI application inside a Docker container using Python 3.12.

Docker allows us to package the application and its dependencies into a container so that it can run consistently across different environments.

## 2. Project Structure

```text
project/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── README.md
```

## 3. Prerequisites

Install the following tools before starting:

- Python 3.12
- Docker Desktop (Windows/Mac) or Docker Engine (Linux)
- Git (optional)

Verify Docker installation:

```bash
docker --version
```

Check whether Docker is running:

```bash
docker info
```

## 4. Create requirements.txt

Add your Python dependencies to `requirements.txt`.

Example:

```text
fastapi
uvicorn
```

## 5. Create Dockerfile

Create a file named `Dockerfile` in the project root directory.

```
1. Use python 3.12 base image
2. Set working directory
3. Copy requirements and install dependencies
4. Copy rest of application code
5. Expose the application port
6. Command to start FastAPI application
```

## 6. Create .dockerignore

Create a `.dockerignore` file to prevent unnecessary files from being copied into the Docker image.

```text
__pycache__/
*.pyc
*.pyo
.venv/
venv/
.git/
.env
```

## 7. Build Docker Image

Open your terminal in the project directory.

Run the following command:

```bash
docker build -t fastapi-app .
```

Explanation:

- `docker build` – Builds a Docker image.
- `-t fastapi-app` – Assigns a name to the Docker image.
- `.` – Uses the current directory as the build context.

## 8. Verify Docker Image

To check whether the image was created successfully:

```bash
docker images
```

You should see an image named:

```text
fastapi-app
```

## 9. Run Docker Container

Start your FastAPI application using:

```bash
docker run -d -p 8000:8000 --name fastapi-container fastapi-app
```

Explanation:

- `docker run` – Creates and starts a container.
- `-d` – Runs the container in the background.
- `-p 8000:8000` – Maps host port 8000 to container port 8000.
- `--name fastapi-container` – Assigns a name to the container.
- `fastapi-app` – Specifies the Docker image.

## 10. Check Running Containers

Run:

```bash
docker ps
```

To view all containers, including stopped containers:

```bash
docker ps -a
```

## 11. Access FastAPI Application

Once the container is running, open your browser.

**FastAPI Application:**

http://localhost:8000

**Swagger API Documentation:**

http://localhost:8000/docs

**ReDoc API Documentation:**

http://localhost:8000/redoc

## 12. View Container Logs

To check application logs:

```bash
docker logs fastapi-container
```

To continuously monitor logs:

```bash
docker logs -f fastapi-container
```

## 13. Stop Docker Container

To stop the running container:

```bash
docker stop fastapi-container
```

## 14. Start Existing Container

To start a previously stopped container:

```bash
docker start fastapi-container
```

## 15. Restart Docker Container

```bash
docker restart fastapi-container
```

## 16. Remove Docker Container

First, stop the container:

```bash
docker stop fastapi-container
```

Then remove it:

```bash
docker rm fastapi-container
```

## 17. Remove Docker Image

To remove the Docker image:

```bash
docker rmi fastapi-app
```

Note: Remove the container before removing its image.

## 18. Rebuild Docker Image After Code Changes

Whenever you modify your application code or dependencies, rebuild the image.

```bash
docker build -t fastapi-app .
```

Remove the old container if it exists:

```bash
docker rm -f fastapi-container
```

Run the updated container:

```bash
docker run -d -p 8000:8000 --name fastapi-container fastapi-app
```

## 19. Complete Docker Command Summary

| Task                    | Command                                                             |
| ----------------------- | ------------------------------------------------------------------- |
| Build image             | `docker build -t fastapi-app .`                                   |
| List images             | `docker images`                                                   |
| Run container           | `docker run -d -p 8000:8000 --name fastapi-container fastapi-app` |
| List running containers | `docker ps`                                                       |
| List all containers     | `docker ps -a`                                                    |
| View logs               | `docker logs fastapi-container`                                   |
| Stop container          | `docker stop fastapi-container`                                   |
| Start container         | `docker start fastapi-container`                                  |
| Restart container       | `docker restart fastapi-container`                                |
| Remove container        | `docker rm -f fastapi-container`                                  |
| Remove image            | `docker rmi fastapi-app`                                          |

## 20. Conclusion

Your FastAPI application is now containerized using Docker.

You can build the Docker image, start the container, access the FastAPI APIs through your browser, monitor application logs, and manage the Docker container using the commands described above.
