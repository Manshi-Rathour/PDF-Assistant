# PDF-Assistant

The **PDF Assistant** is a Python-based application designed to help users interact with PDF documents using a knowledge-based approach. It leverages PostgreSQL for storage, a vector database for efficient document retrieval, and the phidata framework to provide a seamless experience for managing and querying PDF content.

## Features

- **Pre-Trained on NLP Content**: The assistant is pre-trained on the book *Practical Natural Language Processing* by O'Reilly.
- **Customizable Training**: Users can upload any PDF documents to the `pdfs` folder, and the assistant will train on those files instead.
- **PDF URL Knowledge Base**: Optionally supports loading PDFs directly from URLs (commented in the code for now).
- **Vector Database Integration**: Uses `PgVector` for efficient vectorized queries on PDF content.
- **PostgreSQL Storage**: Stores and retrieves assistant sessions and metadata in a PostgreSQL database.
- **Interactive CLI**: Provides a Command-Line Interface (CLI) for interacting with the assistant.

  
## Prerequisites
- **Git:** <a href="https://git-scm.com/" target="_blank">Download and Install Git</a>
- **Groq:** <a href="https://groq.com/" target="_blank">Get free API key after login</a>
- **Docker**: For running PostgreSQL locally

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
