** Financial Chatbot
A deep learning-powered chatbot designed to answer financial questions using a hybrid model architecture.

** Overview
This project implements a sophisticated chatbot that can handle two distinct types of user queries:

Dictionary/Keyword Questions: Simple requests for the definition of a financial term (e.g., "What is inflation?").

General/Knowledge Questions: More complex, conversational queries that require a generated response (e.g., "How can I start investing in stocks?").

To achieve this, the chatbot uses a two-stage hybrid model:

Intent Classifier (Bidirectional LSTM): First, a Bidirectional LSTM model classifies the user's input to determine if it's a "dictionary" question or a "general" question.

Response Generator (Sequence-to-Sequence): Based on the classification, the system either retrieves a predefined definition or uses a generative Seq2Seq model to create a novel answer.


** How It Works: Architecture
When a user inputs a question, it goes through the following pipeline:

Classification:

The input is tokenized using the lstm_tokenizer.

It's fed into the bidirectional_LSTM.h5 model, which outputs a score.

Branching Logic:

If score > 0.5 (Dictionary Query):

The system identifies the query as a request for a definition.

It searches the keyword_dict.pkl for a matching financial term.

It returns the predefined definition associated with that term.

If score <= 0.5 (Generative Query):

The system identifies the query as a general, knowledge-based question.

The input is tokenized using the seq2seq_tokenizer (Final_Tokenizer).

It's processed by the chatbot.h5 (Sequence-to-Sequence) model, which generates an answer token-by-token.

The final generated sentence is cleaned and returned to the user.

** Project Structure

<img width="690" height="639" alt="image" src="https://github.com/user-attachments/assets/6f6d997b-b951-4718-968c-a2612de2d256" />


** Technologies Used
Python 3
TensorFlow & Keras: For building and serving both the LSTM and Seq2Seq models.
TensorFlow Datasets: For SubwordTextEncoder tokenization.
NumPy: For numerical operations and sequence padding.
Pickle: For loading the keyword dictionary.
