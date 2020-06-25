[![View matlab_word2vec_binary_reader on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/77272-matlab_word2vec_binary_reader)
# readW2Vbin


Reads a pre-trained word2vec word embedding model in the binary format. Note that it shows a progress bar during reading the data.

# Environment

MATLAB R2019b

Text Analytics Toolbox Required.


# Syntax


`emb = readW2Vbin(filename [,encoding])`


# Description


Use `readW2Vbin` to read a pre-trained word2vec word embedding model in the binary format. It assumes that the file is written in the following format.



   -  The data before the first `0x20` (space) are ascii characters representing the number of vocabularies of the model , while the data between the first `0x20` and the first `0x10` (newline) represent the dimension of the word vector.  (e.g.,`[ 51 48 48 48 48 48 48 32 51 48 48 10] ` means 3 milion words embedded into 300 dimensions. ) 
   -  The main body, which consists of sequence of word-vector pairs, begins right after the newline character. One word-vector pair consists of a sequence of bytes that represents a word, space (0x20), and a sequence of binary data that represents the embedded vector corresponding to the word in single precision (32bit) format.  The length of the vector data is 4bytes times number of dimensions (e.g., 1200 bytes for 300 dimension). 

# Input Arguments


`filename `- Name of the pre-trained word2vec model file in the binary format, specified as a string scalar or character vector.

`encoding `- Character encoding of the "word" in the binary file, specified as a string scalar or charcter vector. The default value is 'UTF-8'.

# Output Arguments


emb - Word embedding, returned as a `wordEmbedding` object.


## Note: 


This function was tested with the "GoogleNews-vectors-negative300.bin" from the  word2vec web ([https://code.google.com/archive/p/word2vec/](https://code.google.com/archive/p/word2vec/)). It took about a minute to read the 3.5GB file.


