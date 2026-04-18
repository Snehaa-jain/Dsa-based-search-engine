# DSA Based Search Engine

A fast and intelligent search engine for 3500+ Data Structures and Algorithms problems across **LeetCode**, **Codeforces**, and **CodeChef** — all in one place.

---

## 📌 Project Description

Finding the right DSA problem to practice can be time-consuming when you have to search across multiple platforms. This project solves that by aggregating problems from LeetCode, Codeforces, and CodeChef into a single searchable corpus.

You can search by problem name, topic, or tag and get ranked results instantly using a TF-IDF based search algorithm with cosine similarity scoring.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Node.js, Express.js |
| Search Algorithm | TF-IDF + Cosine Similarity (`natural` library) |
| Web Scraping | Puppeteer |
| Frontend | HTML, CSS, Vanilla JavaScript |
| Data Storage | JSON files |

---

## ⚙️ How to Run

### Prerequisites
- Node.js v18 or higher
- npm

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/Snehaa-jain/Dsa-based-search-engine.git
cd Dsa-based-search-engine
```

**2. Install dependencies**
```bash
npm install
```

**3. Start the server**
```bash
node index.js
```

**4. Open in browser**
```
http://localhost:3000
```

### Optional — Re-scrape problems
```bash
npm run scrape
npm run merge
```
> Note: Scraping requires a stable internet connection and may take a few minutes.

---

## 🔍 How It Works (TF-IDF)

**TF-IDF** stands for **Term Frequency–Inverse Document Frequency**. It is a technique used to measure how relevant a word is to a document in a collection.

### Term Frequency (TF)
Measures how often a term appears in a document. A word that appears more frequently in a problem's title or description gets a higher score.

```
TF = (Number of times term appears in document) / (Total terms in document)
```

### Inverse Document Frequency (IDF)
Penalizes terms that appear in too many documents (like common words). Rare terms that appear in fewer problems are considered more meaningful.

```
IDF = log(Total documents / Number of documents containing the term)
```

### Cosine Similarity
After computing TF-IDF vectors for both the search query and each problem, the engine calculates the **cosine similarity** between them to rank results. A higher cosine similarity means a better match.

### Title Boosting
Problem titles are duplicated during indexing to give them more weight than descriptions, ensuring title matches rank higher in results.

---

## 📁 Project Structure

```
├── assets/
│   └── logos/          # Platform logos
├── corpus/
│   └── all_problems.json   # Merged problem dataset
├── problems/
│   ├── leetcode_problems.json
│   └── codeforces_problems.json
├── utils/
│   ├── preprocess.js   # Text cleaning and stopword removal
│   └── merge.js        # Merges scraped data into one corpus
├── index.js            # Express server + search logic
├── script.js           # Frontend search handler
├── scrape.js           # Puppeteer web scraper
├── index.html          # Main UI
└── styles.css          # Styling
```
