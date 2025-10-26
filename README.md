# 🎬 Movie Recommendation System

This project is a **content-based movie recommendation system** built using **Python**, **pandas**, **scikit-learn**, and **Streamlit**.  
It recommends up to **500 similar movies** based on the cast and crew of a given movie title.

---

## 🚀 Features

- Uses **TF-IDF Vectorization** and **Cosine Similarity** to find similar movies.  
- Recommends movies based on **cast and crew similarity**.  
- Simple and interactive **Streamlit web app** interface.  
- Displays up to **500 movie recommendations** for any given movie.  

---

## 🧠 How It Works

1. The system loads a movie dataset (`movies.csv`).
2. It combines the `cast` and `crew` columns into a single textual feature.
3. The text data is transformed into numerical vectors using **TF-IDF**.
4. **Cosine similarity** is computed between all movie vectors.
5. When a user inputs a movie title, the system finds the most similar ones.

---

## 🗂️ Dataset

The project expects a CSV file containing at least the following columns:

| Column | Description |
|:-------|:-------------|
| `title` | Movie title |
| `cast` | Main actors/actresses |
| `crew` | Directors, producers, and other crew members |

Example row:

| title | cast | crew |
|:------|:------|:------|
| Inception | Leonardo DiCaprio, Joseph Gordon-Levitt | Christopher Nolan, Emma Thomas |

> 💡 You can use your own movie dataset or download a TMDB dataset.

---

## 🧰 Requirements

Install the required Python libraries before running the app:

```bash
pip install pandas scikit-learn streamlit
```

---

## 🏗️ Project Structure

```
movie-recommender/
│
├── movies.csv.zip           # Dataset file
├── app.py                   # Main Streamlit app
└── README.md                # Project documentation
```

---

## ▶️ How to Run the App

1. **Clone or download** this repository.
2. Place your dataset file (`movies.csv.zip`) in the same directory as `app.py`.
3. Run the following command in your terminal:

   ```bash
   streamlit run app.py
   ```

4. Open the Streamlit web app in your browser (usually `http://localhost:8501`).

---

## 🖥️ Usage

1. Enter a movie name in the input box (e.g., `Inception`).
2. Click on **“Recommend”**.
3. View the top 500 similar movies displayed below.

---

## ⚙️ Code Overview

### Key Steps:
- **Data Preprocessing:** Selects `title`, `cast`, and `crew` columns.
- **Feature Extraction:** Applies `TfidfVectorizer` with English stop words.
- **Similarity Calculation:** Uses `cosine_similarity` to compare movie vectors.
- **Recommendation Function:** Sorts and retrieves the top 500 most similar titles.

### Example Function:

```python
def recommend(title):
    title_lower = title.lower()
    titles_lower = data['title'].str.lower().tolist()
    if title_lower not in titles_lower:
        return ["Movie not found! Please check the title."]
    idx = titles_lower.index(title_lower)
    sim_scores = list(enumerate(cosine_sim[idx]))
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    movie_indices = [i[0] for i in sim_scores[1:501]]
    return data['title'].iloc[movie_indices].tolist()
```

---

## 🧩 Example Output

If you enter:

```
Inception
```

The app may return:

```
1. Interstellar  
2. The Dark Knight  
3. The Prestige  
4. Memento  
5. Tenet  
... (and more up to 500)
```

---

## 📄 License

This project is licensed under the **MIT License** – feel free to modify and share it.

---

## ❤️ Acknowledgements

- [Streamlit](https://streamlit.io) – for creating an easy way to build web apps with Python.  
- [scikit-learn](https://scikit-learn.org) – for TF-IDF and cosine similarity tools.  
- [TMDB](https://www.themoviedb.org/) – for providing open movie data.

---

**Developed with ❤️ using Python and Streamlit**
