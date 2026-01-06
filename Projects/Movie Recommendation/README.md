

# End-to-End Movie Recommendation System Project Using Machine Learning

This project comprehensively covers the development of an **end-to-end movie recommendation system** leveraging machine learning techniques, culminating in a deployable web application. The project uses a movie dataset and focuses on building a **content-based filtering recommendation system**.

---
## Project Architecture & Workflow

The system follows a structured pipeline to transform raw movie metadata into a functional recommendation engine.



### The Workflow Timeline
| Phase | Action | Purpose |
| :--- | :--- | :--- |
| **I. Data Ingestion** | Load `movies.csv` and `credits.csv`. | Acquire metadata (cast, crew, plot). |
| **II. Transformation** | Merge datasets & flatten JSON objects. | Create a usable, flat feature set. |
| **III. NLP Pipeline** | Stemming, lowercasing, space removal. | Normalize text for the computer. |
| **IV. Vectorization** | Apply `CountVectorizer`. | Convert "text soup" into math vectors. |
| **V. Engine Building** | Compute `Cosine Similarity`. | Quantify "closeness" between movies. |
| **VI. UI Development** | Build Frontend with `Streamlit`. | Create a user-friendly entry point. |

---

## <Database size={24} /> Key Concepts and Project Overview

### Recommender Systems (RS)
* **Offline (in-store) RS:** Involves salespersons recommending products based on knowledge of product similarity and customer preference.
* **Online RS:** Uses machine learning to suggest products/videos/music based on user interaction and content similarity.
* **Significance:** RS is crucial in e-commerce platforms like Amazon, Flipkart, and media platforms like Spotify, YouTube, Facebook, Instagram.

### Types of RS
1.  **Content-Based Filtering:** Recommends items similar to those the user liked before, based on item attributes.
2.  **Collaborative Filtering:** Recommends items based on user similarity and user behavior patterns.
3.  **Hybrid Systems:** Combine content-based and collaborative filtering, widely used by large companies like YouTube.



> **Project Choice:** focuses on building a **content-based recommender system** for movies, with plans to explore collaborative and hybrid filtering in future projects.

---

## <Layout size={24} /> Dataset and Data Exploration

* **Dataset Used:** PMDB 500 Movies Dataset.
* **Metadata:** movie ID, title, budget, genres, keywords, cast, crew (directors, editors, music directors), overview, popularity, production companies, release dates, revenue, runtime, language, status, tagline, and voting statistics.
* **Structure:** Includes two main dataframes: **movies** and **credits**.

### Data Preparation & Merging
* **Merging:** Join datasets on the movie title to create a unified dataframe (approx. 123 columns).
* **Cleaning:** Drop irrelevant columns (budget, revenue, popularity) as they don't contribute to content similarity.
* **Feature Selection:** Retain `genres`, `keywords`, `cast` (top 3), `crew` (directors), and `overview`.

---

## <Code size={24} /> Data Preprocessing

### Cleaning Steps
1.  **JSON Flattening:** Convert nested lists/dictionaries into flat lists of strings.
2.  **Space Removal:** Convert "Science Fiction" to "ScienceFiction" to ensure they are treated as a single entity during vectorization.
3.  **Stemming:** Apply root word extraction using **NLTK**.
4.  **Stop Words:** Remove common filler words (e.g., "the", "is") that lack semantic weight.

### Creating the "Tags" Column
Combine all processed features into a single **"tags"** column per movie to form a textual profile.

---

## Feature Engineering: Vectorization & Similarity

### Text Vectorization
We convert text into numerical vectors using **CountVectorizer** (Bag-of-Words).
* **Vocabulary:** Limited to the 5,000 most frequent words.

### Similarity Metric
We compute pairwise similarity using **Cosine Similarity**. 
$$ \text{cosine similarity} = S_C (A, B) = \cos(\theta) = \frac{A \cdot B}{\|A\| \|B\|} $$

---

## Recommendation Logic
1.  Find the **index** of the input movie.
2.  Retrieve **similarity scores** from the pre-computed matrix.
3.  **Sort** scores in descending order.
4.  Fetch the **top 5** most similar movies.

---

## Web Application & Deployment

* **Framework:** Built with **Streamlit** for rapid UI development.
* **Visuals:** Integrated **TMDb API** to fetch movie posters dynamically using movie IDs.
* **Deployment:** Steps provided for **Heroku** using `Procfile` and `requirements.txt`.

---

## Project Workflow Timeline

| Step | Description |
| :--- | :--- |
| **Data Collection** | Download PMDB 500 datasets |
| **Data Merging** | Join datasets on movie title |
| **Data Cleaning** | Flatten JSON, clean text |
| **Vectorization** | Apply CountVectorizer |
| **Similarity** | Compute Cosine Similarity Matrix |
| **Web App** | Build Streamlit UI & TMDb API integration |
| **Deployment** | Deploy to Heroku/Cloud |

---

## Important Libraries

* **Pandas & NumPy:** Data handling.
* **NLTK:** Text stemming.
* **Scikit-learn:** Vectorization and Similarity.
* **Streamlit:** Web UI.
* **Requests:** API interaction.

---

## Key Insights & Conclusions
* Content-based filtering is effective for metadata-rich datasets.
* Preprocessing (Stemming/Stopword removal) is vital for vector quality.
* Visual enrichment via APIs significantly improves the user experience.

<CheckCircle color="green" size={20} /> **Summary of Recommendations:** Merge metadata, clean tags, vectorize, compute similarity, and build an interactive UI.

---

**Closing Note:** This project provides a comprehensive walkthrough of building a movie recommender system from scratch, demonstrating practical ML applications in the recommendation domain.
