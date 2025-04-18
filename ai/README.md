# AI Development Environment

This project sets up a local AI development environment using Docker Compose, featuring Ollama for running large language models and Open WebUI for a user-friendly interface.

## Prerequisites

- Docker and Docker Compose installed
- NVIDIA GPU with drivers installed (for GPU acceleration)
- Git

## Project Structure

```
.
├── docker-compose.yml
├── open-webui/
│   └── data/          # Persistent data for Open WebUI
├── ollama/            # Ollama model storage
└── ollama-custom-models/  # Custom model storage
```

## Services

### Ollama
- Runs large language models locally
- Exposed on port 11434
- GPU-accelerated using NVIDIA drivers
- Persistent storage for models in `./ollama` directory
- Custom models can be stored in `./ollama-custom-models`

### Open WebUI
- Web interface for interacting with Ollama
- Exposed on port 3000
- Connects to Ollama service internally
- Persistent data stored in `./open-webui` directory

## Getting Started

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Start the services:
   ```bash
   docker-compose up -d
   ```

3. Access the web interface:
   - Open your browser and navigate to `http://localhost:3000`

## Configuration

### Environment Variables

You can customize the following environment variables:

- `OLLAMA_DOCKER_TAG`: Ollama Docker image tag (default: latest)
- `WEBUI_DOCKER_TAG`: Open WebUI Docker image tag (default: main)
- `WEBUI_SECRET_KEY`: Secret key for Open WebUI (set in docker-compose.yml)

### Volume Mounts

- `./ollama`: Stores Ollama models and configuration
- `./ollama-custom-models`: Stores custom models
- `./open-webui`: Stores Open WebUI data and configuration

## Usage

1. Access the Open WebUI interface at `http://localhost:3000`
2. Select or download models through the interface
3. Start chatting with your chosen model

## Troubleshooting

- If you encounter GPU-related issues, ensure your NVIDIA drivers are properly installed
- Check Docker logs for specific service issues:
  ```bash
  docker-compose logs ollama
  docker-compose logs open-webui
  ```

## Maintenance

- To update the services:
  ```bash
  docker-compose pull
  docker-compose up -d
  ```

- To stop the services:
  ```bash
  docker-compose down
  ```

## License

GNU GENERAL PUBLIC LICENSE v3
[Add contribution guidelines here]
