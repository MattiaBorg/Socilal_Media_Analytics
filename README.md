# Chat Control: Social Media Analysis Pipeline

This pipeline analyzes the online debate regarding the European “Chat Control” proposal using Reddit data. It combines **Social Network Analysis (SNA)** to map interactions and **Social Content Analysis (SCA)** to extract sentiment and themes.

## 1. Project Structure
The workflow is divided into 4 sequential Notebooks:

1. **`Data_extraction.ipynb`**: Creation of the raw dataset via Reddit API (PRAW).
   * Targets high-impact threads with a minimum of 500 comments.
   * Filters out bots and deleted users.
   * *Output:* `Datasets/chat_control_comments.csv`

2. **`SNA.ipynb`**: Social structure mapping and community detection.
   * Constructs a Reply Graph and extracts the Giant Component.
   * Identifies clusters (Louvain vs. Greedy Modularity) and calculates metrics (Degree Centrality, Betweenness Centrality, Closeness Centrality, Network Diameter, Radius, and Assortativity).
   * *Output:* `Datasets/chat_control_sna.csv`

3. **`SCA.ipynb`**: Semantic and sentiment analysis.
   * Compares VADER (Lexicon-based) and BERT (Deep Learning) approaches for sentiment analysis.
   * Identifies dominant debate themes using BERTopic modeling.
   * Extracts semantic keywords via SBERT for community profiling.
   * *Output:* `Datasets/chat_control_FINAL.csv`

4. **`Results_Visualization.ipynb`**: Reporting and visual export.
   * Generates static charts (Matplotlib), interactive dashboards (Plotly), and Semantic WordClouds.
   * Exports the final network for visualization.
   * *Output:* Qualitative reports and `Gephi.gexf` (To explore the graph Gephi.gexf: Open Gephi, navigate to the Workspace tab, and click on Open to import the file from the root directory).

## 2. Requirements
Developed in Python (Google Colab). Key dependencies:

```bash
pip install pandas networkx numpy python-louvain
pip install praw torch transformers bertopic sentence-transformers
pip install matplotlib seaborn plotly wordcloud
