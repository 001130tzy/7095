# README: Movie Recommendation System Using TMDB Data

## Artifact Identification

**Report Title**: Movie Recommendation System Using TMDB Data  
**Group Number**: 5  
**Students**:  
- He Yiyang, ID: 24435988, Email: 24435988@life.hkbu.edu.hk  
- Lin Junjian, ID: 24450715, Email: 24450715@life.hkbu.edu.hk  
- Song Wenqi, ID: 24439231, Email: 24439231@life.hkbu.edu.hk  
- Li Yankun, ID: 24444197, Email: 24444197@life.hkbu.edu.hk  
- Tang Ziyan, ID: 24466646, Email: 24466646@life.hkbu.edu.hk  

**Abstract**:  
This project develops a two-stage hybrid movie recommendation system using the TMDB dataset, which provides rich metadata on global movies. The system integrates content similarity recall (via KNN and cosine similarity) with multi-dimensional dynamic filtering (using Euclidean distance, TF-IDF, and weighted scoring) to deliver relevant recommendations while tackling cold start and popularity bias. Leveraging Big Data tools like HDFS for storage, Spark for data processing, and Matplotlib for visualization, the artifact enables full reproducibility of the experiments detailed in the report. The software architecture consists of a data pipeline (storage and cleaning), a recommendation engine (recall and filtering), and a visualization module. The artifact includes scripts and datasets to regenerate the precision, recall, diversity, and novelty metrics, as well as figures (e.g., histograms and plots) matching those in the report, ensuring experimental reproducibility.

## Artifact Dependencies and Requirements

- **Hardware Resources**:  
  - Minimum: 4-core CPU, 8GB RAM, 50GB storage  
  - Recommended: 8-core CPU, 16GB RAM, 100GB storage (for HDFS and Spark efficiency)  

- **Operating Systems**:  
  - Tested on Ubuntu 20.04 LTS; compatible with any OS supporting Hadoop and Python  

- **Software Libraries**:  
  - Python 3.9  
  - PySpark 3.2.0 (with Hadoop 3.2 compatibility)  
  - NumPy 1.21  
  - Pandas 1.4  
  - scikit-learn 1.0 (for KNN and similarity calculations)  
  - Matplotlib 3.5 (for visualization)  
  - Optional: Tableau or Power BI (for enhanced visualization, not required for core execution)  

- **Input Dataset**:  
  - TMDB dataset: `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` (included in the artifact under `data/` directory)  
  - Size: ~25MB uncompressed; processed data grows to ~100MB after cleaning  

- **Other Dependencies**:  
  - Hadoop 3.2+ (for HDFS)  
  - Java 8 (required by Hadoop and Spark)  

## Artifact Installation and Deployment Process

### Installation and Compilation
1. **Install Java and Hadoop**:  
   - Install Java 8: `sudo apt install openjdk-8-jdk` (Ubuntu)  
   - Download and configure Hadoop 3.2+: Follow [Hadoop setup guide](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/SingleCluster.html)  
   - Estimated time: ~15-20 minutes  
2. **Install Python and Dependencies**:  
   - Install Python 3.9: `sudo apt install python3.9`  
   - Install PySpark and libraries:  
     ```bash
     pip install pyspark==3.2.0 numpy==1.21 pandas==1.4 scikit-learn==1.0 matplotlib==3.5
     Estimated time: ~10-15 minutes
3.**Verify Setup**:
-Check Hadoop: hadoop version
-Check Spark: pyspark --version
-Deployment
-Start HDFS:
-Format namenode (first time only): hdfs namenode -format
-Start HDFS: start-dfs.sh
-Estimated time: ~2-5 minutes
-Upload Data:
-Copy datasets to HDFS:
-bash

-Collapse

-Wrap

-Copy
-hdfs dfs -put data/tmdb_5000_movies.csv /input/
-hdfs dfs -put data/tmdb_5000_credits.csv /input/
-Run the Pipeline:
-Execute the main script:
-bash

-Collapse

-Wrap

-Copy
-spark-submit main.py
-Estimated time: ~5 minutes (initialization and data loading)
-Reproducibility of Experiments
4.**Experiment Workflow**
-Data Storage and Cleaning:
-Uploads tmdb_5000_movies.csv and tmdb_5000_credits.csv to HDFS.
-Cleans data using clean_data.py with PySpark: extracts genres, keywords, actors, and directors; removes nulls and duplicates.
-Recommendation Computation:
-Runs recommend.py:
-Recall Stage: Uses KNN with Euclidean distance to generate a 40-movie candidate set.
-Filtering Stage: Applies Gaussian year weights, rating weights, and popularity weights to select the top 5 recommendations.
5.**Visualization**:
-Executes visualize.py to generate metric plots and tables using Matplotlib.
-Execution Time
-Full workflow: ~30-40 minutes on recommended hardware
-Data cleaning: ~10-15 minutes
-Recommendation computation: ~15-20 minutes
-Visualization: ~5 minutes
-Expected Results and Evaluation
6.**Outputs**:
-Cleaned dataset: output/cleaned_data.csv
-Recommendation list: output/recommendations.csv (top 5 movies with scores)
-Figures:
output/accuracy_plot.png (Precision and Recall histogram)
output/diversity_plot.png (Genre and Director entropy bar chart)
output/novelty_plot.png (Novelty percentile histogram)
7.**Evaluation**:
Precision: ~0.76, Recall: ~0.03 (Hybrid Model, see Table 2)
Genre Entropy: ~2.29, Director Entropy: ~2.20 (see Table 3)
Novelty: ~32.64 (see Table 4)
Results may vary slightly due to random sampling in KNN.
8.**Relation to Report Results**
The artifact regenerates the results in Section 3.2.3 of the report:
recommendations.csv matches the top-5 list format in the report.
accuracy_plot.png replicates Figure 6 (histogram of Precision and Recall).
diversity_plot.png matches Figure 7 (bar chart of entropy).
novelty_plot.png corresponds to Figure 8 (novelty histogram).
Matplotlib ensures figures are in the same format as the report, enabling direct comparison of reproducibility scope.
