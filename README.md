
# Image Color Palette Reduction & Classification

## 📌 Overview
This project explores color palette reduction in images using unsupervised clustering algorithms (K-Means & K-Medoids) and evaluates the impact on compression and classification performance. The goal is to reduce thousands of unique colors in images to just 5-20 representative colors while preserving semantic information for distinguishing between cats and flowers.

## 🎯 Key Findings
- **Compression Gain**: 78-92% reduction in file size when reducing to 5 colors
- **Algorithm Performance**: K-Means consistently outperforms K-Medoids across all metrics
- **Classification Impact**: kNN classifier performed **better** on compressed data (F1: 0.727) than original data (F1: 0.625), suggesting color reduction acts as effective feature denoising
- **Optimal Parameters**: k=5 clusters with K-Means in HSL color space provides best balance of compression and accuracy

## 🛠️ Technologies Used
- Python 3.12
- NumPy, Pandas
- Scikit-learn (K-Means, K-Medoids, kNN, GridSearchCV)
- Matplotlib, Seaborn (visualizations)
- Pillow (image processing)

## 📁 Project Structure
```
├── Project1.ipynb          # Main Jupyter notebook with complete analysis
├── requirements.txt         # Python dependencies
├── README.md               # Project documentation
├── baza.zip                # Input images
├── reduced_images/         # Output directory for compressed images (created at runtime)
└── outputs/                # Generated CSV files with metrics
    ├── mean_clustering_metrics.csv
    └── compression_stats.csv
```

## 🔬 Methodology

### 1. Data Preparation
- Load 132 images (55 cats, 77 flowers)
- Extract RGB and HSL color spaces
- Create pixel-level and unique color DataFrames

### 2. Color Palette Reduction
- **Features**: HSL color space (Hue, Saturation, Lightness) - chosen for perceptual consistency
- **Algorithms**: K-Means vs. K-Medoids
- **Parameters**: k ∈ {5, 10, 20}, 5 random seeds per configuration
- **Evaluation**: Silhouette Score, Caliński-Harabasz Index

### 3. Compression Analysis
- Save reduced images (k=5, K-Means)
- Calculate compression gain percentage
- Regression modeling to test relationship between original colors and compression gain

### 4. Binary Classification
- kNN classifier (k optimized via GridSearchCV)
- Compare performance on original vs. compressed images
- F1 score as primary metric

## 📊 Results

| Metric | K-Means (k=5) | K-Medoids (k=5) |
|--------|---------------|-----------------|
| Silhouette Score | 0.423 | 0.360 |
| CHI | 12,960 | 10,078 |

**Classification Performance:**
- Original images: Test F1 = 0.625
- Compressed images: Test F1 = 0.727

## 🚀 Installation & Usage

### Prerequisites
```bash
pip install -r requirements.txt
```

### Running the Analysis
1. Open `Project1.ipynb` in Jupyter Notebook/Lab
2. Run cells sequentially
3. Results will be saved to:
   - `mean_clustering_metrics.csv`
   - `compression_stats.csv`
   - `reduced_images.zip`

> **Note**: The notebook expects image data from Google Drive. Modify the data loading section to use local files if needed.

## 📈 Visualizations Included
- Violin plots comparing clustering algorithms
- Scatter plots of color co-occurrence
- Histograms of unique color distributions
- Regression plots for compression analysis
- Performance comparison bar charts

## 🤔 Future Improvements
- Experiment with alternative clustering algorithms (DBSCAN, Agglomerative)
- Test different color spaces (LAB, HSV)
- Explore deep learning approaches (autoencoders for color quantization)
- Extend classification to more categories
- Implement real-time video color reduction

## 📝 License
MIT

## 👨‍💻 Author
Denys Yakovliev

## 🙏 Acknowledgments
- Course: Wstęp do uczenia maszynowego 2026
- University of Warsaw

