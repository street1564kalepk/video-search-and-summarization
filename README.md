# Video Search and Summarization

A fork of [NVIDIA AI Blueprints: Video Search and Summarization](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization).

This blueprint enables intelligent video search and summarization using NVIDIA AI technologies, allowing users to search through video content using natural language queries and generate concise summaries of video segments.

## Features

- **Natural Language Video Search**: Query video libraries using plain English
- **Automatic Summarization**: Generate concise summaries of video content
- **Multi-modal Understanding**: Combines visual and audio analysis
- **Scalable Architecture**: Built to handle large video libraries
- **NVIDIA GPU Accelerated**: Leverages NVIDIA GPUs for fast inference

## Prerequisites

- Python 3.10+
- NVIDIA GPU (A100 or H100 recommended)
- Docker & Docker Compose
- NVIDIA Container Toolkit
- NVIDIA API Key (for cloud-based models)

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/your-org/video-search-and-summarization.git
cd video-search-and-summarization
```

### 2. Configure Environment

```bash
cp .env.example .env
# Edit .env with your NVIDIA API keys and configuration
```

### 3. Launch with Docker Compose

```bash
docker compose up --build
```

### 4. Access the Application

Open your browser and navigate to `http://localhost:8080`

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Frontend (UI)                      │
│              React / Next.js App                     │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│                  Backend API                         │
│               FastAPI Application                    │
└────────┬─────────────┬──────────────────┬───────────┘
         │             │                  │
┌────────▼──┐  ┌───────▼──────┐  ┌───────▼───────────┐
│  Video    │  │   Vector     │  │   Summarization   │
│ Ingestion │  │   Store      │  │     Service       │
│ Pipeline  │  │  (Milvus)    │  │  (NVIDIA NIM)     │
└───────────┘  └──────────────┘  └───────────────────┘
```

## Configuration

Key environment variables:

| Variable | Description | Default |
|----------|-------------|---------|
| `NVIDIA_API_KEY` | NVIDIA API key for NIM services | Required |
| `MILVUS_HOST` | Milvus vector database host | `localhost` |
| `MILVUS_PORT` | Milvus vector database port | `19530` |
| `VIDEO_STORAGE_PATH` | Path to store uploaded videos | `./data/videos` |
| `MAX_VIDEO_SIZE_MB` | Maximum video upload size in MB | `500` |

## Development

### Setting Up Local Development Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -r requirements-dev.txt
```

### Running Tests

```bash
pytest tests/ -v
```

### Code Style

This project uses `ruff` for linting and `black` for formatting:

```bash
black .
ruff check .
```

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) and review the [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md) before submitting.

To report bugs or request features, please use the appropriate [issue template](.github/ISSUE_TEMPLATE/).

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Original blueprint by [NVIDIA AI Blueprints](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization)
- Built with [NVIDIA NIM](https://developer.nvidia.com/nim) microservices
- Vector search powered by [Milvus](https://milvus.io/)
