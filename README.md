# DNA-Sequenced
This is an implementation of ULMFiT for genomics classification using Pytorch and Fastai. The model architecture used is based on the AWD-LSTM model, consisting of an embedding, three LSTM layers, and a final set of linear layers.

The ULMFiT approach uses three training phases to produce a classification model:

Train a language model on a large, unlabeled corpus
Fine tune the language model on the classification corpus
Use the fine tuned language model to initialize a classification model
This method is particularly advantageous for genomic data, where large amounts of unlabeled data is abundant and labeled data is scarce. The ULMFiT approach allows us to train a model on a large, unlabeled genomic corpus in an unsupervised fashion. The pre-trained language model serves as a feature extractor for parsing genomic data.

Typical deep learning approaches to genomics classification are highly restricted to whatever labeled data is available. Models are usually trained from scratch on small datasets, leading to problems with overfitting. When unsupervised pre-training is used, it is typically done only on the classification dataset or on synthetically generated data. The Genomic-ULMFiT approach uses genome scale corpuses for pre-training to produce better feature extractors than we would get by training only on the classification corpus.
These notebooks detail data preparation and training for language models based on the human genome. These models form the foundations for the classification models trained in the other directories. The language model architecture is based on the AWD-LSTM.

Genomic data is broken into tokens using a k-mer approach with a set stride between k-mers. For tokenization with k-mer length k and stride s, the input genomic sequences are broken into chunks of length k base pairs with a shift of s base pairs between k-mers.

LM 0 details processing the human genome into a form we can feed into a model.

LM 1 trains a model with k-mer length 4 and stride 2.

LM 2 trains a model with k-mer length 5 and stride 2.

LM 3 trains a model with k-mer length 8 and stride 3.

LM 4 trains a model with k-mer length 5 and stride 1

LM 5 trains a model with k-mer length 3 and stride 1

LM 6 trains a model with k-mer length 1 and stride 1


**lnc RNA**


These notebooks look at training a classification model to distinguish between human coding mRNA sequences and long noncoding RNA (lncRNA) sequences following the Genomic ULMFiT approach. This dataset comes from the paper A deep recurrent neural network discovers complex biological rules to decipher RNA protein-coding potential by Hill et al. and is available for download here.

The dataset contains two test sets - a standard test set of 1000 sequences and a challenge test set 1000 sequences. The regular test set contains standard mRNA and lncRNA sequences. The challenge test set contains mRNA sequences with short CDSs and lncRNAs with long untranslated ORFs.

lncRNA 0 shows the data processing steps

lncRNA 1 shows training the classification model using Genomic ULMFiT and inference on the two test sets
