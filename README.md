# Document AI Assistant

## Overview
Document AI Assistant is a Python-based system that enables natural language question-answering on text and PDF documents. Built using transformer models, this tool allows users to query documents in plain English and receive instant, context-aware answers without manual reading or searching.

## Features
- **Document Processing**: Supports both TXT and PDF file formats
- **Natural Language Q&A**: Ask questions in plain English about document content
- **AI-Powered Answers**: Utilizes transformer models for accurate information extraction
- **Easy Setup**: Simple installation with minimal dependencies
- **Free to Use**: No API keys or subscription required

## Technical Stack
- **Python 3.8+**
- **Transformers Library** (Hugging Face)
- **PyPDF2** for PDF text extraction
- **Google's FLAN-T5** model for text generation

## Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Quick Install
```bash
pip install torch transformers PyPDF2
```

### Manual Installation
1. Clone the repository:
```bash
git clone https://github.com/yourusername/document-ai-assistant.git
cd document-ai-assistant
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage
```python
from document_assistant import DocumentAIAssistant

# Initialize assistant
assistant = DocumentAIAssistant()

# Load document
assistant.load_document("your_document.pdf")

# Load AI model
assistant.load_model()

# Ask questions
answer = assistant.answer_question("What is the main topic of this document?")
print(answer)
```

### Interactive Mode
Run the interactive script:
```bash
python interactive_mode.py
```

Follow the prompts to:
1. Upload a document (TXT or PDF)
2. Ask questions in natural language
3. Get instant answers

### Google Colab Usage
For Google Colab users, a ready-to-run notebook is available:
```python
# Run in Colab cell
!pip install torch transformers PyPDF2
# Then run the provided notebook cells
```

## How It Works

### 1. Document Processing
- **TXT files**: Direct text extraction
- **PDF files**: Text extraction using PyPDF2
- **Text cleaning**: Removal of special characters and whitespace normalization

### 2. Question Answering Pipeline
1. Document text is loaded and preprocessed
2. User question is combined with document context
3. Transformer model generates answer based on document content
4. Response is validated and returned

### 3. AI Model
- **Default model**: `google/flan-t5-base`
- **Fallback model**: `google/flan-t5-small` (if base model unavailable)
- **Optimized for**: Document-based question answering

## Project Structure
```
document-ai-assistant/
├── document_assistant.py    # Main assistant class
├── interactive_mode.py      # Interactive command-line interface
├── requirements.txt         # Dependencies
├── README.md               # This file
├── examples/               # Example documents
│   ├── sample_document.txt
│   └── sample_report.pdf
└── notebooks/              # Jupyter/Colab notebooks
    └── Document_AI_Assistant.ipynb
```

## API Reference

### DocumentAIAssistant Class

#### Methods
- `__init__(model_name="google/flan-t5-base")`: Initialize assistant
- `load_document(file_path)`: Load and process document
- `load_model()`: Load transformer model
- `answer_question(question)`: Get answer for given question

#### Parameters
- `model_name`: Hugging Face model identifier
- `document_text`: Extracted document content
- `qa_pipeline`: Transformer pipeline object

## Examples

### Example 1: Basic Document Q&A
```python
assistant = DocumentAIAssistant()
assistant.load_document("research_paper.pdf")
assistant.load_model()

questions = [
    "What is the research methodology?",
    "What are the key findings?",
    "What conclusions are drawn?"
]

for q in questions:
    print(f"Q: {q}")
    print(f"A: {assistant.answer_question(q)}\n")
```

### Example 2: Legal Document Analysis
```python
assistant.load_document("contract.pdf")
answer = assistant.answer_question("What are the termination clauses?")
```

## Performance
- **Document size**: Optimized for documents up to 3000 characters per query
- **Response time**: ~2-5 seconds depending on document size
- **Accuracy**: High for fact-based questions within document context

## Limitations
1. **Document size**: Best for documents under 50 pages
2. **Scanned PDFs**: Requires OCR preprocessing
3. **Complex reasoning**: Limited to information extraction, not complex inference
4. **Context window**: Models have token limitations

## Troubleshooting

### Common Issues
1. **Model loading failed**: Try using smaller model (`google/flan-t5-small`)
2. **Memory issues**: Reduce document size or use GPU
3. **PDF extraction errors**: Ensure PDF is text-based (not scanned)

### Solutions
```python
# For model loading issues
assistant = DocumentAIAssistant(model_name="google/flan-t5-small")

# For large documents
# Split document and process in chunks
```

## Contributing
Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

### Development Setup
```bash
git clone https://github.com/yourusername/document-ai-assistant.git
cd document-ai-assistant
pip install -e .
```


## Citation
If you use this project in your research or work:
```bibtex
@software{document_ai_assistant_2024,
  title = {Document AI Assistant},
  author = {Your Name},
  year = {2024},
  url = {https://github.com/yourusername/document-ai-assistant}
}
```

## Support
- **Issues**: [GitHub Issues](https://github.com/yourusername/document-ai-assistant/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/document-ai-assistant/discussions)

## Acknowledgments
- Hugging Face for transformer models
- Google Research for FLAN-T5
- PyPDF2 developers

