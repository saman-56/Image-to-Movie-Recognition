# 🎬 Image-to-Movie Recognition

An AI-powered computer vision project that identifies a movie from an input image by comparing its visual features with frames extracted from a movie dataset.

The system uses **OpenAI CLIP** to generate visual embeddings and **FAISS** for efficient similarity search. A Flask API allows users to upload an image and receive the predicted movie along with confidence information and similar frames.

## 🚀 Features

* 🎞️ Extract frames from movie files automatically
* 🗂️ Generate metadata for extracted frames
* 🧠 Generate image embeddings using CLIP (ViT-B/32)
* 🔎 Perform fast similarity search using FAISS
* 🖼️ Support image upload for movie prediction
* ✂️ Multi-crop image processing for improved matching
* 📊 Return prediction confidence and top candidate movies
* 🌐 Flask-based API for movie recognition

## 🛠️ Technologies Used

* **Python**
* **OpenCV** – movie processing and frame extraction
* **CLIP** – visual feature/embedding generation
* **PyTorch** – deep learning framework used with CLIP
* **FAISS** – vector similarity search
* **Flask** – web API
* **Pillow (PIL)** – image processing
* **NumPy** – numerical computation
* **Pandas** – metadata processing
* **TQDM** – progress tracking

## 🔄 Project Workflow

```text
Movie Dataset
     │
     ▼
Frame Extraction
     │
     ▼
Metadata Generation
     │
     ▼
CLIP Embedding Generation
     │
     ▼
FAISS Vector Index
     │
     ▼
Input Image
     │
     ▼
Image Embedding
     │
     ▼
Similarity Search
     │
     ▼
Movie Prediction
```

## 📁 Project Structure

```text
Image-to-Movie-Recognition/
│
├── 01_extract_frames.py
├── 02_build_metadata.py
├── 03_generate_embeddings.py
├── 04_build_faiss_index.py
├── 05_search_api.py
├── test_search.py
└── README.md
```

### File Description

| File                        | Description                                                          |
| --------------------------- | -------------------------------------------------------------------- |
| `01_extract_frames.py`      | Extracts frames from movie files at a specified interval             |
| `02_build_metadata.py`      | Creates metadata containing movie names, frame paths, and timestamps |
| `03_generate_embeddings.py` | Generates normalized CLIP embeddings for movie frames                |
| `04_build_faiss_index.py`   | Builds a FAISS similarity-search index from the embeddings           |
| `05_search_api.py`          | Provides a Flask API for image-based movie prediction                |
| `test_search.py`            | Used for testing the movie search functionality                      |

## ⚙️ How It Works

### 1. Frame Extraction

Movie files such as `.mp4`, `.mkv`, `.avi`, and `.mov` are processed using OpenCV. Frames are extracted at regular intervals and organized according to their movie.

### 2. Metadata Generation

Information about each extracted frame is stored in a CSV file, including:

* Movie name
* Frame path
* Timestamp

### 3. Visual Embeddings

The project uses the **CLIP ViT-B/32 model** to convert movie frames into numerical feature vectors. These embeddings represent the visual characteristics of each frame.

### 4. FAISS Indexing

The generated embeddings are stored in a FAISS index. The project supports both:

* `flat` – exact similarity search
* `ivf` – approximate and more scalable similarity search

### 5. Movie Recognition API

The Flask application accepts an input image and generates its CLIP embedding. The embedding is compared against the FAISS index to find visually similar movie frames.

The system uses multiple image crops and weighted voting to determine the most likely movie.

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/saman-56/Image-to-Movie-Recognition.git
cd Image-to-Movie-Recognition
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Install the required dependencies:

```bash
pip install opencv-python numpy pandas tqdm pillow torch faiss-cpu flask
```

Install the CLIP package used by the project:

```bash
pip install git+https://github.com/openai/CLIP.git
```

## ▶️ Running the Project

### Step 1 — Extract Movie Frames

Configure the movie dataset and output directories in:

```text
01_extract_frames.py
```

Then run:

```bash
python 01_extract_frames.py
```

### Step 2 — Generate Metadata

Run:

```bash
python 02_build_metadata.py
```

### Step 3 — Generate CLIP Embeddings

Run:

```bash
python 03_generate_embeddings.py
```

### Step 4 — Build the FAISS Index

Run:

```bash
python 04_build_faiss_index.py
```

### Step 5 — Start the Movie Recognition API

Run:

```bash
python 05_search_api.py
```

The Flask server runs on:

```text
http://localhost:5000
```

Open the address in a browser and upload an image to test the movie recognition system.

## 📡 API

### Predict Movie

**Endpoint:**

```text
POST /predict_movie
```

Upload an image using the form field:

```text
image
```

The API returns information such as:

```json
{
  "prediction": "Movie Name",
  "confidence": 0.85,
  "vote_score": 4.25,
  "top_candidates": [],
  "nearest_frames": []
}
```

## 🎯 Applications

This project demonstrates how computer vision and vector similarity search can be used for:

* Movie identification
* Visual content retrieval
* Image-to-video matching
* Multimedia search systems
* Content-based retrieval
* AI-powered media analysis

## 🔮 Future Improvements

* Add a web-based frontend with a modern UI
* Improve recognition accuracy using larger datasets
* Add GPU-optimized inference
* Support more advanced vision models
* Add movie posters and additional movie metadata
* Deploy the API as a cloud service
* Add automated evaluation metrics
* Improve path configuration so the project can run on different computers without modifying source files

## 👥 Team Project

This project was developed collaboratively as a group project.

### Contributions

* Movie frame extraction and preprocessing
* Metadata generation
* CLIP-based feature extraction
* FAISS vector indexing
* Similarity search and movie prediction API
* Testing and integration

> **Note:** Individual contributions can be listed here according to each team member's actual work.

## 📌 Disclaimer

This project is intended for educational and research purposes. Movie files and datasets used for testing should be obtained and used in accordance with applicable copyright and licensing requirements.

## ⭐ Project Highlights

**Computer Vision • Deep Learning • CLIP • FAISS • Similarity Search • Image Retrieval • Flask API • Python**
