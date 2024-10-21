# Machine Learning Operation (MLOps)
This project is created for testing purpose based on open source software tools.

## List of Techstacks
- Google Colabs
- MLFlow
- Python (pytest, flask, pandantic, polar)
- Docker/Kubernetes
- Grafana
- Prometeus



## Steps
- Use Google Colab (Python) to create and experiment ML projects (Loan Prediction)
    - INPUT : Dataset (csv)
    - OUTPUT: ML Model (ipython)
- Convert ML Model (ipython) to Python based and implement in MLFlow (tracking, experiment comparing, versioning, model registry, evaluating) on DEV/UAT environment
    - INPUT : Dataset (csv)
              ML Model (ipython)
    - OUTPUT: ML Model (python)
              Prediction Model
- Serving production environment with docker/kubernetes, webhook with github on GCP as web application
    - INPUT : User's Request as json to API (flask)
    - OUTPUT: prediction result
- Monitoring production predictive model (Docker, Grafana, Prometeus)
    - INPUT : prediction model
    - OUTPUT: monitoring information 

### Step 1: Create LLM Model
- Preprocess dataset
- Transformer Architecture (encoder/decoder, only decoder)
    - Output Embedded (convert word to vector)
    - Positional Encoding (Add positional information to the words e.g. different meaning in sequence)
    - Masked Multihead Attention + Add Normalization (Capture contexture information)
    - ANN Feed Forward (Adjust weight for choosing the next word)
    - Linear + Softmax (Minimization and choosen the next word as output)
    - NOTE:
        - LLM Parameters are all the weight in ANN
        - Context Window is limit of LLM that can remember input/output with each user
- Pre-Training
- RLHF (Reinforcement Learning from Human Feedback)
- Fine-Tuning domain specific data

#### Step 1.1: Preprocess dataset
- INPUT: Text Corpus
- OUTPUT: Vocabulary Vector
- PROCESS:
    - Choose dataset (e.g. some public book content)
    - BPE Tokenization
        - Tokenization: Load and splitted by punctuation
    - Word2Vec: convert word to vector to find relationship between the words in vocabularies
        - CBOW (Continuous Bag of Words): predict context (another words around) from single word
        - Skip Gram: predict middle word from context (another words around)
        - Average vector of CBOW and Skip Gram