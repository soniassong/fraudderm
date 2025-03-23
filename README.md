### University of California, Berkeley
* Team Members:
    * Sonia Song
    * Katya Aukamp
    * Song Gao
    * Akshay Sharathchandra
   
### Overview
This project leverages Neo4j, a graph database, to detect potential Medicare fraud by analyzing relationships between healthcare providers, drugs, and procedures. The goal is to identify unusual patterns in billing practices that may indicate fraudulent behavior. The project uses graph-based techniques such as Community Detection, Weighted Degree Centrality, Jaccard Similarity, and PageRank to uncover suspicious activities.

### Key Features
- Community Detection: Identifies clusters of providers with similar billing patterns.
- Weighted Degree Centrality: Measures the influence of providers based on the number and value of services rendered.
- Jaccard Similarity: Detects providers with unusually high similarity in their billing practices.
- PageRank: Ranks providers based on their importance in the network.

### Dataset
The dataset used in this project is derived from Medicare claims data, which includes:
- Providers: Information about healthcare providers (e.g., NPI, name, location).
- Drugs: Details about prescribed drugs (e.g., drug code, description).
- Procedures: Information about medical procedures performed (e.g., procedure code, description).
- Services Rendered: Records of services provided, including the number of beneficiaries, total services, and total amount paid.

### Techniques and Models
1. Community Detection
Identifies groups of providers who frequently prescribe the same drugs or perform the same procedures.
Helps detect collusion or coordinated fraudulent activities.

2. Weighted Degree Centrality
Measures the influence of providers based on the total amount paid for their services.
Providers with unusually high centrality scores may be flagged for further investigation.

3. Jaccard Similarity
Compares the similarity of services rendered by different providers.
High similarity scores may indicate fraudulent billing practices.

4. PageRank
Ranks providers based on their importance in the network.
Providers with high PageRank scores may be key players in fraudulent activities.

### Code Execution
To run the project, follow these steps:

1. Community Detection
Run the following notebooks in order:

```python
code/medicare_common_practice_tables.ipynb
code/medicare_community_detection.ipynb
```

2. Weighted Degree Centrality
Run the notebook:
```python
code/postgres_neo4j_weighted_centrality_sgao.ipynb
```

3. Jaccard Similarity and PageRank
Run the following notebooks in order:

```python
code/medicare_tables_build.ipynb
code/medicare_graph.ipynb
```

Web Server Interface
The Neo4j web server interface is accessible at:
```python
https://xxxx:7473
Username: neo4j
Password: [please contact class instructor if you'd like to have access]
```

Query Example
To return all nodes and relationships, run the following query in the Neo4j web interface:
```python
MATCH (n) RETURN n
```

### Data Preparation
The data is imported into PostgreSQL and then transferred to Neo4j for graph analysis. The following tables are created and populated:
- Providers: Contains provider information.
- Drugs: Contains drug information.
- Procedures: Contains procedure information.
- Services Rendered: Links providers to drugs and procedures.

Key Queries and Analysis
1. Provider-Drug Relationships
- Identify providers who prescribe a high volume of specific drugs.
- Calculate the total amount paid for each drug.

2. Provider-Procedure Relationships
- Identify providers who perform a high volume of specific procedures.
- Calculate the total amount paid for each procedure.

3. Degree Centrality
- Measure the influence of providers based on the number of drugs prescribed or procedures performed.
- Identify providers with unusually high centrality scores.

4. Community Detection
- Detect clusters of providers who frequently prescribe the same drugs or perform the same procedures.

### Results
Key Findings:
- Providers with high Weighted Degree Centrality scores were flagged for further investigation.
- Community Detection revealed clusters of providers with similar billing patterns, some of which were suspicious.
- Jaccard Similarity identified providers with unusually high similarity in their billing practices, indicating potential fraud.

### How to Replicate the Results
1. Setup
Clone the repository:
```python
git clone https://github.com/your-username/medicare-fraud-detection.git
cd medicare-fraud-detection
```

Install the required dependencies:
```python
pip install -r requirements.txt
```

2. Data Preparation
- Download the Medicare dataset and place it in the ./data directory.
- Import the data into PostgreSQL using the provided scripts.

3. Run the Analysis
Execute the notebooks in the specified order to perform community detection, weighted degree centrality, Jaccard similarity, and PageRank analysis.

4. Visualize Results
Use the Neo4j web interface to visualize the graph and explore the results.

### Future Work
- Expand Dataset: Include additional years of Medicare data for more comprehensive analysis.
- Advanced Algorithms: Implement more advanced graph algorithms for fraud detection.
- Real-Time Monitoring: Develop a real-time monitoring system to detect fraudulent activities as they occur.

### Acknowledgments
The Medicare dataset was sourced from publicly available Medicare claims data.

This project was inspired by the need for more effective tools to detect healthcare fraud.
