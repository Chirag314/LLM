# LLM1

This code demonstrates how to use the OpenAI API with Weights & Biases for LLMs.

Dependencies:

  1. openai
  2. tiktoken
  3. wandb
     
Key Features:

 * Logs OpenAI API calls to Weights & Biases.
 * Encodes and decodes text using tiktoken encoding.
 * Samples text with different temperatures and top-p values.
 * Demonstrates OpenAI Chat API.
   
Code Breakdown:

Imports:
  tiktoken for encoding and decoding text.
  wandb for logging OpenAI API calls.
  openai for accessing the OpenAI API.
  getpass for securely entering the OpenAI API key.
  
OpenAI API Key:
  Checks if the OpenAI API key is set as an environment variable.
  If not, prompts the user to enter the key securely.
Sets the OpenAI API key.

WandB Integration:
  Initializes wandb with project and job type.
  
Tiktoken Encoding:
  Gets the encoding for the "text-davinci-003" model.
  Encodes and decodes a sample text.
  Prints the token IDs and their corresponding decoded characters.
  
Text Generation:
  Defines a function generate_with_temperature to sample text with different temperatures.
  Generates and prints text samples with different temperatures.
  Defines a function generate_with_topp to sample text with different top-p values.
  Generates and prints text samples with different top-p values.
  
OpenAI Chat API:
  Defines the model to use for the chat.
  Creates a chat interaction with the user.
  Prints the response from the assistant.
  Logging and Finishing:
  Logs all OpenAI API calls to wandb.
  Finishes the wandb run.
  
Resources:

OpenAI API: https://openai.com/blog/openai-api
Tiktoken: https://github.com/openai/tiktoken
Weights & Biases: https://wandb.ai/site

# LLM2

This code demonstrates how to use the OpenAI API with Weights & Biases to generate support questions for W&B users.

Dependencies:

  openai
  tiktoken
  wandb
  rich
  pandas
  tenacity
  Key Features:

1. Generates support questions based on W&B documentation.
2. Uses OpenAI's retry logic to handle API rate limits.
3. Extracts context, question, and answer from model generations.
4. Saves generated examples as a CSV and logs them to Weights & Biases.
   
Code Breakdown:

Imports:

  tiktoken for encoding and decoding text.
  wandb for logging OpenAI API calls and generated data.
  openai for accessing the OpenAI API.
  getpass for securely entering the OpenAI API key.
  rich for displaying markdown text.
  pandas for working with dataframes.
  tenacity for retrying API calls.
  
OpenAI API Key:

  Checks if the OpenAI API key is set as an environment variable.
  If not, prompts the user to enter the key securely.
  Sets the OpenAI API key.
  
Logging into Weights & Biases:
  
  Initializes wandb with project and job type.
  OpenAI API Calls with Backoff:
  Defines a completion_with_backoff function to retry OpenAI API calls.
  This function uses a random exponential backoff strategy to avoid rate limits.
  
Model Configuration:
  Sets the model name to be used for generating support questions.
  
Prompt Templates:
  Reads system and user prompts from external files.
  
Generating Support Questions:
   Defines functions for generating support questions based on:
  Few-shot learning from real user queries.
  Specific document fragments.
  These functions use the defined prompt templates and model name.
  
Context Extraction:
  Defines a extract_random_chunk function to extract a random chunk of text from a document.
  This function ensures the chunk length is within the model's context window.
  
Generation Parsing:
  Defines a parse_generation function to extract context, question, and answer from the model's output.
  
Data Processing and Logging:
  Generates support questions for multiple documents.
  Parses each generation and stores the extracted information.
  Converts the extracted data to a pandas dataframe.
  Saves the dataframe as a CSV file.
  Logs the dataframe and CSV file to Weights & Biases.
  
Finishing Weights & Biases Run:
  Logs all information and finishes the wandb run.
Running the Code:

Install the required dependencies:
  pip install -Uqqq rich openai tiktoken wandb tenacity
Set your OpenAI API key as an environment variable:
export OPENAI_API_KEY="YOUR_API_KEY"
Run the code:
Python
!python your_script.py
Use code with caution. Learn more
Resources:

OpenAI API: https://openai.com/
Tiktoken: https://github.com/openai/tiktoken
Weights & Biases: https://wandb.ai/site
Rich: https://rich.readthedocs.io/en/stable/introduction.html
Pandas: https://medium.com/@simon1-provost/https-pandas-pydata-org-docs-reference-api-pandas-dataframe-html-6421e4ff1f7b


# LLM3

This code demonstrates how to use Langchain to retrieve relevant documents and answer user queries based on those documents.

Dependencies:

 * openai
 * tiktoken
 * wandb
 * rich
 * tenacity
 * langchain
 * unstructured
 * tabulate
 * pdf2image
 * chromadb
   
Key Features:

  - Finds all markdown files in a directory and loads them into a Langchain document.
  - Counts the number of tokens in each document using the OpenAI tokenizer.
  - Splits the documents into smaller sections using the MarkdownTextSplitter.
  - Embeds the text in each section using the OpenAI embeddings and stores the vectors in a Chroma database.
  - Retrieves relevant documents based on a user query.
  - Uses the Langchain prompts and OpenAI chat API to answer the user query based on the retrieved documents.
  - Logs the results to Weights & Biases.
  - 
Code Breakdown:

Imports:
  - Langchain libraries for document loading, text splitting, embeddings, retrieval, prompts, and LLMs.
  - OpenAI API for embeddings and chat API.
  - Tiktoken for encoding and decoding text.
  - Wandb for logging.
  - Rich for displaying markdown text.
  - Tenacity for retrying API calls.
  - Other libraries for supporting functionalities.
    
OpenAI API Credentials:
    Checks if the OpenAI API key is set as an environment variable.
    If not, prompts the user to enter the key securely.
    Sets the OpenAI API key.
    
WandB Logging:
    Sets the WandB project and initializes the run.
    
Model and Document Loading:
     Defines the model name to be used for embeddings.
    Downloads and loads sample markdown documents.
    
Tokenization and Splitting:
    Creates a Tiktoken encoder for the specified model.
    Counts the number of tokens in each document.
    Splits the documents into smaller sections using a MarkdownTextSplitter.
    
Embedding and Retrieval:
    Creates an OpenAIEmbeddings object for embedding text.
    Creates a Chroma database to store the embedded vectors.
    Converts the document sections to a LangChain document and embeds them.
    Creates a retriever from the embedded document database.
    
User Query and Retrieval:
    Defines a user query.
    Retrieves relevant documents based on the query using the retriever.
    Prints the source of the retrieved documents.
    
Prompt and Answer Generation:
    Defines a Langchain prompt template for combining context and questions.
    Creates a prompt using retrieved documents and the user query.
    Uses OpenAI through Langchain to generate an answer based on the prompt.
    Displays the generated answer in markdown format.
    
RetrievalQA Chain:
    Creates a RetrievalQA chain using Langchain.
    Runs the chain with the user query to obtain the answer.
    Displays the answer in markdown format.
    
Logging and Finishing:
    Logs results to Weights & Biases.
    Finishes the WandB run.
    
Running the Code:

Install the required dependencies:
    pip install -Uqqq rich openai tiktoken wandb tenacity langchain unstructured tabulate pdf2image chromadb

Set your OpenAI API key as an environment variable:
export OPENAI_API_KEY="YOUR_API_KEY"
Run the code:
Python
!python your_script.py

Resources:

Langchain: https://langchain.readthedocs.io/en/latest/: https://langchain.readthedocs.io/en/latest/
OpenAI API: https://openai.com/blog/openai-api: https://openai.com/blog/openai-api
Tiktoken: https://github.com/openai/tiktoken: https://github.com/openai/tiktoken
Weights & Biases: https://wandb.ai/site: https://wandb.ai/site
Note: This readme provides a high-level overview of the code. For detailed information, refer to the code comments and the resources listed above.


