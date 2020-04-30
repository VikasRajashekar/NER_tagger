# Note: 
**This is fork of repository(https://github.com/glample/tagger) with minor modifications for German language.**


**Set up instructions:**
Conda environment setup:

Following are the list of commands to be used to get the environment ready for the project:
1.conda create --name NER_py python=2.7 \
2.conda activate NER_py \
3.conda install theano \
4.conda install -c mila-udem pygpu

# German Dataset:
## Note: Neither in paper or in github I was able to find exact settings/hyper-parameters  used for German language for SOTA results

**For German data set, A small change in loader.py at line number: 15 is necessary. We need to use codecs of type "latin-1" because of German special letters.**

The dataset used is from the below link:\
https://github.com/MaviccPRP/ger_ner_evals/tree/master/corpora/conll2003

Files used:\
The raw files are converted to txt files as required by the project.

1. Training: deu.train --> deu_training.txt
2. Development: deu.de --> deu_dev.txt
3. Test: deu.testa --> deu_testa.txt

**Command to trigger the training on GPU:**

THEANO_FLAGS='device=cuda,floatX=float32' python train.py --train deu_training.txt --dev deu_dev.txt --test deu_testa.txt

**Results German:**

For default setting as in the github, the Network was able to achieve **FB1 of 66.30** for 100 epocs! \
accuracy:  94.44%; precision:  73.46%; recall:  60.42%; FB1:  66.30\
              LOC: precision:  75.98%; recall:  63.76%; FB1:  69.34  991 \
             MISC: precision:  68.74%; recall:  57.92%; FB1:  62.87  851 \
              ORG: precision:  77.97%; recall:  55.04%; FB1:  64.53  876 \
              PER: precision:  71.52%; recall:  64.17%; FB1:  67.64  1257 \

**Experiments with hyper-parameters:**\
1. Change word embedding sizxe to 200 from 100 and LSTM size to 200 from 100 for Tokens.\ 
Results as of 29 Epocs.
Network achieved FB1 score of : **66.07000**\

2. Use settings mentioned in paper: Learning rate of 0.01 and Token embedding size of 64.
Result as of 28 Epocs.
Network achieved FB1 score of : **67.48000**\
accuracy:  94.54%; precision:  74.58%; recall:  61.62%; FB1:  67.48 \
              LOC: precision:  78.22%; recall:  65.37%; FB1:  71.22  987 \
             MISC: precision:  79.24%; recall:  51.39%; FB1:  62.34  655 \
              ORG: precision:  71.60%; recall:  58.50%; FB1:  64.39  1014 \
              PER: precision:  71.88%; recall:  68.59%; FB1:  70.20  1337\


# English Dataset:

**For English data set, A small change in loader.py at line number: 15 is necessary. We need to use codecs of type "utf8"**

The data set is from the below link:\
https://github.com/davidsbatista/NER-datasets/tree/master/CONLL2003

Files used:
1. Training: train.txt
2. Development: dev.txt
3. Test: test.txt
**Command to trigger the training on GPU:**

THEANO_FLAGS='device=cuda,floatX=float32' python train.py --train train.txt --dev valid.txt --test test.txt

**Results English:**
**FB1 score of about 83.35**\
accuracy:  96.55%; precision:  85.58%; recall:  81.23%; FB1:  83.35\
              LOC: precision:  89.54%; recall:  85.67%; FB1:  87.56  1596\
             MISC: precision:  80.50%; recall:  73.50%; FB1:  76.84  641\
              ORG: precision:  79.96%; recall:  77.84%; FB1:  78.89  1617\
              PER: precision:  89.58%; recall:  83.49%; FB1:  86.43  1507\





