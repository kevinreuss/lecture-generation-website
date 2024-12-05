# Introduction to Voice Control Systems

Voice Controlled Systems (VCS) are built upon the foundations of Speech Recognition Technology and Natural Language Processing (NLP). They leverage these technologies to decode spoken words and comprehend their meaning, enabling user interaction with software applications using voice commands.

## Speech Recognition

Speech Recognition is the technology that converts spoken words into text. It uses techniques like Hidden Markov Model (HMM) and Deep Neural Networks (DNN) for acoustic modeling, and Language Modeling (LM) for understanding the context. Google's Speech-to-Text API is a popular example. Here's an example using Python:

```python
import speech_recognition as sr

def listen():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        audio = r.listen(source)
        text = r.recognize_google(audio)
    return text
```

This script listens to the microphone, captures the audio, and uses Google's Speech-to-Text API to convert it into text.

## Natural Language Processing

NLP is the technology that understands the contextual meaning of words and sentences. It uses techniques like Parsing, Semantic Analysis, and Named Entity Recognition (NER). Python's NLTK and Spacy are popular libraries for NLP.

Here's a simple example of parsing using Spacy:

```python
import spacy

def parse(text):
    nlp = spacy.load("en_core_web_sm")
    doc = nlp(text)
    return [(token.text, token.pos_) for token in doc]
```

This script loads the English language model, parses the input text, and returns a list of tuples containing words and their grammatical roles.

## Combining Speech Recognition and NLP

In a VCS, speech recognition and NLP work together. The speech recognition system converts voice commands into text, and the NLP system understands the command and performs the appropriate action. Here's a simplified example:

```python
def voice_command():
    text = listen()
    parse(text)
```

The `voice_command` function captures a voice command, converts it into text, and parses the text to understand the command. Note that the actual implementation of a VCS would involve more complex parsing and action execution based on the parsed command.