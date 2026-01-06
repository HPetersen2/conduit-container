# Conduit Container

A Docker-based setup to run an Angular frontend and a Django backend together in a unified, containerized environment. This project demonstrates how to package, network, and secure multiple services using Docker and Docker Compose for local development and cloud-ready deployment.

The main goal of this project is to consolidate knowledge in containerization, networking, and basic network security by operating a full-stack application stack in isolated yet connected containers.

---

## Installation / Quickstart

Follow these steps to get the project up and running locally.

### Prerequisites

* Docker Desktop (Docker Engine + Docker Compose)
* Git

If Docker is not installed, follow the official installation guide:

* Docker Desktop (Windows / macOS): [https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)
* Docker Engine (Linux): [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

After installation, verify Docker:

```bash
docker --version
docker-compose --version
```

### Setup Steps

1. Clone the project repository:

   ```bash
   git clone <repository-url>
   cd conduit-container
   ```

2. Copy the environment template file:

   **Linux / macOS**

   ```bash
   cp .env.template .env
   ```

   **Windows (Command Prompt)**

   ```cmd
   copy .env.template .env
   ```

   **Windows (PowerShell)**

   ```powershell
   Copy-Item -Path .env.template -Destination .env
   ```

3. Make sure Docker Desktop is installed and running.

4. Build and start all services:

   ```bash
   docker compose up --build -d
   ```

5. To stop and remove the containers:

   ```bash
   docker compose down
   ```

---

## Usage

After starting the stack with Docker Compose, the containers run together within a shared Docker network.

* The Angular frontend consumes the backend via the service name defined in `docker-compose.yml`.
* All configuration (ports, hostnames, secrets) is controlled via the `.env` file.
* No services are exposed beyond what is explicitly defined in the Compose configuration.

Start the stack:

```bash
docker-compose up --build
```

Stop and remove containers:

```bash
docker-compose down
```

---

## API Reference

This repository does **not** define or document concrete API endpoints.

The actual API surface depends entirely on the Django backend project that is included or mounted into the backend container. Endpoint definitions, authentication, and data models must be documented within the backend repository itself.

This container setup is intentionally API-agnostic and focuses solely on orchestration, networking, and runtime configuration.

---

## Architecture Overview

* **Angular Frontend**: Built and served from a dedicated frontend container
* **Django Backend**: Runs in its own container with isolated dependencies
* **Docker Network**: Enables secure communication between services
* **Environment Variables**: Centralized configuration via `.env` file

This setup mirrors real-world cloud deployments and encourages best practices in service isolation and network security.

---

## Contributing

Contributions are welcome.

1. Fork the repository
2. Create a new feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
