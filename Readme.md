# Legal concept-example system

This repo contains the code and the data for the paper: "Giving Examples Instead of Answering Questions: 
Introducing Legal Concept-Example Systems".

# Data

The data is placed in the `data` directory. It contains the following files:

1. `questions.jsonl` - the questions generated for 11 concepts by ChatGPT, with the prompt:  <br/>
    For each of the following legal concepts from the GDPR, please give 4 specific and 1 general yes/no questions, which might be discussed by a court <br/>
    The file has the following structure (JSONL):
    * `id` - the id of the question,
    * `concept` - the concept which the question was generated for,
    * `question` - the question generated by ChatGPT.
2. `sentences.jsonl` - the individual sentences taken from GDPRhub decisions (articles 44-46 of GDPR) that according to the model, 
    contain an answer to the question. <br/>
    The file has the following structure:
    * `id` - the id of the question,
    * `concept` - the concept which the question was generated for,
    * `question` - the question generated by ChatGPT.
    * `sentences` - a list with the following items:
        * `score` - the score assigned by the binary model to the sentence,
        * `sentence` - the content of the sentence
3. `answers.jsonl` - answers to the questions from `questions.jsonl` generated by Flan-T5 model, using the context from `sentences.jsonl`:
    * `concept` - the concept which the question was generated for,
    * `question` - the question generated by ChatGPT,
    * `context` - the context, as 3 sentences from the decision, surrounding the sentence from `sentences.jsonl`,
    * `answer` - the answer given by the model.

4. `Analysis.docx` - the manual analysis of the obtained results.

# Code

The code of the experiment is recorded as a [Jupyter notebook](legal-concepts.ipynb)
