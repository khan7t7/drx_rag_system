# Dr. X – RAG System with Local LLaMA, FAISS & Embeddings

A Retrieval-Augmented Generation (RAG) system for processing and querying Dr. X's data using local LLaMA, Sentence Transformers, and FAISS. The system extracts text from various file formats (PDF, DOCX, CSV, Excel), chunks it, embeds it into a vector database, and generates responses using a quantized LLaMA model. It also supports translation and performance visualization.

The system performs the following tasks:

- Extracts text from multiple file formats.
- Chunks text with overlap for context preservation.
- Generates embeddings with `all-MiniLM-L6-v2`.
- Stores embeddings in a FAISS vector database.
- Uses a quantized LLaMA model (`Llama-3.2-1B-Instruct-Q4_K_M`) for response generation.
- Visualizes performance metrics and supports Arabic translation.

The implementation is contained in `main.ipynb`, a Jupyter Notebook with modular cells.

## Features

- Supports PDF, DOCX, CSV, and Excel file formats.
- Efficient text retrieval using FAISS.
- Offline response generation with LLaMA.
- Translation to Arabic for multilingual support.
- Performance visualizations for extraction, RAG, and translation.

## Prerequisites

- **Operating System:** Windows, macOS, or Linux.
- **Python:** 3.13.3 (or compatible).
- **Hardware:**
  - Minimum: 8GB RAM, 4-core CPU.
  - Recommended: 16GB RAM, GPU for faster inference.
- **Disk Space:** ~5GB for dependencies, LLaMA model, and data.
- **Internet:** Required for initial setup and model download.

## Setup

### Clone the Repository

```bash
git clone https://github.com/your-username/DrX-RAG-System.git
cd DrX-RAG-System
```

### Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Install Dependencies

Ensure `requirements.txt` is present. Install packages:

```bash
pip install -r requirements.txt
```

Key packages: `tiktoken`, `sentence-transformers`, `faiss-cpu`, `pymupdf`, `python-docx`, `pandas`, `matplotlib`, `seaborn`.

### Download LLaMA Model

Obtain `llama-3.2-1b-instruct-q4_k_m.gguf` from a trusted source (e.g., Hugging Face). Place it in `C:/mystuff/Project1/Llama-3.2-1B-Instruct-Q4_K_M-GGUF/`. Update the path in `main.ipynb` (Cell 6) if stored elsewhere.

### Prepare Data

Create a `Dr.X` folder in the project root. Add PDF, DOCX, CSV, or Excel files with Dr. X's data. Ensure files are readable and not password-protected.

### Create Output Directory

```bash
mkdir outputs
```

Stores logs (`visualization.log`) and plots (`performance_plots.png`).

## Running the System

### Start Jupyter Notebook

```bash
jupyter notebook
```

Open `main.ipynb` in your browser.

### Run Cells in Order

Execute each cell sequentially (Shift+Enter):

1. Installs dependencies.
2. Sets up `tiktoken` tokenizer for chunking.
3. Extracts and chunks text from Dr.X files.
4. Loads `all-MiniLM-L6-v2` for embeddings.
5. Builds FAISS index.
6. Loads LLaMA model.
7. Evaluates performance (extraction, RAG, translation).
8. Generates performance plots.
9. Provides GitHub upload instructions.

### Test Custom Queries

Edit `sample_queries` in Cell 7 to test new queries:

```python
sample_queries = [
    "What is Dr. X's contribution?",
    "Summarize Dr. X's research topics.",
    "What datasets did Dr. X use?",
    "Explain Dr. X's methodology."
]
```

### Check Outputs

- View `outputs/visualization.log` for processing details.
- Open `outputs/performance_plots.png` for visualizations.
- Review notebook outputs for extraction stats and query responses.

### Save Results

Save the notebook to retain outputs. Export plots or logs as needed.

## File Structure

```plaintext
DrX-RAG-System/
├── Dr.X/                     # Input data files (PDF, DOCX, CSV, Excel)
├── outputs/                  # Output files
│   ├── visualization.log     # Performance logs
│   ├── performance_plots.png # Visualization plots
├── main.ipynb                # Main RAG implementation
├── requirements.txt          # Python dependencies
├── README.md                 # This file
└── venv/                     # Virtual environment (not in Git)
```

**Note:** The LLaMA model is not included. Update its path in `main.ipynb` (Cell 6).

## Troubleshooting

### Dependency Installation Fails

- Upgrade pip: `pip install --upgrade pip`.
- Install packages individually: `pip install tiktoken sentence-transformers faiss-cpu`.
- Check Python version compatibility.

### LLaMA Model Error

- Ensure the GGUF file path in Cell 6 is correct.
- Verify the model file (`llama-3.2-1b-instruct-q4_k_m.gguf`) is not corrupted.

### File Extraction Issues

- Warnings (e.g., "Cannot parse header or footer") may occur for complex Excel files. Verify extracted text.
- Ensure Dr.X files are accessible and not locked.

### Slow Performance

- Reduce chunk size in Cell 2 (e.g., `chunk_size=256`) for lower memory use.
- Use a GPU or cloud instance for faster LLaMA inference.

### Plotting Errors

- Confirm `matplotlib` and `seaborn` are installed.
- Check write permissions for `outputs/` directory.

For further assistance, open a GitHub issue with error logs.
