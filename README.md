# PDF-Assistant



## Prerequisites
- **Git:** <a href="https://git-scm.com/" target="_blank">Download and Install Git</a>
- **Groq:** <a href="https://groq.com/" target="_blank">Get free API key after login</a>

## Installation
To utilize PDF Assistant locally, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Manshi-Rathour/PDF-Assistant
   ```
   
2. **Navigate to the project directory**:
   ```bash
   cd PDF-Assistant
   ```
   
3. **Set Up a Virtual Environment**:
   Create and activate a virtual environment for dependency management:
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

4. **Install Dependencies**:
   Install the necessary packages using the `requirements.txt` file:
   ```bash
   pip install -r requirements.txt
   ```

6. **Using PostgreSQL with Local Storage**

    Follow the steps below to set up PostgreSQL with local storage:
    
    - Step 1: Start the PostgreSQL Docker Container
      
      Run the following command in your Git Bash to create and start a PostgreSQL container:
    
      ```bash
      docker run -d \
      -e POSTGRES_DB=ai \
      -e POSTGRES_USER=ai \
      -e POSTGRES_PASSWORD=ai \
      -e PGDATA=/var/lib/postgresql/data/pgdata \
      -v pgvolume:/var/lib/postgresql/data \
      -p 5532:5432 \
      --name pgvector \
      phidata/pgvector:16
      ```
    - Step 2: Configure the Database URL
      
      Use the following database URL in your application to connect to the PostgreSQL instance:
       ```
       db_url = "postgresql+psycopg://ai:ai@localhost:5532/ai"
       ```
       
5. **Configure API Keys**:
   Set up your API keys in a `.env` file. Create a `.env` file in the root directory and add the following line:
   ```env
   GROQ_API_KEY="your-groq-api-key"
   ```
   (Optional) If you want to use cloud storage like AWS RDS PostgresSQL then:
   ```env
   DB_URL=postgresql+psycopg://{master_username}:{password}@{endpoint}:5432/{database_name}
   ```
  
   
7. **Run the Application**:
   ```bash
   python pdf_assistant.py
   ```
