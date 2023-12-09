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
