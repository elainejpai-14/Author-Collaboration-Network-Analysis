# Author Collaboration Network Analysis

This repository contains a Jupyter Notebook (`Author_Collaboration_Network_Analysis.ipynb`) that performs an analysis of author collaboration networks using a dataset of arXiv papers. The project aims to visualize and understand the collaboration patterns among authors in the academic domain.

## Project Overview

The core of this project involves:
1.  **Data Loading and Preprocessing**: Loading a large JSON dataset of arXiv papers and extracting relevant information such as author lists, titles, categories, and update dates.
2.  **Co-Author Network Construction**: Building a graph where nodes represent authors and edges represent co-authorship on a paper. This involves careful parsing and cleaning of author strings to ensure accurate edge creation.
3.  **Graph Analysis**: Utilizing the `networkx` library to analyze the constructed collaboration graph, including calculating basic graph properties (number of nodes, edges) and centrality measures (e.g., degree centrality).
4.  **Visualization**: Generating visualizations, such as degree distribution plots, to illustrate the network's characteristics.

## Dataset

The analysis uses the `arxiv-metadata-oai-snapshot.json` dataset, which can be downloaded via `kagglehub`. This dataset contains metadata for a vast collection of arXiv papers.

**Dataset Source**: [Cornell-University/arxiv](https://www.kaggle.com/datasets/Cornell-University/arxiv) (Accessed via KaggleHub)

## Setup and Installation

To run this notebook, you'll need to have Python installed along with the following libraries. It's recommended to use a virtual environment.

1.  **Clone the repository**:
    ```bash
    git clone [https://github.com/elainejpai-14/Author-Collaboration-Network-Analysis.git](https://github.com/elainejpai-14/Author-Collaboration-Network-Analysis.git)
    cd Author-Collaboration-Network-Analysis
    ```

2.  **Create and activate a virtual environment (optional but recommended)**:
    ```bash
    python -m venv venv
    # On Windows
    .\venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install the required Python packages**:
    ```bash
    pip install pandas networkx matplotlib kagglehub
    ```

    * `pandas`: For data manipulation and analysis.
    * `networkx`: For creating, manipulating, and studying the structure, dynamics, and functions of complex networks.
    * `matplotlib`: For creating static, animated, and interactive visualizations in Python.
    * `kagglehub`: To easily download the arXiv dataset.

## Usage

1.  **Download the dataset**: The notebook automatically handles the download of the `arxiv` dataset using `kagglehub`. Ensure you have `kagglehub` installed and configured if running outside a Kaggle environment.

2.  **Run the Jupyter Notebook**:
    ```bash
    jupyter notebook Author_Collaboration_Network_Analysis.ipynb
    ```
    This will open the notebook in your web browser. You can then run the cells sequentially to perform the analysis.

## Notebook Structure

The notebook is organized into the following steps:

* **Step 1: Load Dataset**: Downloads the arXiv metadata dataset.
* **Step 2: Import Libraries**: Imports necessary Python libraries (`json`, `pandas`, `itertools`, `networkx`, `re`, `matplotlib.pyplot`).
* **Step 3: Load JSON and Convert to DataFrame**: Reads the JSON data from the downloaded file and converts it into a pandas DataFrame.
* **Step 4: Build the Co-Author Network**:
    * **Generate Edge List**: Parses the 'authors' string for each paper, cleans author names (removes stopwords, single characters, digits, special characters, and filters for specific name formats), and generates pairs of co-authors to form an edge list, which is saved to `edges.txt`.
    * Reads the generated `edges.txt` file to create a list of tuples representing the edges in the graph.
* **Step 5: Create and Analyze the Graph**:
    * **NetworkX**: Initializes a `networkx` graph and adds the edges. Prints the total number of nodes and edges.
    * **Node Cleaning**: Removes "bad" nodes (e.g., stopwords, single characters, or specific patterns) from the graph to refine the network.
    * **Centrality Analysis**: Calculates the degree centrality for all nodes in the graph and identifies the top 10 authors with the highest degree centrality.
* **Step 6: Visualizations**:
    * **Degree Distribution**: Generates a histogram of the degree distribution of the network, plotted on a log-log scale, to show the frequency of authors with a certain number of co-authors.

## Results

The notebook will output:
* The path to the downloaded dataset.
* The total number of nodes and edges in the constructed collaboration graph.
* A list of the top 10 authors by degree centrality, indicating who has the most direct collaborations.
* A plot showing the degree distribution of the network, which typically follows a power-law distribution in real-world networks.

## Future Enhancements

* Implement other centrality measures (e.g., betweenness centrality, closeness centrality, eigenvector centrality) to gain deeper insights into author influence and connectivity.
* Explore community detection algorithms to identify research clusters or groups of highly collaborative authors.
* Visualize smaller sub-graphs or ego-networks for specific authors to understand their immediate collaboration circles.
* Analyze temporal aspects of collaboration by considering the `update_date` of papers.
* Integrate interactive visualizations using libraries like `Plotly` or `Bokeh`.

## Contributing

Contributions are welcome! If you have suggestions for improvements or new features, please open an issue or submit a pull request.
