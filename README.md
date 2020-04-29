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


# English Dataset:

**For German data set, A small change in loader.py at line number: 15 is necessary. We need to use codecs of type "utf8" because of German special letters.**

The data set is from the below link:\
https://github.com/davidsbatista/NER-datasets/tree/master/CONLL2003

Files used:
1. Training: train.txt
2. Development: dev.txt
3. Test: test.txt
**Command to trigger the training on GPU:**

THEANO_FLAGS='device=cuda,floatX=float32' python train.py --train deu_training.txt --dev deu_dev.txt --test deu_testa.txt

**Results English:**





