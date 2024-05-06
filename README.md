<div align="center">    
 
# XL-WA: a Gold Evaluation Benchmark for Word Alignment in 14 Language Pairs

[![Conference](https://img.shields.io/badge/CLiC--it-2023-red
)](https://clic2023.ilc.cnr.it/)

</div>

## About the project
This is the repository for the paper [*XL-WA: a Gold Evaluation Benchmark for Word Alignment in 14 Language Pairs*](https://ceur-ws.org/Vol-3596/paper32.pdf), accepted at CLiC-it 2023 by Federico **Martelli**, Andrei Stefan **Bejgu**, Cesare **Campagnano**, Jaka **Čibej**, Rute **Costa**, Apolonija **Gantar**, Jelena **Kallas**, Svetla **Koeva**, Kristina **Koppel**, Simon **Krek**, Margit **Langemets**, Veronika **Lipp**, Sanni **Nimb**, Sussi **Olsen**, Bolette **Pedersen**, Valeria **Quochi**, Ana **Salgado**, László **Simon**, Carole **Tiberius**, Rafael-J **Ureña-Ruiz** and Roberto **Navigli**.

## Abstract
Word alignment plays a crucial role in several NLP tasks, such as lexicon injection and cross-lingual label projection.
The evaluation of word alignment systems relies heavily on manually-curated datasets, 
which are not always available, especially in mid- and low-resource languages.
In order to address this limitation, we propose XL-WA, a novel entirely manually-curated evaluation
benchmark for word alignment covering 14 language pairs.
We illustrate the creation process of our benchmark and compare statistical and neural approaches 
to word alignment in both language-specific and zero-shot settings, thus investigating the ability
of state-of-the-art models to generalize on unseen language pairs.


## Cite this work

If you use any part of this work, please consider citing the paper as follows:
```
@InProceedings{martelli-EtAl:2023:clicit,
  author    = {Martelli, Federico  and  Bejgu, Andrei Stefan  and  Campagnano, Cesare  and  Čibej, Jaka  and  Costa, Rute  and  Gantar, Apolonija  and  Kallas, Jelena  and  Koeva, Svetla  and  Koppel, Kristina  and  Krek, Simon  and  Langemets, Margit  and  Lipp, Veronika  and  Nimb, Sanni  and  Olsen, Sussi  and  Pedersen, Bolette Sandford  and  Quochi, Valeria  and  Salgado, Ana  and  Simon, László  and  Tiberius, Carole  and  Ureña-Ruiz, Rafael-J  and  Navigli, Roberto},
  title     = {XL-WA: a Gold Evaluation Benchmark for Word Alignment in 14 Language Pairs},
  booktitle      = {Procedings of the Ninth Italian Conference on Computational Linguistics (CLiC-it 2023)},
  month          = {November},
  year           = {2023}
}
```

## Dataset

### Download the data

You can download a copy of all the files in this repository by cloning the
[git](https://git-scm.com/) repository:

```sh
git clone git@github.com:SapienzaNLP/XL-WA.git
```

or [download a zip archive](https://github.com/SapienzaNLP/XL-WA/archive/main.zip).

### Data format
The data is available in tsv format, with the following columns:

```
Source sentence 	 Target sentence     	Alignment
Viral pneumonia accounts for about 200 million cases .	La polmonite virale conta circa 200 milioni di casi .	1-0 1-1 0-2 2-3 3-3 4-4 5-5 6-6 7-7 7-8 8-9													
They are of no economic importance .	Non presenta alcun interesse economico .	1-1 3-2 5-3 4-4 6-5			

```

* **Column 1:** Tokenized source sentence.
* **Column 2:** Tokenized target sentence.
* **Column 3:** Alignment information, provided using integer pairs, which indicate the correspondence between words in the source and target sentences. The first number in the pair indicates the index of the source word, while the second number indicates the index of the target word. The indices start from 0.

### Datasets

We release the datasets for Multilingual Word Alignment. Within the `data` folder, you can find a sub-folder for each of the 14 languages. Each sub-folder contains the data for the corresponding language (en-X). The data is further divided to train, dev and test sets. 

```
data
├── es
│   ├── train.tsv
│   ├── dev.tsv
│   └── test.tsv
├── bg
│   ├── train.tsv
│   ├── dev.tsv
│   └── test.tsv
...
```

####  Training data


The training data is generated automatically. For each language pair, we trained the [GIZA++](https://github.com/moses-smt/giza-pp) and [FastAlign](https://github.com/clab/fast_align) statistical systems using a randomly selected sample of 0.5 million parallel sentences. From this data, we extracted 1,000 sentences with the highest number of overlapping alignments derived from the previously mentioned silver-tagged dataset.

####  Evaluation data
Evaluation data is manually-annotated exclusively by professional mother tongue annotators with a solid academic background and proven experience in linguistic annotation tasks. For each language pair, we manually annotated ~300 sentences, dividing it into 30% for development and 70% for testing.

| **Lang. Pair** | **\# of Sentences (Dev)** | **\# of Sentences (Test)** | **\# of Alignments (Dev)** | **\# of Alignments (Test)** |
|---------------|---------------------------|----------------------------|--------------------------|---------------------------|
| EN-AR         | 90 | 210 | 1591 | 3597 |
| EN-BG         | 105 | 245 | 1719 | 4179 |
| EN-DA         | 105 | 245 | 1841 | 4136 |
| EN-ES         | 105 | 245 | 1961 | 4722 |
| EN-ET         | 105 | 245 | 1614 | 3722 |
| EN-HU         | 105 | 245 | 1580 | 3781 |
| EN-IT         | 103 | 243 | 1980 | 4765 |
| EN-KO         | 90 | 210 | 1277 | 3007 |
| EN-NL         | 105 | 245 | 1886 | 4490 |
| EN-PT         | 105 | 245 | 1849 | 4578 |
| EN-RU         | 90 | 210 | 1114 | 2582 |
| EN-SL         | 105 | 245 | 1942 | 4537 |
| EN-SV         | 90 | 210 | 1522 | 3530 |
| EN-ZH         | 90 | 210 | 1724 | 4135 |
| **Total**     | **1393** | **3253** | **23600** | **55761** |

For accessing the datasets in the following language pairs: EN-AR, EN-KO, EN-SV, EN-ZH, please contact [Babelscape](mailto:info@babelscape.com).


## License
This work is under the [Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) license](https://creativecommons.org/licenses/by-nc-sa/4.0/).
