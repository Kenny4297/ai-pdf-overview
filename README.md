# AI-PDF
## Table of Contents
- [License](#license)
- [Project Overview](#project-overview)
- [Purpose and Inspiration](#purpose-and-inspiration)
- [Issues](#issues)
- [Architecture](#architecture)
- [Process Overview](#process-overview)
- [Technologies Used](#technologies-used)

## License
This project is licensed under the MIT license.

## Project Overview
AI-PDF is an AI document scanner. Users can load PDFs to Amazon S3, then ask the AI questions about the uploaded files. The AI can even pinpoint the page where it found the information. For confidentiality, login authentication using AWS Cognito is implemented.

## Purpose and Inspiration
My client needed an efficient way to parse numerous PDFs for specific information like company protocols and regulations. This solution simplifies their task significantly.

## Issues
### Large Size PDFs
The large file sizes of PDFs prevented their upload through the standard homepage 'file upload' feature. To resolve this, I set up an Amazon S3 account shared with my client, allowing them to upload directly to the database and avoid the 15-second timeout issue.

### Extracting Text for AI Parsing
Text extraction from PDFs for AI parsing was a key challenge addressed in the development process.

## Architecture
**Event-Driven Processing Pipeline:** Upon PDF upload to S3, the system triggers an AWS Lambda function that immediately processes the document through an automated workflow. The document flows through text extraction using pdf-parse, followed by text cleaning to remove formatting artifacts. The cleaned text is then chunked into semantic segments and converted to vector embeddings using OpenAI's text-embedding-ada-002 model. These embeddings are immediately stored in Pinecone's vector database with metadata linking back to the source document and page numbers. This real-time processing approach ensures all uploaded documents are instantly searchable, eliminating query-time processing delays that would negatively impact user experience.

## Process Overview
### 1. User Authentication & Document Upload
- **Tools Used**: AWS Cognito for authentication, Amazon S3 for storage, AWS Lambda for processing
- **Functionality**: Secure user login followed by direct PDF upload to S3, which automatically triggers Lambda-based processing pipeline

### 2. Text Extraction
- **Tool Used**: `pdf-parse` npm package for extracting text
- **Functionality**: Function to extract and split text, removing unnecessary characters like new lines

### 3. Text Cleaning & Preprocessing  
- **Tool Used**: Custom preprocessing functions
- **Functionality**: Remove formatting artifacts and standardize text for optimal embedding quality

### 4. Vectorize and Embed Documents
- **Text to Embedding**: Used `openai.createEmbedding` for converting text to embeddings
- **Chunking Strategy**: Text segmented into manageable chunks while preserving context

### 5. Vector Storage
- **Upload to Pinecone DB**: Uploaded vectors to Pinecone DB with metadata for future retrieval
- **Indexing**: Maintains document provenance and page references for citation tracking

### 6. User Query Input
- **Interface**: Natural language query input through intuitive web interface
- **Processing**: Queries converted to embeddings using same OpenAI model

### 7. Vector Search & Retrieval
- **Vector Search**: Performed searches in Pinecone to match user queries
- **Ranking**: Results ranked by similarity scores and relevance

### 8. Format Results for AI Processing
- **Formatting with Langchain**: Used Langchain to format vectors for OpenAI comprehension
- **Context Preparation**: Retrieved content prepared for response generation

### 9. Generate AI Response
- **AI Response Generation**: Utilized OpenAI (GPT-3.5-turbo/GPT-4) to generate responses from prepared content
- **Citation Integration**: Automatic page-level citation generation for source verification

## Technologies Used
### Front End:
- React.js
- Next.js
- TypeScript
- TailwindCSS
- AWS Cognito
- Langchain
- Openai-edge

### Back End:
- Amazon S3
- AWS Lambda
- NeonDB
- PineconeDB
- PostgreSQL
- Drizzle ORM

> Due to the sensitive nature of this project, specific data details cannot be shared. For more information or a detailed walkthrough, please reach out directly.
