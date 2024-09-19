# ContentSmith AI

![Screenshot 2024-09-19 190118](https://github.com/user-attachments/assets/1d9aaa89-333e-4b1a-96b3-c0bee7d8e2ea)


ContentSmith AI is an intelligent content generation and social media analytics system built with **Retrieval-Augmented Generation (RAG)**. It transforms social media profile analytics from CSV files into valuable insights, enabling users to automate content creation and understand engagement trends with precision.

This project uses **Cohere's language models** for chat interaction and embeddings, along with **Pinecone** as the vector database for efficient vector search and retrieval. The project has been compiled in a Langflow JSON file (`ContentSmith AI.json`) for easy deployment and customization within your own Langflow instance.

## Project Overview

**Live Demo**: [ContentSmith AI on Hugging Face Spaces](https://huggingface.co/spaces/DonGuillotine/LangflowProj)

ContentSmith AI automates social media content analysis by enabling users to ask specific questions about their TikTok performance data, such as identifying posts with high engagement, summarizing popular posts, and understanding engagement trends over time. The system is designed to provide accurate and reliable insights by reducing hallucinations, pulling exact quotes from data, and ensuring grounded, factual responses.

### Core Features

- **Automated Insights**: Analyze social media posts to generate summaries, engagement breakdowns, and content trends.
- **Fact-Based Responses**: Uses advanced prompting to reduce hallucinations and verify claims using extracted data.
- **Multimodal Search**: Retrieve posts by likes, engagement trends, or specific keywords.
- **Chain-of-Thought Reasoning**: The assistant reasons through each step to provide accurate and well-supported responses.
- **CSV Data Processing**: Easily upload CSV files for processing, vectorization, and retrieval.

### Technologies Used

- **Cohere Language Model**: Handles chat interaction and advanced prompting for content generation.
- **Cohere Embedding Model (`embed-english-v2.0`)**: Converts textual data from the CSV into vector embeddings for semantic search and retrieval.
- **Pinecone Vector Database**: Stores embeddings and facilitates efficient vector-based search.

## Installation and Setup

### Step 1: Import the `ContentSmith AI.json`

1. Open your Langflow instance.
2. Upload the provided `ContentSmith AI.json` file.

### Step 2: Set Up Global Variables in Langflow

To configure the project in your Langflow instance, create the following **Global Variables** in Langflow for the system to work properly:

- `COHERE_API_KEY`: Your API key from Cohere.
- `PINECONE_INDEX_NAME`: The name of your Pinecone index.
- `PINECONE_API_KEY`: Your Pinecone API key.

## How It Works

### 1. **CSV File Processing**
ContentSmith AI begins by extracting relevant columns from the uploaded CSV file, such as:
- `Date Posted`
- `Transcripts`
- `Caption`
- `Hashtags`
- Engagement metrics like `Likes`, `Views`, `Comments`, and `Shares`

### 2. **Text Cleaning and Vectorization**
After extracting and cleaning the text (removing unnecessary characters and structuring the content), the system uses the **Cohere Embedding Model (`embed-english-v2.0`)** to convert this data into vector embeddings. These embeddings are stored in the **Pinecone Vector Database**, which allows for efficient semantic search and retrieval.

### 3. **Retrieval-Augmented Generation (RAG)**
When users ask a question, ContentSmith AI retrieves the most relevant embeddings from Pinecone, and the Cohere model generates a response by referencing this context. Advanced prompting techniques ensure that the model pulls exact quotes, verifies claims, and expresses uncertainty if the relevant information isn’t available.

### 4. **User Interaction (Example Queries)**
Here are a few example queries users can ask:
- **"Show me all posts about 'Grok' from February"**: The system will search for posts mentioning "Grok" in the `Caption`, `Transcripts`, or `Hashtags` from February.
- **"Summarize the top 5 posts about product launches"**: It will retrieve and summarize the most popular posts based on `Likes` and `Views` metrics.
- **"Generate a summary of the most popular social media posts from last month"**: ContentSmith will provide an engagement-based summary of recent posts.
- **"List posts with over 1000 likes"**: It filters posts by `Likes` and returns relevant ones.
- **"Give me a breakdown of engagement trends in the past 3 months"**: The system aggregates metrics over the last 3 months and generates a trend report.

### Advanced Prompting Techniques

To ensure accuracy and reliability, ContentSmith AI uses advanced prompting techniques:
- **Hallucination Reduction**: By pulling from factual data and expressing uncertainty if the data is not present, hallucinations are minimized.
- **Exact Quotes**: When possible, the assistant pulls exact quotes from the data to ensure accurate responses.
- **Chain-of-Thought Reasoning**: The assistant uses logical reasoning steps to ensure it generates correct and meaningful insights.
- **Data Verification**: If the query requires a factual answer, the assistant verifies claims against the stored context before responding.

## Deployment

### Live on Hugging Face
You can access a live version of the project on [Hugging Face Spaces](https://huggingface.co/spaces/DonGuillotine/LangflowProj).

## Conclusion

ContentSmith AI provides an efficient and scalable way to turn social media data into actionable insights. By combining semantic search, factual content generation, and flexible querying through RAG, it is an ideal tool for marketers, content creators, and social media managers.

## License

This project is licensed under the MIT License.
