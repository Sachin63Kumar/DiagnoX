# DiagnoX

Diagnox is an AI-powered chatbot designed to assist with healthcare-related queries. It leverages medical literature and Google Gemini's language model to provide accurate and contextually relevant responses. The chatbot is built using Flask and integrates with Pinecone for vector search and Langchain for document retrieval.

## Features

- **Healthcare-oriented chatbot**: Uses medical books as reference material for answering healthcare questions.
- **Customizable**: Easily configurable with your Pinecone API key and Google API key.
- **Fast and efficient**: Uses Pinecone’s vector search to quickly retrieve relevant medical information.
- **Advanced Language Model**: Powered by Google Gemini 2.0 Flash model to generate responses.

## Prerequisites

Before you get started, ensure you have the following:

- Python 3.8+
- A Google Gemini API key (for generating responses using the AI model).
- A Pinecone API key (for vector search).
- A `.env` file for storing sensitive keys (API keys).

### Installation

1. Clone the repository to your local machine:

    ```bash
    git clone https://github.com/yourusername/DiagnoX.git
    cd DiagnoX
    ```

2. Create and activate a Python virtual environment:

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. Install required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

### Environment Setup

You need to create a `.env` file in the root directory of your project to store your API keys.

```text
PINECONE_API_KEY=your_pinecone_api_key
GOOGLE_API_KEY=your_google_api_key
```

Replace `your_pinecone_api_key` and `your_google_api_key` with your actual API keys.

### Running the Application

1. To run the Flask app locally, execute the following command:

    ```bash
    python app.py
    ```

2. The application will be hosted on `http://localhost:8080`.

3. Open your browser and navigate to `http://localhost:8080` to start interacting with the chatbot.

## Code Overview

### `app.py` - Main Flask Application

The `app.py` file is the main file of the application, which serves as the backend API.

- **Imports**: We import necessary libraries such as Flask for the web server, Langchain components for LLM-based document retrieval, Pinecone for vector search, and dotenv to load environment variables.
- **API Keys**: We fetch the API keys from the `.env` file and configure the environment.
- **Embeddings**: We use Hugging Face embeddings to process and store the medical data, and load them into Pinecone’s vector store.
- **Google Gemini LLM**: The chatbot uses Google's Gemini API (version 2.0 Flash) to generate responses based on retrieved documents.
- **Retrieval Chain**: Langchain is used to create a retrieval chain to fetch relevant medical information from the Pinecone index and provide contextually relevant answers.

### Key Routes

1. **`/`**: The root endpoint renders the `chat.html` template, which serves as the front end of the chatbot.
2. **`/get`**: This endpoint receives the user's input (question), queries the retrieval chain, and returns the chatbot’s response based on the relevant medical data retrieved.

### Dependencies

This project requires the following Python packages:

- `flask`: Web framework to serve the application.
- `langchain`: Library to create chains for document retrieval and interaction with LLMs.
- `pinecone-client`: Client to interact with the Pinecone vector database.
- `google-generative-ai`: To interact with the Google Gemini model for generating responses.
- `python-dotenv`: To load environment variables from a `.env` file.
- `requests`: For making HTTP requests to external APIs like Google Gemini.

These dependencies are listed in the `requirements.txt` file.

### Example Flow

1. The user sends a healthcare-related question via the front-end interface.
2. The `chat` route processes the question and queries Pinecone's vector search to retrieve the most relevant medical documents.
3. The `rag_chain` uses the Google Gemini model to generate an answer based on the retrieved documents.
4. The chatbot responds with the generated answer.

## Front-End (Optional)

The front-end of this application is a simple `chat.html` file. You can customize this template as per your requirements for the user interface. It takes user input, sends it to the backend, and displays the chatbot's response.

## Contributing

Feel free to fork the repository, create an issue, or submit a pull request if you have any improvements, fixes, or suggestions. Contributions are always welcome!

### How to Contribute

1. Fork the repository.
2. Clone your forked repository to your local machine.
3. Create a new branch for your feature or bug fix.
4. Make the changes and commit them.
5. Push your changes and create a pull request.

## License

This project is open-source and available under the [MIT License](LICENSE).

## Contact

If you have any questions, feel free to reach out to me via GitHub or email.
