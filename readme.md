# Backend README

## Overview
This is the backend of the project, built using **FastAPI**. It provides a REST API for various functionalities, including language translation, using the **MarianMTModel** from Hugging Face.

## Features
- Language translation API
- HTTPS enabled
- CORS configuration
- Modular and scalable design

## Prerequisites
- Python 3.10 or higher
- Virtual environment (recommended)
- OpenSSL for HTTPS

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/snarayan1603/nao-backend.git
   cd <repository_name>
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Generate SSL certificates for HTTPS:
   ```bash
   openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./ssl/server.key -out ./ssl/server.crt
   ```

## Usage
1. Run the development server:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 443 --ssl-keyfile=./ssl/server.key --ssl-certfile=./ssl/server.crt
   ```

2. Access the API:
   - Locally: `https://localhost:443`
   - On your network: `https://<your-local-ip>:443`

3. Test the translation endpoint:
   - Endpoint: `POST /api/translate`
   - Request body:
     ```json
     {
       "text": "Hello, world!",
       "source_lang": "en",
       "target_lang": "es"
     }
     ```
   - Example response:
     ```json
     {
       "translated_text": "Hola, mundo!"
     }
     ```

## Directory Structure
```
project_root/
├── main.py                # Entry point for the FastAPI application
├── requirements.txt       # Python dependencies
├── ssl/                   # SSL certificate and key
│   ├── server.key
│   ├── server.crt
└── README.md              # Documentation (this file)
```

## Dependencies
- **FastAPI**: Web framework
- **Uvicorn**: ASGI server
- **Transformers**: Hugging Face library for MarianMTModel
- **PyTorch**: Deep learning library

## Troubleshooting
### Error: "NumPy version mismatch"
- Downgrade NumPy to a compatible version:
  ```bash
  pip install "numpy<2.0"
  ```

### Error: "Module not found"
- Ensure all dependencies are installed:
  ```bash
  pip install -r requirements.txt
  ```

### Error: "Permission denied on port 443"
- Run the server with `sudo`:
  ```bash
  sudo uvicorn main:app --host 0.0.0.0 --port 443 --ssl-keyfile=./ssl/server.key --ssl-certfile=./ssl/server.crt
  ```

## License
This project is licensed under the [MIT License](LICENSE).

## Contact
For any questions or issues, please contact [your_email@example.com].

