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

### Here's a simplified overview of how GPT works (Transformer Neural Network)

- Tokenization: The input text is broken down into smaller units, typically subwords or characters. This is often done using techniques like Byte Pair Encoding (BPE).
- Embedding: Each token is mapped to a dense vector representation, known as an embedding. These embeddings capture the semantic meaning of the tokens.
- Positional Encoding: Information about the position of each token in the sequence is added to the embeddings. This helps the model understand the context and relationships between words.
- Multi-Head-Attention (Self Attension): The transformer architecture uses self-attention to allow each token to interact with all other tokens in the sequence. This helps the model capture long-range dependencies and understand the context of each token.
- Feed-Forward Neural Network: A feed-forward neural network is applied to each position in the sequence, further processing the information.
- add norm, dropout 
- Decoder Output: The decoder generates the output sequence, token by token. The probability distribution over all possible tokens is calculated at each step, and the token with the highest probability is chosen.
**Added & Norm**
**Linear**
**Output Decoder**

- Encoder-Decoder Architecture: GPT uses an encoder-decoder architecture. The encoder processes the input sequence, and the decoder generates the output sequence.


1. Data Collection and Preprocessing:
    Massive Dataset: LLMs are trained on massive amounts of text data from the internet, books, articles, code, and more.
    Data Cleaning: The data is cleaned to remove noise, inconsistencies, and biases.
    Tokenization: The text is broken down into smaller units called tokens, which can be words, subwords, or characters.
2. Model Architecture:
    Transformer Architecture: Most modern LLMs are based on the transformer architecture, which is particularly well-suited for processing sequential data.
    Encoder-Decoder Structure: This architecture consists of an encoder that processes the input sequence and a decoder that generates the output sequence.
    Self-Attention Mechanism: This key component allows the model to weigh the importance of different parts of the input sequence.
3. Training Process:
    Parameter Initialization: The model's parameters (weights and biases) are initialized randomly.
    Forward Pass:
    The input sequence is fed into the encoder, which processes it through multiple layers of self-attention and feed-forward neural networks.
    The output of the encoder is passed to the decoder, which generates the output sequence token by token.
    Loss Calculation: The generated output is compared to the ground truth (correct output), and a loss function is used to measure the difference.
    Backpropagation: The error is propagated back through the network to update the model's parameters using gradient descent.
    Iterative Training: This process is repeated multiple times on different batches of data until the model converges.
4. Model Inference:
    Input: A new input sequence is fed into the trained model.
    Forward Pass: The model processes the input sequence through its layers and generates an output sequence.
    Output: The generated output is decoded into human-readable text.
5. Fine-Tuning:
    Specific Task Adaptation: For specific tasks like question-answering or code generation, the pre-trained LLM can be fine-tuned on a smaller, task-specific dataset.
    Parameter Adjustment: The model's parameters are adjusted to better fit the specific task.

Data Processing
- Corpus: Dataset as long sequence of text

#### Step 1.1: Preprocess dataset
- INPUT: Text Corpus
- OUTPUT: Vocabulary Vector
- PROCESS:
    - Choose dataset (e.g. some public book content)
    - BPE Tokenization: build a vocab list (will use pre-trained)
    - Word2Vec: convert word to vector to find relationship between the words in vocabularies (choose 1 or both then average)
        - CBOW (Continuous Bag of Words): predict context (another words around) from single word
        - Skip Gram: predict middle word from context (another words around)