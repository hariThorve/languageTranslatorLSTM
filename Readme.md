# 🌐 Language Translation using LSTM Encoder-Decoder 🚀


Welcome! 👋 This project shows how to build a neural machine translation system that translates English sentences to Marathi using TensorFlow and Keras. At its heart is the classic **Encoder-Decoder** architecture with LSTM layers—a go-to approach for sequence-to-sequence (seq2seq) tasks like language translation. 🧠💬


## 🏗️ Encoder-Decoder Architecture Overview


### 🔵 Encoder
The **encoder** takes your input English sentence and squashes all its info into a fixed-length context vector (the final hidden and cell states of the LSTM). Think of it as the brain that remembers everything about your sentence and passes it to the decoder! 🧳

- **Input:** Tokenized and padded English sentence.
- **Layers:**
  - 🧩 Embedding layer: Converts word indices to dense vectors.
  - 🔄 LSTM layer: Processes the sequence and outputs the final hidden and cell states.
- **Output:** Encoder states (hidden and cell states).


### 🟣 Decoder
The **decoder** is like a language artist—it takes the context vector from the encoder and generates the Marathi translation, one word at a time! 🎨📝

- **Input:**
  - Previous word in the target sequence (starting with a special `<start>` token).
  - Encoder states (context vector).
- **Layers:**
  - 🧩 Embedding layer: Converts word indices to dense vectors.
  - 🔄 LSTM layer: Generates the next hidden and cell states.
  - 🎯 Dense layer: Outputs a probability distribution over the target vocabulary.
- **Output:** Predicted next word and updated decoder states.


## 🛠️ Implementation in `LanguageTranslationLSTM.ipynb`


### 📋 Data Preparation
- The dataset consists of English-Marathi sentence pairs.
- Sentences are preprocessed (lowercased, punctuation and digits removed, special tokens added). ✂️
- Tokenizers are created for both languages, and sequences are padded to uniform lengths. 🧮


### 🏗️ Model Construction
- **Encoder:**
  - Input layer for English sequences.
  - Embedding and LSTM layers.
  - Outputs the final hidden and cell states.
- **Decoder:**
  - Input layer for Marathi sequences.
  - Embedding and LSTM layers (initialized with encoder states).
  - Dense layer with softmax activation for word prediction.
- The model is compiled with `sparse_categorical_crossentropy` loss and trained on the sentence pairs. 🏋️‍♂️


### 🔍 Inference Models
- **Encoder Inference Model:**
  - Takes an English sentence and outputs the encoder's final states.
- **Decoder Inference Model:**
  - Takes the previous Marathi word and the encoder states, and outputs the next word and updated states.


### 🌈 Translation Function
- The `translate_sentence` function:
  1. Preprocesses and tokenizes the input English sentence. 🧹
  2. Uses the encoder model to get initial states. 🧠
  3. Iteratively feeds the decoder with the previous word and states to generate the Marathi translation, until the `<end>` token is produced or the maximum length is reached. 🔁


### 💡 Example Usage
The notebook demonstrates translation of sample English sentences to Marathi using the trained model and the `translate_sentence` function. Try it out with your own sentences! ✨


## 📝 Key Takeaways
- The encoder-decoder LSTM architecture is effective for sequence-to-sequence tasks like language translation. 🌍
- The encoder compresses the input sequence into a context vector, and the decoder generates the output sequence step by step. 🏃‍♂️➡️🏃‍♀️
- The implementation in the notebook follows best practices for preprocessing, model construction, and inference. 👍


## 🔮 Next Steps
- Evaluate translation quality on a larger test set. 📊
- Consider enhancements such as attention mechanisms for improved performance on longer or more complex sentences. 🧲

---


---

**References:**
- [Sequence to Sequence Learning with Neural Networks (Sutskever et al., 2014)](https://arxiv.org/abs/1409.3215)
- [TensorFlow Keras Documentation](https://www.tensorflow.org/guide/keras)

---

_Made with ❤️ for language lovers and ML enthusiasts!_
