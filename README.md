# 🎬 Movie Recommendation System

A content-based movie recommendation system built with Python, utilizing TF-IDF vectorization and cosine similarity to suggest movies similar to user preferences. The project features an interactive Streamlit web interface that displays movie details and posters fetched from the OMDb API.

## 📋 Table of Contents
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Content-Based Filtering**: Recommends movies based on genres, keywords, and plot overview
- **TF-IDF Vectorization**: Advanced text feature extraction for better recommendations
- **Interactive Web Interface**: User-friendly Streamlit application
- **Movie Details**: Fetches plot summaries and posters from OMDb API
- **Text Preprocessing**: Includes stopword removal and tokenization for improved accuracy
- **Logging**: Comprehensive logging for debugging and monitoring
- **Efficient Storage**: Pre-processed data saved using joblib for fast loading

## 📁 Project Structure

```
Movie-Recommendation-Database/
│
├── main.py                 # Streamlit web application
├── preprocess.py           # Data preprocessing and model training
├── recommend.py            # Recommendation engine
├── omdb_utils.py           # OMDb API integration
├── movies.csv              # Movie dataset
├── config.json             # Configuration file (API keys)
├── df_cleaned.pkl          # Preprocessed dataframe (generated)
├── tfidf_matrix.pkl        # TF-IDF matrix (generated)
├── cosine_sim.pkl          # Cosine similarity matrix (generated)
├── preprocess.log          # Preprocessing logs
├── recommend.log           # Recommendation logs
└── README.md               # Project documentation
```

## 🔧 Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- OMDb API key (free from [OMDb API](http://www.omdbapi.com/apikey.aspx))

## 📥 Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd Movie-Recommendation-Database-main
   ```

2. **Install required packages**:
   ```bash
   pip install pandas numpy scikit-learn nltk joblib streamlit requests
   ```

3. **Download NLTK data**:
   The preprocessing script will automatically download required NLTK data (punkt, stopwords), but you can also do it manually:
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('punkt_tab')
   nltk.download('stopwords')
   ```

## ⚙️ Configuration

1. **Create a `config.json` file** in the project root directory:
   ```json
   {
     "OMDB_API_KEY": "your_api_key_here"
   }
   ```

2. **Get your OMDb API key**:
   - Visit [OMDb API](http://www.omdbapi.com/apikey.aspx)
   - Sign up for a free API key
   - Replace `your_api_key_here` with your actual API key

3. **Prepare your dataset**:
   - Ensure `movies.csv` is in the project root directory
   - The CSV should contain columns: `genres`, `keywords`, `overview`, `title`

## 🚀 Usage

### Step 1: Preprocess the Data

Run the preprocessing script to prepare the data and generate necessary files:

```bash
python preprocess.py
```

This will:
- Load and clean the movie dataset
- Apply text preprocessing (lowercase, stopword removal, tokenization)
- Create TF-IDF vectors
- Calculate cosine similarity matrix
- Save processed data to `.pkl` files

### Step 2: Launch the Web Application

Start the Streamlit application:

```bash
streamlit run main.py
```

The application will open in your default web browser (typically at `http://localhost:8501`).

### Step 3: Get Recommendations

1. Select a movie from the dropdown menu
2. Click "🚀 Recommend Similar Movies"
3. View recommended movies with posters and plot summaries

## 🔍 How It Works

### 1. **Data Preprocessing** (`preprocess.py`)
   - Loads movie dataset from CSV
   - Combines genres, keywords, and overview into a single text field
   - Applies text cleaning:
     - Removes special characters
     - Converts to lowercase
     - Tokenizes text
     - Removes stopwords
   - Creates TF-IDF (Term Frequency-Inverse Document Frequency) vectors
   - Computes cosine similarity between all movies

### 2. **Recommendation Engine** (`recommend.py`)
   - Loads pre-processed data from pickle files
   - Finds the input movie in the dataset
   - Retrieves movies with highest cosine similarity scores
   - Returns top N recommendations (default: 5)

### 3. **OMDb Integration** (`omdb_utils.py`)
   - Fetches movie details from OMDb API
   - Retrieves plot summaries and poster images
   - Handles API errors gracefully

### 4. **Web Interface** (`main.py`)
   - Streamlit-based interactive UI
   - Dropdown for movie selection
   - Displays recommendations with images and descriptions
   - Responsive layout with columns for better presentation

## 🛠️ Technologies Used

- **Python**: Core programming language
- **Pandas**: Data manipulation and analysis
- **Scikit-learn**: Machine learning (TF-IDF, cosine similarity)
- **NLTK**: Natural language processing (tokenization, stopwords)
- **Streamlit**: Web application framework
- **Requests**: HTTP library for API calls
- **Joblib**: Efficient serialization of Python objects
- **OMDb API**: Movie information and posters

## 📊 Algorithm Details

### TF-IDF (Term Frequency-Inverse Document Frequency)
- Measures importance of words in documents
- High weight for terms frequent in a document but rare across all documents
- Max features: 5000

### Cosine Similarity
- Measures similarity between two vectors
- Range: 0 (completely different) to 1 (identical)
- Formula: `similarity = (A · B) / (||A|| × ||B||)`

## 🐛 Troubleshooting

**Issue**: Movies not found in dataset
- **Solution**: Ensure the movie name matches exactly (case-insensitive)

**Issue**: OMDb API returns "N/A"
- **Solution**: Check your API key in `config.json` and verify internet connection

**Issue**: Missing `.pkl` files
- **Solution**: Run `python preprocess.py` before starting the app

**Issue**: Import errors
- **Solution**: Install all dependencies: `pip install -r requirements.txt` (create requirements.txt if needed)

## 📝 Future Enhancements

- [ ] Add collaborative filtering
- [ ] Implement hybrid recommendation system
- [ ] Add user ratings and feedback
- [ ] Include movie trailers
- [ ] Add filtering by genre, year, rating
- [ ] Improve UI/UX with custom CSS
- [ ] Deploy to cloud platform (Heroku, AWS, etc.)
- [ ] Add caching for API calls
- [ ] Implement search functionality

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

Created with ❤️ by Sandesh

## 🙏 Acknowledgments

- [OMDb API](http://www.omdbapi.com/) for providing movie data
- [Streamlit](https://streamlit.io/) for the amazing web framework
- [NLTK](https://www.nltk.org/) for natural language processing tools
- The open-source community for inspiration and resources

---

**Happy Movie Watching! 🍿**
