# **Information Retrieval - Wikipedia Search Engine**
---

The project was conductes under the course "Information Retrieval" at Ben Gurion University. The culminating project entails developing a search engine for English Wikipedia. This search engine can handle and organize over six million documents, geared towards swiftly delivering pertinent results for user inquiries across the entire Wikipedia article collection. We used fine-tuned and optimized various techniques to ensure an optimal search experience for our users.


### **The data:**
---
### Files Included:
1. `search_frontend.py` - contains the method search that will retreive the final ranked list of ('doc_id','title')
2. `QueryProcessor.py` - contains the query extension (Word2Vec), query preprocess methods for the retrieval results.
3. `Pagerank_creator.py` - contains the methods used for ranking the documents: using generating of graph with vertices and edegs.
4. `Pageview_creator.py` - contains Wikipedia pageview data from August 2021 and a dictionary of this pageviews
5. `Index_title_creator.py` - contains the inverted index of the title and all the methods for using this index in BM-25 algorithm. 
6. `Index_body_creator.py` - contains the inverted index of the body and all the methods for using this index in BM-25 algorithm. 
7. `Inverted_index_gcp.py` - contains the inverted index file and all the methods for creating an index.
8. `Buckets_body_title_bins.txt` - contains the files list from the buckets as required.

---
---
### **Retrieval Methods Used:**
---

        o Inverted Index
        o Stop Words Removal
        o Stemming
        o TF - IDF
        o Word2Vec
        o BM - 25

---
---
### **Indexes Created:**
---
        o Inverted_Index_Title
        o Inverted_Index_Body

---
---

### **Code Structure:**
---
**_Main Method_**:

        o Given a query, we calculate the score for each document in the corpus by leveraging inverted indexes of both the corpus titles
        and texts (body). Additionally, we incorporate page rank and page view data for each document. To enhance query understanding, we
        utilize a Word2Vec model. Finally, we compute the scores using the BM-25 algorithm for each index, assigning different weights
        accordingly:
            1. Similarity by title - weight of 0.4
            2. Similarity by body - weight of 0.6
            After obtaining the merged scores of the body and the title, we normalize this score by the maximum BM-25 score and multiply 
            the result by a weight of 0.5.
            To these scores, we add a weight of 0.25 for the document's page rank, which is normalized by the maximum page rank score,
            and a weight of 0.25 for the document's page views, which are normalized by the maximum page view score.

**_Functionality of major pieces_**:

        o Preprocessing and Index Initialization: We upgraded the inverted index file with key attributes like document count and average
          length. Indicators for stemming and pre-trained word embedding models were added for efficient querying.
        o Inverted Index Creation for Body and Title: Functions were implemented for preprocessing document bodies, covering tokenization
          and stop words removal. Specialized tokenization techniques were applied to title index. Indexing techniques were optimized to
          suit each section's characteristics.
        o Page Rank Creation: Page Rank scores were computed using Wikipedia link data. A directed graph was generated from wiki links,
          and resulting scores were stored for analysis.
        o Page View Creation: Wikipedia pageview data for August 2021 was processed, filtering for English pages and aggregating page
          views for each document ID. The aggregated data was stored for future use.
        o Query Processor Class Creation: The QueryProcessor class was developed to handle user queries. It preprocesses queries, expands
          them based on semantic similarity, and computes BM25 scores. The resulting ranked document list prioritizes relevance.
          Throughout each step, algorithms and techniques were iteratively optimized to enhance search accuracy and efficiency.
    

---
---
### Notes:
---
A link to our project on Google Cloud Storage - https://console.cloud.google.com/storage/browser?hl=en&project=project-ir-413718&prefix=&forceOnObjectsSortingFiltering=false&forceOnBucketsSortingFiltering=true

The external IP address of a VM: http://35.238.198.254:8080 you can access our search engine by activating it at /search?query=YOUR_QUERY. 
