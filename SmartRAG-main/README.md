# SmartRAG – Private Multimodal AI Document Assistant

A locally running AI-powered document assistant that lets users interact with their documents, images, and audio through natural language conversations.

SmartRAG combines Retrieval-Augmented Generation (RAG), local Large Language Models (LLMs), vector search, OCR, and speech recognition to provide context-aware answers with source citations while keeping user data on the local machine.

## Key Features

- **Multimodal Document Processing:** Supports PDF, DOCX, TXT, Markdown, images, and audio files.
- **Retrieval-Augmented Generation:** Retrieves relevant document content to generate contextually grounded responses.
- **Source Citations:** Provides numbered citations linked to the original document and relevant page.
- **Local AI Processing:** Uses Ollama to run language and embedding models locally.
- **Image Understanding:** Integrates Tesseract OCR and BLIP image captioning.
- **Audio Transcription:** Uses Whisper for local speech-to-text processing.
- **Document Management:** Upload, preview, delete, and organize documents through a web interface.
- **Voice Input:** Ask questions using speech input.
- **Conversation History:** Maintains multiple conversations with follow-up context.

## Technology Stack

| Component | Technology |
|---|---|
| Frontend | Next.js |
| Backend | Python, FastAPI |
| LLM Runtime | Ollama |
| Language Model | Llama 3.1 |
| Embeddings | Nomic Embed Text |
| RAG Pipeline | Retrieval-Augmented Generation |
| Image OCR | Tesseract |
| Image Captioning | BLIP |
| Audio Processing | Whisper |
| Package Management | npm, pip |

## Architecture

![SmartRAG Architecture](https://github.com/user-attachments/assets/678d61a7-5f73-40eb-ad5e-b8c20ead69ae)

## Prerequisites

Install the following before running the application:

- Python 3.10–3.12
- Node.js 20+
- Ollama
- Tesseract OCR 5.x
- FFmpeg

### Install Tesseract and FFmpeg

**Windows:**
```bash
winget install UB-Mannheim.TesseractOCR Gyan.FFmpeg
```

**macOS:**
```bash
brew install tesseract ffmpeg
```

**Ubuntu/Debian:**
```bash
sudo apt install tesseract-ocr ffmpeg
```

## Installation and Setup

### 1. Download AI Models

Start Ollama and download the required models:

```bash
ollama pull llama3.1:8b
ollama pull nomic-embed-text
```

### 2. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/SmartRAG.git
cd SmartRAG
```

### 3. Set Up the Python Backend

```bash
python -m venv .venv
```

Activate the environment on Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### 4. Set Up the Frontend

```bash
cd frontend
npm install
cd ..
```

## Running the Application

Run the complete application from the project root:

```bash
python start.py
```

The application starts:

- **Frontend:** http://localhost:3000
- **Backend:** http://localhost:8000
- **API Documentation:** http://localhost:8000/docs

Open the frontend in your browser and upload documents to start interacting with your data.

Press `Ctrl + C` to stop the application.

### Running Services Separately

Backend:

```bash
uvicorn api:app --reload --port 8000
```

Frontend:

```bash
cd frontend
npm run dev
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | Check system and model status |
| GET | `/api/documents` | Retrieve uploaded documents |
| POST | `/api/documents` | Upload and index documents |
| GET | `/api/documents/{id}/file` | Retrieve original file |
| DELETE | `/api/documents/{id}` | Delete a document |
| DELETE | `/api/documents | Delete all documents |
| POST | `/api/chat` | Ask questions using RAG |
| POST | `/api/transcribe` | Transcribe audio files |

## Configuration

Application settings are managed through:

```text
config.yaml
```

Environment variables can override configuration settings.

Example:

```bash
SMARTRAG_MODELS__LLM_MODEL=llama3.2:3b
SMARTRAG_RETRIEVAL__TOP_K=8
SMARTRAG_GENERATION__TEMPERATURE=0.3
```

## Docker Deployment

The application can also be deployed using Docker Compose.

```bash
cd docker
docker compose up -d --build
```

Access the application at:

```text
http://localhost:3000
```

Stop the containers:

```bash
docker compose down
```

## Troubleshooting

- **Ollama connection error:** Ensure Ollama is running and the required models are downloaded.
- **Model not found:** Check the model names in `config.yaml`.
- **Frontend connection error:** Verify that the backend is running on port 8000.
- **OCR issues:** Verify Tesseract installation using `tesseract --version`.
- **Audio processing errors:** Verify FFmpeg installation using `ffmpeg -version`.

## Original Project and Attribution

This repository is based on the original SmartRAG project:

https://github.com/itanishqshelar/SmartRAG

Original contributors retain credit for their work. Refer to the original repository and LICENSE for applicable licensing terms.

## License

This project is distributed under the MIT License. See the [LICENSE](LICENSE) file for details.