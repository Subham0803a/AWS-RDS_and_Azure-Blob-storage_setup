
🚀 LLM Document Management API
A robust FastAPI-based backend designed for managing users and their document uploads. This project leverages AWS RDS (PostgreSQL) for structured metadata and Azure Blob Storage for scalable cloud file hosting.
🛠️ Tech Stack
Backend Framework: FastAPI
Database: AWS RDS (PostgreSQL)
Cloud Storage: Azure Blob Storage
ORM: SQLAlchemy
Data Validation: Pydantic
Server: Uvicorn
📋 Prerequisites
Python: 3.8 or higher installed.
AWS Account: Access to an RDS PostgreSQL instance.
Azure Account: A Storage Account and a created container.
⚙️ Local Setup
1. Clone the Repository

Bash


git clone <your-repository-url>
cd AWS-RDS_and_Azure-Blob-storage_setup


2. Configure Environment Variables
Create a .env file in the root directory and add your credentials. Note: This file is ignored by Git for security.

Ini, TOML


# AWS RDS Configuration
DB_HOST=testing-db.cpceoka4oj77.ap-south-1.rds.amazonaws.com
DB_PORT=5432
DB_NAME=llm
DB_USER=postgres
DB_PASSWORD=subham0803

# Azure Blob Storage
AZURE_STORAGE_CONNECTION_STRING="DefaultEndpointsProtocol=https;AccountName=docqastorage2025;AccountKey=...;EndpointSuffix=core.windows.net"
AZURE_CONTAINER_NAME=documents

# SMTP Email Settings (for OTP)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-app-password


3. Setup Virtual Environment

Bash


# Create the virtual environment
python -m venv venv

# Activate the environment (Windows)
.\venv\Scripts\Activate.ps1

# Install required packages
pip install fastapi uvicorn sqlalchemy azure-storage-blob python-dotenv python-multipart pydantic[email]


4. Run the Application

Bash


python main.py


The server will start at http://localhost:5000. On startup, the API will automatically create the necessary database tables.
🧪 Testing with Postman
1. Check Health Status
Method: GET
URL: http://localhost:5000/health
Purpose: Verifies that both AWS RDS and Azure Blob Storage are connected.
2. Create a User
Method: POST
URL: http://localhost:5000/users
Body (JSON):
JSON
{
  "username": "subham_dev",
  "email": "subham@example.com",
  "full_name": "Subham Pratap"
}


3. Upload a Document
Method: POST
URL: http://localhost:5000/documents/upload
Body Type: form-data
Keys:
file: (Select a PDF or Image file)
user_id: 1 (The ID of the user created above)
4. Fetch User's Document Gallery
Method: GET
URL: http://localhost:5000/documents/user/1/list
Purpose: Lists all files uploaded specifically by User 1 using the One-to-Many relationship.
📂 Project Structure

Plaintext


.
├── app/
│   ├── database/       # DB Connections (AWS) & Storage (Azure) logic
│   ├── models/         # SQLAlchemy Database Models
│   ├── routers/        # API route handlers (Users, Documents)
│   └── schemas/        # Pydantic data validation schemas
├── main.py             # App entry point & startup initialization
├── .env                # Private Credentials (STRICTLY IGNORED BY GIT)
├── .gitignore          # Rules to exclude venv/ and .env
└── requirements.txt    # List of project dependencies


