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

