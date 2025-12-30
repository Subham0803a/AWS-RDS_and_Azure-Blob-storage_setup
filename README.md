⚙️ How to Setup

# Create and activate virtual environment
python -m venv venv
.\venv\Scripts\Activate.ps1

# Install required libraries
pip install -r requirement.txt 

# 3. Add .env & Your Keys

DB_HOST=testing-db.cpceoka4oj77.ap-south-1.rds.amazonaws.com
DB_PORT=5432
DB_NAME=llm
DB_USER=postgres
DB_PASSWORD=subham0803

AZURE_STORAGE_CONNECTION_STRING=your_connection_string_here
AZURE_CONTAINER_NAME=documents

# 4. Run the API
Run this command in PowerShell ---> python main.py

# File Structure
├── app/
│   ├── database/       # DB Connections (AWS) & Storage (Azure) logic
│   ├── models/         # SQLAlchemy Database Models
│   ├── routers/        # API route handlers (Users, Documents)
│   └── schemas/        # Pydantic data validation schemas
├── main.py             # App entry point & startup initialization
├── .env                # Private Credentials (STRICTLY IGNORED BY GIT)
├── .gitignore          # Rules to exclude venv/ and .env
└── requirements.txt    # List of project dependencies


