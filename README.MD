 ### Simple Resume PDF Parser

This Jupyter Notebook project provides a basic yet functional tool to parse information from PDF resumes or a plain text resume template. It uses regular expressions to extract key details like email addresses, phone numbers, and a predefined set of technical skills. The project is designed to be run within a Jupyter environment, offering an interactive way to upload and process resumes.

## Features

* **PDF Upload (Recommended):** Directly upload PDF resume files within the Jupyter Notebook interface for parsing.
* **Plain Text Template Parsing:** Includes an example for parsing resume content provided as a simple Python string.
* **Text Extraction:** Utilizes `pdfplumber` to robustly extract text content from PDF documents.
* **Email Extraction:** Identifies common email address patterns.
* **Phone Number Extraction:** Detects various phone number formats.
* **Skill Keyword Matching:** Scans the resume for a predefined list of technical skills.
* **Interactive Output:** Displays parsed information clearly within the notebook.

## Installation

1.  **Clone the Repository (Optional - if this were a Git repo):**
    ```bash
    # If you have a Git repository for this project
    # git clone <your-repo-url>
    # cd <your-repo-directory>
    ```

2.  **Install Required Python Libraries:**
    Open your terminal or command prompt and run the following pip command:
    ```bash
    pip install jupyter ipywidgets pdfplumber
    ```
    * `jupyter`: For running the notebook.
    * `ipywidgets`: For the interactive file upload widget.
    * `pdfplumber`: For robust text extraction from PDF files.

## Usage

1.  **Launch Jupyter Notebook/Lab:**
    Navigate to the directory where you saved your `.ipynb` file (or start Jupyter and navigate to it from the browser interface). Then run:
    ```bash
    jupyter notebook
    # or
    # jupyter lab
    ```
    This will open Jupyter in your web browser.

2.  **Open the Notebook:**
    Locate and click on the `resume_parser.ipynb`

3.  **Run All Cells:**
    Execute all cells in the notebook sequentially (e.g., by clicking "Cell" -> "Run All" or by running each cell individually using `Shift + Enter`).

### Option 1: Parsing Uploaded PDF Resumes (Recommended)

1.  After running all cells, an "Upload a Resume (PDF) to Parse:" section will appear with an **"Upload" button**.
2.  Click this button to browse and select a PDF resume file from your local machine.
3.  Once the PDF is uploaded, the script will automatically process it, and the extracted email, phone number, and skills will be displayed directly below the upload widget.

### Option 2: Parsing from a Predefined Text Template

1.  Scroll to the section in the notebook that contains the `sample_resume_content` variable.
2.  You can modify the multi-line string content of `sample_resume_content` directly within the notebook cell to represent a new resume.
3.  Run the cell containing the `sample_resume_content` and the subsequent parsing and display cells.
4.  The parsed information from your modified template will be displayed below.

## Customization

* **Skill Keywords:**
    You can easily customize the list of `skill_keywords` in the `parse_simple_resume` function to include more specific or relevant skills for your use case.
    ```python
    skill_keywords = [
        "Python", "Java", "SQL", "JavaScript", "React", "Angular", "Vue.js",
    ]
    ```
* **Regular Expressions:**
    For more precise extraction of emails or phone numbers (e.g., handling country-specific phone formats), you can modify the regular expressions in the `parse_simple_resume` function.
    * **Email Regex:** `r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'`
    * **Phone Regex:** `r'(\+?\d{1,3}[-.\s]?)?(\(?\d{3}\)?[-.\s]?){2}\d{4}'`

## Limitations

This simple parser has several limitations:

* **Basic Text Extraction:** Relies heavily on the quality of text extraction from the PDF.
    * **Scanned PDFs:** It will perform poorly or fail on scanned image-based PDFs, as it lacks Optical Character Recognition (OCR) capabilities. For such files, you would need an additional OCR step (e.g., using Tesseract or cloud OCR services).
    * **Complex Layouts:** Resumes with highly complex or unusual layouts might lead to jumbled or incomplete text extraction, affecting parsing accuracy.
* **Keyword-Based Skills:** Skill extraction is purely based on matching predefined keywords. It does not understand synonyms, context, or infer skills from job descriptions.
* **No Named Entity Recognition (NER):** It does not use advanced NLP techniques to identify categories like "experience," "education," "projects," job titles, or company names.
* **No Semantic Understanding:** The parser has no understanding of the meaning or relationships between the extracted pieces of information.
* **Rule-Based:** Its accuracy is limited by the quality and comprehensiveness of the regular expressions and keyword lists.
* **Not Production Ready:** This project is for demonstration and learning purposes. A production-grade resume parser would require robust error handling, more sophisticated NLP models, and often, machine learning.  
