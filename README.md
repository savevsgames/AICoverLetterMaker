# AICoverLetterMaker

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.12%2B-blue.svg)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.1.52-green.svg)](https://github.com/langchain-ai/langchain)
[![OpenAI](https://img.shields.io/badge/OpenAI-ChatGPT-orange.svg)](https://openai.com/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Ready-brightgreen.svg)](https://colab.research.google.com/)


AICoverLetterMaker is a Python-based cover letter generator that leverages LangChain and OpenAI's Chat models to produce personalized, high-quality cover letters. By extracting details from a job posting, a candidate's resume (PDF), and additional company research, this tool generates tailored cover letters to help job-seekers stand out.

## Table of Contents

- [Features](#features)
- [Installation and Setup](#installation-and-setup)
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

## Installation and Setup

### Prerequisites

- **Python 3.12+** installed on your system.
- **Git** installed.
- (Optional) A GitHub account for contributing.

### 1. Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/savevsgames/AICoverLetterMaker.git
cd AICoverLetterMaker
```

### 2. Set Up a Virtual Environment
It is recommended that you use a virtual environment to manage project dependencies. To create and activate a virtual environment, follow these steps:

On Windows:
```bash
python -m venv .venv
.\.venv\Scripts\activate
```

On macOS/Linux:
```bash
python3 -m venv .venv
source .venv/bin/activate
```

Your prompt should now indicate that the virtual environment is active (e.g., it might show “(.venv)” at the beginning).

### 3. Install Dependencies
With your virtual environment active, install the required packages:

```bash
pip install pdfplumber beautifulsoup4 python-docx python-dotenv langchain langchain-openai openai tiktoken
```
Note: Alternatively, if you want to make a requirements.txt file, you can install all dependencies with:

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables
Create a .env file in the root directory of the project. Include your OpenAI API key and your personal details. For example:

```bash
# .env file

OPENAI_API_KEY=your_openai_api_key
NAME=YOUR NAME
ADDRESS=YOUR ADDRESS
CITY_STATE_ZIP=YOUR CITY, STATE, ZIP
EMAIL=YOUR EMAIL
PHONE=YOUR PHONE NUMBER
GITHUB=https://github.com/YOURGITHUB
LINKEDIN=https://www.linkedin.com/in/YOURLINKEDIN
```

The project uses python-dotenv to load these variables.

### 5. Running the Application
After setting up the environment, you can run the Jupyter Notebook: cover_letter_maker_2-0-0.ipynb locally one cell at a time according to the instructions.

```bash
jupyter notebook
```

Then, open the cover_letter_maker_2-0-0.ipynb notebook and follow the on-screen instructions to generate your cover letter.

### 6. (Optional) Google Colab Setup
If you plan to run the project in Google Colab, use the following two cells at the beginning of your notebook:

Cell 1: Install Dependencies - Python

```bash
!pip install python-dotenv pdfplumber beautifulsoup4 python-docx
```

Cell 2: Environment Setup in Colab - Python

```bash
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

    # Set the application date
    APPLICATION_DATE = datetime.now().strftime("%B %d, %Y")
    print("Application Date:", APPLICATION_DATE)

    # Load environment variables from the .env file
    load_dotenv()

    # Verify that the variables are loaded
    print("OPENAI_API_KEY:", repr(os.getenv("OPENAI_API_KEY")))
    print("NAME:", os.getenv("NAME"))
    print("Google Colab setup complete.")
else:
    print("This block should only be run in Google Colab.")

print("Environment setup complete.")
```

## Contributing

If you wish to contribute:

- Fork the repository.
- Create a new branch for your feature or bug fix.
- Follow the installation and setup instructions above.
- Make your changes and submit a pull request.

## Configuration

### Model Parameters:
The LLM model is instantiated in the code using the ChatOpenAI class. You can adjust parameters like temperature directly in the instantiation.

## Token Usage Tracking:

Helper functions print token usage details after each model call. Use these details to adjust prompt lengths or set limits.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

Author: Greg Barker
GitHub: https://github.com/savevsgames
LinkedIn: https://www.linkedin.com/in/greg-barker-savevsgames/


