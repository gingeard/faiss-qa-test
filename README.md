# FAISS QA

#### This is a simple example of using the [FAISS](https://engineering.fb.com/2017/03/29/data-infrastructure/faiss-a-library-for-efficient-similarity-search/) (Facebook AI Similarity Search), [LangChain](https://python.langchain.com/) framework and [OpenAI API](https://platform.openai.com/docs/api-reference) to find the most similar answer to the question from the predefined list of documents (for example, from FAQ database, Support system and so on).

The script accomplishes the following general steps:

1. Initializes a FAISS vector store with a list of documents by:
    - transforming the list of documents into a vectorized DataFrame,
    - utilizing the OpenAI API for initializing embeddings,
    - creating a vector store from these vectorized documents and embeddings.
3. Performs a similarity search by:
    - using user input to execute a similarity search with FAISS,
    - ranking the documents based on similarity,
    - selecting the most relevant document.
3. Generates a response by:
    - setting up a Language Model chain using the LangChain.
    - adds the user input to the most relevant document (for generating a contextually relevant response)
    - using the OpenAI API to generate a response based on the prompt.

### Install requirements
```bash
python -m venv faiss-qa-venv
source faiss-qa/bin/activate
pip install -r requirements.txt
```

### Before run add .env file with the OpenAI API key
```plain
OPEN_AI_KEY = "sk-xxxxxxxx"
```

You can obtain the API key from the [OpenAI API keys page](https://platform.openai.com/account/api-keys).

### Running example
```plain
$ python faiss-qa.py   # input = "I forgot my password."

If you forgot your password, you can reset it by clicking on the 'Forgot Password?' link
on the login page. Enter your email address, and we will send you instructions on how to reset
your password. For more information, please refer to this link: https://example.com/confluence/recover-password.
```