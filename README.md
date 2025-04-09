# RAG Bootcamp

This is a collection of reference implementations for Vector Institute's **RAG (Retrieval-Augmented Generation) Bootcamp**, scheduled to take place from Nov 2024 to Jan 2025. It demonstrates some of the common methodologies used in RAG workflows (data ingestion, chunks, embeddings, vector databases, sparse/dense retrieval, reranking) using the popular Python [LangChain](https://python.langchain.com/docs/get_started/introduction) and [LlamaIndex](https://docs.llamaindex.ai/en/stable/) libraries.

## Reference Implementations

This repository includes several reference implementations showing different approaches and methodologies related to Retrieval-Augmented Generation.

- [**Web Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/web_search): Popular LLMs like OpenAI's GPT-4o and Meta's Llama-3 are very good at processing natural language, but their knowledge is limited by the data they were trained on. As of November 2024, neither service can correctly answer the question "Who won the 2024 World Series of Baseball?"
- [**Document Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/document_search): Use a collection of unstructured documents to answer domain-specific questions, like: "How many AI scholarships did Vector Institute award in 2022?"
- [**SQL Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/sql_search): Answer natural language questions with information from structured relational data. This demo uses a financial dataset from a Portugese banking instituation, [available on Kaggle](https://www.kaggle.com/datasets/prakharrathi25/banking-dataset-marketing-targets)
- [**Cloud Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/cloud_search): Retrieve information from data in a cloud service, in this example AWS S3 storage
- [**PubMed QA**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/pubmed_qa): A full pipeline on the [PubMed](https://pubmed.ncbi.nlm.nih.gov/download/) dataset demonstrating ingestion, embeddings, vector index/storage, retrieval, reranking, with a focus on evaluation metrics.
- [**RAG Evaluation**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/rag_evaluation): RAG evaluation techniques based on the [Ragas](https://github.com/explodinggradients/ragas) framework. Focuses on evaluation "test sets" and how to use these to determine how well a RAG pipeline is actually working.

## Requirements

* Python 3.10+

## Git Repostory

Start by cloning this git repository to a local folder:

```
git clone https://github.com/VectorInstitute/rag-bootcamp
```

## [Optional] Build the virtual Python environments

**These instructions only apply if you are not running this code on the Vector Institute cluster.** If you are are working on the Vector cluster, these environments are already pre-compiled and ready to use in the `/ssd003/projects/aieng/public/rag_bootcamp/envs` folder.

The notebooks contained in this repository depend on several different Python environments. Following table lists the environment for each notebook:

| Notebooks  | Environment  |
| ---------------------  | -------------------  |
| [**Web Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/web_search), [**Document Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/document_search), [**SQL Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/sql_search), [**Cloud Search**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/cloud_search)  | ```rag_dataloaders```  |
| [**RAG Evaluation**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/rag_evaluation)  | ```rag_evaluation```  |
| [**PubMed QA**](https://github.com/VectorInstitute/rag_bootcamp/tree/main/pubmed_qa)  | ```rag_pubmed_qa```  |

Build these environments using the following instructions: 

```
python3 --version # Make sure this shows Python 3.10+!

# Install the dataloaders environment
python3 -m venv ./rag_dataloaders
source rag_dataloaders/bin/activate
python3 -m pip install -r ./envs/rag_dataloaders/requirements.txt
deactivate

# Install the evaluation environment
python3 -m venv ./rag_evaluation
source rag_evaluation/bin/activate
python3 -m pip install -r ./envs/rag_evaluation/requirements.txt
deactivate

# Install the pubmed_qa environment
python3 -m venv ./rag_pubmed_qa
source rag_pubmed_qa/bin/activate
python3 -m pip install -r ./envs/rag_pubmed_qa/requirements.txt
deactivate
```

## Add the Jupyter notebook kernels

These kernels are required for the notebooks in this repository. You can make them available to Jupyter with the following instructions:

```
# The following path is for use on the Vector cluster. If you are using a different environment, update this accordingly.
export RAG_BOOTCAMP_ENV="/ssd003/projects/aieng/public/rag_bootcamp/envs"

source $RAG_BOOTCAMP_ENV/rag_dataloaders/bin/activate
ipython kernel install --user --name=rag_dataloaders
deactivate

source $RAG_BOOTCAMP_ENV/rag_evaluation/bin/activate
ipython kernel install --user --name=rag_evaluation
deactivate

source $RAG_BOOTCAMP_ENV/rag_pubmed_qa/bin/activate
ipython kernel install --user --name=rag_pubmed_qa
deactivate
```

## Lastly, start a Jupyter notebook

```
# The following path is for use on the Vector cluster. If you are using a different environment, update this accordingly.
export RAG_BOOTCAMP_ENV="/ssd003/projects/aieng/public/rag_bootcamp/envs"

source $RAG_BOOTCAMP_ENV/<env_to_be_used>/bin/activate
jupyter notebook --ip $(hostname --fqdn)
```
