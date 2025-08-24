# Web Summarizer

**WebSummarizer** is a lightweight Python project that fetches a web page, extracts its main textual content, and uses OpenAI's language model to generate a concise, markdown‑formatted summary.  
It is built as an interactive Jupyter notebook (`Web Summarizer.ipynb`) that demonstrates end‑to‑end web‑scraping, text cleaning, prompt engineering, and API calls, making it an excellent learning resource for anyone interested in combining web data extraction with LLM‑driven summarisation.

---

## Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Project Structure](#project-structure)  
- [Web Scraping Resources](#web-scraping-resources)  
- [License](#license)  
- [Contributing](#contributing)  
- [Acknowledgments](#acknowledgments)  

---

## Overview

The notebook walks through the following steps:

1. **Environment Setup** – Loads environment variables (OpenAI API key) securely.  
2. **HTTP Request** – Retrieves a target URL using a custom user‑agent header.  
3. **HTML Parsing** – Uses **BeautifulSoup** to strip away scripts, styles, and other noise, leaving only the meaningful textual content.  
4. **Prompt Construction** – Crafts a system prompt that tells the model to produce a short (3‑5 sentence) markdown summary, ignoring navigation links and advertisements.  
5. **LLM Interaction** – Calls the OpenAI API (`gpt-5-nano` in the example) and returns the model’s summary.  
6. **Display** – Renders the result as clean markdown inside the notebook.

The repository serves both as a ready‑to‑run summariser and as a teaching aid for best practices in web scraping, prompt design, and API handling.

---

## Features

- **One‑Click Summarisation** – Provide any publicly accessible URL and receive a concise markdown summary.
- **Robust Scraping** – Custom user‑agent header and removal of irrelevant HTML elements (`script`, `style`, `img`, `input`).
- **Prompt Engineering** – System and user prompts are clearly separated for easy tweaking.
- **Error Handling** – Graceful handling of network errors and missing titles.
- **Interactive Display** – Uses IPython’s `display(Markdown(...))` for nicely rendered output.
- **Extensible** – The notebook’s modular structure lets you swap out the LLM, adjust the summarisation length, or add caching.

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/AsutoshaNanda/WebSummarizer.git
   cd WebSummarizer
   ```

2. **Create a virtual environment (optional but recommended)**

   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

3. **Install required packages**

   ```bash
   pip install -r requirements.txt
   ```

   *If a `requirements.txt` file is not present, install the core dependencies manually:*

   ```bash
   pip install openai python-dotenv beautifulsoup4 requests ipython
   ```

4. **Configure your OpenAI API key**

   - Create a `.env` file in the project root:

     ```text
     OPENAI_API_KEY=sk-...
     ```

   - The notebook will automatically load this key via `python-dotenv`.

---

## Usage

Open the Jupyter notebook and follow the cells:

```bash
jupyter notebook "Web Summarizer.ipynb"
```

1. **Run the environment‑setup cell** – loads the API key.  
2. **Enter a URL** when prompted (e.g., `https://cnn.com`).  
3. **Execute the summarisation cell** – the notebook fetches the page, cleans the text, sends the prompt to OpenAI, and displays a markdown summary.

You can also import the core functions into your own scripts:

```python
from summarizer import summarize

summary = summarize("https://example.com")
print(summary)
```

*(The `summarizer.py` module can be created from the notebook’s functions for reusable code.)*

---

## Project Structure

```
WebSummarizer/
├── LICENSE                     # MIT license
├── README.md                   # **You are reading it!**
├── Web Summarizer.ipynb        # Main Jupyter notebook (project file)
└── Web Scrapping/              # Additional scraping examples
    ├── 01 WSP.ipynb            # Basic request + BeautifulSoup demo
    └── 02 WSP.ipynb            # Intermediate scraping techniques
```

- **`Web Summarizer.ipynb`** – The core workflow for summarising any website.  
- **`Web Scrapping/`** – Contains two notebooks that walk you through basic to intermediate web‑scraping techniques. The concepts demonstrated there are also useful when adapting the summariser to more complex sites.

---

## Web Scraping Resources

The **Web Scrapping** folder showcases practical examples, but if you need a structured tutorial covering request handling, headers, session reuse, and HTML parsing, refer to the external guide:

> **Basic to Intermediate Web Scraping with Requests** – https://www.tutorialspoint.com/requests/requests_web_scraping_using_requests.htm

Feel free to follow that guide to extend the summariser (e.g., handling pagination, login‑protected pages, or API‑backed sites).

---

## License

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---

## Contributing

Contributions are welcome! If you’d like to improve the summariser, add support for additional LLMs, or enhance error handling, follow these steps:

1. Fork the repository.  
2. Create a feature branch (`git checkout -b feature/awesome‑feature`).  
3. Commit your changes with clear messages.  
4. Open a Pull Request describing the improvement.

Please ensure that any new code follows the existing style (PEP‑8) and includes appropriate docstrings.

---

## Acknowledgments

- **OpenAI** – For the powerful language models used in summarisation.  
- **BeautifulSoup** – For effortless HTML parsing.  
- **Tutorialspoint** – For the excellent introductory web‑scraping tutorial referenced above.  
- **All contributors** who helped test and refine the notebook.

---

Happy Web Summarising! 🎉
