# AICoverLetterMaker

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.13%2B-blue.svg)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.1.52-green.svg)](https://github.com/langchain-ai/langchain)
[![OpenAI](https://img.shields.io/badge/OpenAI-ChatGPT-orange.svg)](https://openai.com/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Ready-brightgreen.svg)](https://colab.research.google.com/)


AICoverLetterMaker is a Python-based cover letter generator that leverages LangChain and OpenAI's Chat models to produce personalized, high-quality cover letters. By extracting details from a job posting, a candidate's resume (PDF), and additional company research, this tool generates tailored cover letters to help job seekers stand out.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Local Setup](#local-setup)
  - [Google Colab Setup](#google-colab-setup)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Automated Cover Letter Generation:**  
  Uses an LLM (via LangChain and OpenAI) to generate personalized cover letters from user-supplied inputs.

- **Job Posting Processing:**  
  Extracts the company name and summarizes job details from a single input prompt.

- **Resume Extraction:**  
  Parses and extracts text from PDF resumes.

- **Web Scraping and Summarization:**  
  Retrieves company and context information from provided URLs and summarizes them.

- **Environment Variable Management:**  
  Loads sensitive information (e.g., API keys) securely from a `.env` file.

- **Token Usage Logging:**  
  (Optional) Prints token usage details to help fine-tune prompt lengths and model parameters.

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/savevsgames/AICoverLetterMaker.git
   cd AICoverLetterMaker
   ```
2. **Install Dependencies:**

    You can install the required Python packages via pip:

    ```bash
    pip install -r requirements.txt
    ```
If you don’t have a requirements.txt file yet, ensure you have at least the following packages installed:

- langchain-openai
- python-dotenv
- pdfplumber
- requests
- beautifulsoup4
- python-docx


3. **Set Up Environment Variables:**

    Create a .env file in the root directory with the following content (fill in your details):

    env
    ```bash
    OPENAI_API_KEY=your_openai_api_key
    NAME=Your Name
    ADDRESS=Your Address
    CITY_STATE_ZIP=Your City, State, ZIP
    EMAIL=Your Email
    PHONE=Your Phone Number
    GITHUB=https://github.com/YOUR_GITHUB
    LINKEDIN=https://www.linkedin.com/in/YOUR_LINKEDIN
    ```

## Usage

## Local Setup

To run the notebook or Python script locally. The code:

Loads environment variables (using python-dotenv).
Instantiates the LLM model once.
Prompts for job posting details, extracts resume text from a PDF, scrapes additional context, and then generates a cover letter.
Saves the generated cover letter as a DOCX file.
Simply open the Jupyter Notebook (or run the Python script) in your local environment and follow the on-screen prompts.

## Google Colab Setup

If you’re running in Google Colab, use the following two blocks at the start:

Block 1: Install Required Packages

```bash
!pip install python-dotenv pdfplumber beautifulsoup4 python-docx
```

Block 2: Environment Setup in Colab

```bash
python
Copy
#%%
import os
import re
import traceback
import pdfplumber
import requests
from bs4 import BeautifulSoup
from docx import Document
from IPython.display import Markdown, display
from dotenv import load_dotenv
from datetime import datetime
import sys

if 'google.colab' in sys.modules:
    from google.colab import files

    # Upload your .env file
    uploaded = files.upload()  # Prompts you to upload your .env file

    # Format the date as "Month Day, Year"
    APPLICATION_DATE = datetime.now().strftime("%B %d, %Y")
    print("Application Date:", APPLICATION_DATE)

    # Load environment variables from the .env file
    load_dotenv()

    # Verify that variables are loaded
    print("OPENAI_API_KEY:", repr(os.getenv("OPENAI_API_KEY")))
    print("NAME:", os.getenv("NAME"))
    print("Google Colab setup complete.")
else:
    print("This block should only be run in Google Colab.")

print("Environment setup complete.")
```

Then proceed with the rest of your code (which instantiates the model and calls your utility functions).

## Configuration

### Model Parameters:
The LLM model is instantiated in the code using the ChatOpenAI class. You can adjust parameters like temperature directly in the instantiation.

## Token Usage Tracking:

Helper functions print token usage details after each model call. Use these details to adjust prompt lengths or set limits.

## Contributing

Contributions are welcome! If you have suggestions, bug reports, or improvements, please open an issue or submit a pull request. For more details, see the CONTRIBUTING.md file.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

Author: Greg Barker
GitHub: https://github.com/savevsgames
LinkedIn: https://www.linkedin.com/in/greg-barker-savevsgames/

This README was generated using a format inspired by my GitHub README Generator repository.
# AICoverLetterMaker
