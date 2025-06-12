# 🎬 Movie Recommender System using NLP and Streamlit

This is a **Content-Based Movie Recommender System** built using **Natural Language Processing (NLP)** and deployed with **Streamlit**. The system recommends movies based on their **tags** (a combination of overview, cast, genres, keywords, and director), using **cosine similarity** of text vectors.

---

## 🔍 Overview

This project is divided into two parts:

1. **Model Training (`.ipynb`)**:  
   - Data preprocessing using `NLTK`, `pandas`, and `ast`
   - Feature extraction from `TMDB 5000 Movies and Credits Dataset`
   - Vectorization using `CountVectorizer`
   - Similarity computation using `cosine_similarity`
   - Model serialization with `pickle`

2. **Frontend App (`app.py`)**:  
   - Interactive **Streamlit** interface
   - Dropdown to select a movie
   - Shows top 8 recommended movies with posters using the **TMDB API**

---

## 🧠 How It Works

### 1. Tag Generation
Each movie is converted into a "tag" string combining:
- **Overview** (movie summary)
- **Genres**
- **Keywords**
- **Top 4 Cast Members**
- **Director**

These are processed to remove spaces and lowercase the text, e.g.:
["Action", "Adventure"] + ["Superhero"] + ["Christian Bale", "Heath Ledger"] + ["Christopher Nolan"]
→ "action adventure superhero christianbale heathledger christophernolan"

### 2. Vectorization
- Text is stemmed using `PorterStemmer`
- `CountVectorizer` extracts top 6000 keywords (excluding stopwords)
- Transformed into vectors using bag-of-words

### 3. Similarity
- Movie similarity is computed using **cosine similarity** between these vectors
- Top 8 similar movies are retrieved (excluding the selected one)

### 4. Streamlit UI
- Dropdown to select a movie
- Posters fetched via TMDB API
- Displayed in a 2-row grid (4 columns each)

---

## 🧾 Dataset

- [`tmdb_5000_movies.csv`](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- [`tmdb_5000_credits.csv`](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

---

## 📦 Dependencies

Create a `requirements.txt` with:

pandas
numpy
scikit-learn
nltk
streamlit
requests
python-decouple


---

## 🔑 API Key Setup

To fetch movie posters, we use the **TMDB API**.

1. Register at [https://www.themoviedb.org/](https://www.themoviedb.org/)
2. Generate an API Key.
3. Create a `.env` file in the root directory:

API_KEY=your_tmdb_api_key_here

## ▶️ How to Run

### Step 1: Train the Model (Run `.ipynb`)
Open and run `movierecom.ipynb` to:
- Process data
- Create `movies.pkl`, `movies_dict.pkl`, `similarity.pkl`

### Step 2: Launch the Streamlit App

```bash
streamlit run app.py
```

### Screenshot

###### Home page
<img src="https://github.com/Sshashank18/MovieRecommender/blob/master/Homepage.png"
     style="float: left; margin-right: 10px;"/>

