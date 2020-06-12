# ON-LSTM

This repository contains the reproducibility code used for word-level language model and unsupervised parsing experiments in the original paper 
[Ordered Neurons: Integrating Tree Structures into Recurrent Neural Networks](https://arxiv.org/abs/1810.09536),
forked from the https://github.com/yikangshen/Ordered-Neurons 


## Software Requirements
Python 3.6, NLTK and PyTorch 0.4 are required for the current codebase.

## Steps

1. Install PyTorch 0.4 and NLTK

2. Download PTB data. Note that the two tasks, i.e., language modeling and unsupervised parsing share the same model 
strucutre but require different formats of the PTB data. For language modeling we need the standard 10,000 word 
[Penn Treebank corpus](https://github.com/pytorch/examples/tree/75e435f98ab7aaa7f82632d4e633e8e03070e8ac/word_language_model/data/penn) data, 
and for parsing we need [Penn Treebank Parsed](https://catalog.ldc.upenn.edu/LDC99T42) data.

3. Scripts and commands

  	+  Train Language Modeling
  	```python main.py --batch_size 20 --dropout 0.45 --dropouth 0.3 --dropouti 0.5 --wdrop 0.45 --chunk_size 10 --seed 141 --epoch 1000 --data /path/to/your/data```

  	+ Test Unsupervised Parsing
    ```python test_phrase_grammar.py --cuda```
    
    The default setting in `main.py` achieves a perplexity of approximately `56.17` on PTB test set 
    and unlabeled F1 of approximately `47.7` on WSJ test set.

## Important notes while reproducing the experiments:
1. This code can be used to do experiments for language modelling and Unsupervised Parsing. For the Unsupervised Parsing, we need to PTB data set which(only 5% it) can be downloaded from nltk. Also avaialble at: https://www.kaggle.com/nltkdata/penn-tree-bank/data
2. We have found that it is efficient to train the model on ECS computer than allocated VM.
3. Report has been uploaded as Reproducibility_Ordered_Neurons.pdf
4. Test results and important figures used in the report uploaded under Reproducibility_Challenge_test_results

NOTE: Understanding the ON-LSTM architecture is not straight forward and it took a good amount of time to understand the architecture and the intuition behind the changes. And the training is time consuming since the On-LSTM ordering slowed down the performance Sequential LSTM model further, and didn't give us much space to try something new.
