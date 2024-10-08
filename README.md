# OCR, Summarization, and QA System with Multilingual Support

This project is an advanced system that performs Optical Character Recognition (OCR) on images and provides summarization, question-answering (QA), and translation functionalities. It supports both English and Arabic languages and allows users to upload images for OCR processing combined with text for further operations.

## Features

- **OCR (Optical Character Recognition)**: Extract text from images using a custom OCR model running on GPU for faster processing.
- **Summarization**: Summarizes extracted text using a pre-trained English summarization model (`facebook/bart-large-cnn`).
- **Question-Answering (QA)**: Supports QA in both English and Arabic with different models. For Arabic, it includes translation of extracted text.
- **Gradio Interface**: Provides a user-friendly web interface using Gradio for easy interaction with the system.

## Table of Contents


- [Features](#features)
- [Contributing](#contributing)
- [License](#license)



## Key Code Components

### 1. OCR Processing

Uses the `ucaslcl/GOT-OCR2_0` model to extract text from images:

```python
tokenizer = AutoTokenizer.from_pretrained('ucaslcl/GOT-OCR2_0', trust_remote_code=True)
model = AutoModel.from_pretrained('ucaslcl/GOT-OCR2_0', trust_remote_code=True, device_map='cuda')
```

### 2. Summarization

Summarizes the extracted text in English using facebook/bart-large-cnn:

```python

summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
```

### 3. Question-Answering (QA)

Supports English QA using deepset/roberta-base-squad2:

```python

pipe_qa_en = pipeline('question-answering', model="deepset/roberta-base-squad2")

Supports Arabic QA using gp-tar4/QA_FineTuned:
```
```python

pipe_qa_ar = pipeline("question-answering", model="gp-tar4/QA_FineTuned")
```
### 4. Translation (English to Arabic)

Translates text from English to Arabic using Helsinki-NLP/opus-mt-en-ar:

```python

pipe_to_arabic = pipeline("translation", model="Helsinki-NLP/opus-mt-en-ar")
```
## Contributing

Contributions are welcome! Please submit pull requests or report issues in the GitHub repository.
License

This project is licensed under the MIT License - see the LICENSE file for details.

## Video
https://drive.google.com/file/d/1Y8tHbZeRxOkjRa6NhHh3YvoxEa05eRF6/view?usp=sharing

