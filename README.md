<H3>ENTER YOUR NAME : NARENDHIRAN P</H3>
<H3>ENTER YOUR REGISTER NO : 212224230177</H3>
<H3>EX. NO.9</H3>
<H3>DATE: 06/09/2026</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: to perform automatic text summarization using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>

```PY
pip install nltk


import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('punkt_tab')


import string

def preprocess_text(text):
    # Tokenize the text into words
    words = word_tokenize(text.lower())

    # Remove stopwords and punctuation
    stop_words = set(stopwords.words('english'))
    words = [w for w in words if w not in stop_words and w not in string.punctuation]

    # Stemming
    ps = PorterStemmer()
    stemmed_words = [ps.stem(w) for w in words]

    return stemmed_words


def generate_summary(text, num_sentences=3):
    sentences = sent_tokenize(text)
    preprocessed_text = preprocess_text(text)

    # Calculate the frequency of each word
    word_freq = {}
    for word in preprocessed_text:
        word_freq[word] = word_freq.get(word, 0) + 1

    # Calculate the score for each sentence based on word frequency
    sentence_scores = {}
    ps = PorterStemmer()
    for sentence in sentences:
        for word in word_tokenize(sentence.lower()):
            stemmed = ps.stem(word)
            if stemmed in word_freq:
                sentence_scores[sentence] = sentence_scores.get(sentence, 0) + word_freq[stemmed]

    # Select top N sentences with highest scores
    summary_sentences = sorted(sentence_scores, key=sentence_scores.get, reverse=True)[:num_sentences]

    return ' '.join(summary_sentences)


if __name__ == "__main__":
    input_text = input()
    summary = generate_summary(input_text)
    print("Original Text:")
    print(input_text)
    print("\nSummary:")
    print(summary)

```

<H3>Output</H3>

```
Original Text:
Natural language processing is a field of artificial intelligence. It focuses on the interaction between computers and humans through natural language. The ultimate objective of NLP is to read, decipher, understand, and make sense of human languages in a valuable way. Most NLP techniques rely on machine learning to derive meaning from human languages. Text summarization is one of the important applications of NLP. It helps in creating a short and coherent summary of a longer text document.

Summary:
The ultimate objective of NLP is to read, decipher, understand, and make sense of human languages in a valuable way. Most NLP techniques rely on machine learning to derive meaning from human languages. It focuses on the interaction between computers and humans through natural language.
```

<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


