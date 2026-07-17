# RAG-Pipelines

Retrieval-Augmented Generation (RAG) pipelines built with **LangChain**, **Mistral AI**, and **ChromaDB**. This project provides a foundation for ingesting documents (including PDFs), embedding and storing them in a vector database, and querying them with an LLM to produce grounded, context-aware answers.

## Overview

RAG (Retrieval-Augmented Generation) combines a retrieval step with a generative language model: relevant chunks of your own documents are fetched from a vector store and passed to the LLM as context, so answers are grounded in your data instead of relying purely on the model's parametric knowledge.

This repository is set up as a starting point for building and experimenting with RAG pipelines, with the core dependencies already wired in for:

- **Document loading & parsing** — via `pypdf` for PDF ingestion
- **Chunking & orchestration** — via `langchain-core`, `langchain-community`, `langchain-classic`, and `langchain-text-splitters`
- **LLM & embeddings provider** — via `langchain-mistralai` (Mistral AI)
- **Vector storage** — via `chromadb`
- **Configuration** — via `python-dotenv` / `pydantic-settings`

## Tech Stack

| Component | Library |
|---|---|
| Orchestration | LangChain (`langchain-core`, `langchain-community`, `langchain-classic`) |
| LLM / Embeddings | Mistral AI (`langchain-mistralai`) |
| Vector store | ChromaDB |
| PDF parsing | pypdf |
| Config management | python-dotenv, pydantic-settings |
| Package management | [uv](https://docs.astral.sh/uv/) |

## Project Structure

```
RAG-Pipelines/
├── docs/                # Project documentation
├── main.py              # Entry point
├── pyproject.toml       # Project metadata & dependencies
├── requirements.txt     # Pinned dependencies (pip-installable)
├── uv.lock              # Locked dependency versions (uv)
└── .python-version      # Python version pin
```

## Requirements

- Python >= 3.11
- A [Mistral AI API key](https://console.mistral.ai/)
- [uv](https://docs.astral.sh/uv/) (recommended) or `pip`

## Installation

Clone the repository:

```bash
git clone https://github.com/thukralhanshika64-design/RAG-Pipelines.git
cd RAG-Pipelines
```

Install dependencies with `uv` (recommended, uses the included `uv.lock`):

```bash
uv sync
```

Or with `pip`:

```bash
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Configuration

Create a `.env` file in the project root with your Mistral AI credentials:

```env
MISTRAL_API_KEY=your_api_key_here
```

## Usage

Run the entry point:

```bash
uv run main.py
```

Or, if using a virtual environment directly:

```bash
python main.py
```

> The pipeline (document ingestion → chunking → embedding → vector storage → retrieval-augmented querying) is under active development. See the `docs/` folder for design notes and further details.

## Roadmap

- [ ] Document ingestion pipeline (PDF and beyond)
- [ ] Text splitting / chunking strategy
- [ ] Embedding generation via Mistral AI
- [ ] Vector storage and similarity search with ChromaDB
- [ ] Retrieval-augmented query interface
- [ ] Evaluation of retrieval quality

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to open an issue or submit a pull request.

## License

No license has been specified for this repository yet. Consider adding one (e.g., MIT, Apache 2.0) to clarify how others can use this project.
