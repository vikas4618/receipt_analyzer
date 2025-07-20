🧾 Receipt OCR Mini App
This is a simple full-stack application to upload receipt images, extract text using OCR (Tesseract), and analyze the data using search, sort, and aggregation functions.


🏗️ Features
Upload receipt images (JPG, PNG, JPEG)

Perform OCR using Tesseract to extract text

Store and view uploaded receipts and extracted data

Perform search (keyword, pattern), sort, and aggregate functions

FastAPI backend + Streamlit frontend

SQLite for lightweight storage


🧰 Requirements
Install dependencies in a virtual environment (recommended):

bash
Copy
Edit
pip install fastapi uvicorn pillow pytesseract streamlit
🔧 Additional Setup
Install Tesseract-OCR:

Windows: https://github.com/tesseract-ocr/tesseract

Set path if needed in main.py:

python
Copy
Edit
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
📁 File Structure
bash
Copy
Edit
.
├── main.py         # FastAPI backend
├── app.py          # Streamlit frontend
├── receipts.db     # SQLite database (auto-created)
├── uploads/        # Folder to save uploaded files
🚀 Running the App
✅ Start Backend (FastAPI):
bash
Copy
Edit
python -m uvicorn main:app --reload
This starts the API at:
http://localhost:8000

✅ Start Frontend (Streamlit):
bash
Copy
Edit
python -m streamlit run app.py
This opens the UI in your browser at:
http://localhost:8501

🧪 Functionality Highlights
🔍 Search Algorithms
Search by:

Keyword (e.g., "Amazon", "Total")

Pattern (regex)

Range (e.g., amount ranges)

Uses:

Linear search (default)

Hashed index (for faster search — prototype only)

📊 Sorting Algorithms
Sort data by:

Filename (A-Z)

Amount (if detected)

Date (if pattern recognized)

Uses:

Python built-ins (Timsort, O(n log n))

📈 Aggregation Functions
Compute:

Sum, Mean, Median, Mode of numerical fields (like amounts)

Frequency histograms of vendors or keywords

Monthly trends from dates in OCR text (if found)

🔄 API Endpoints (Backend)
POST /upload/ — Uploads a receipt and extracts text

GET /history/ — Fetches previously uploaded receipt records

GET /search/?q=keyword — Returns receipts matching keyword

GET /sort/?by=amount — Sorts by a field

GET /aggregate/ — Returns statistics like total spend, frequency, etc.

📓 Sample Usage (Streamlit UI)
Upload a receipt image (.jpg, .png, etc.)

Click “Extract” to OCR and save

View extracted text

Click “📜 Load Upload History” to see saved files

Use sidebar options to filter, sort, or analyze

🧹 Notes
All uploads are saved to uploads/ folder

OCR results are saved in receipts.db under the extracted_text column

Basic error handling and validation included
