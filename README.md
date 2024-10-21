# Machine Translation Error Annotated Corpus

## Overview

This repository contains the annotated corpus used in the paper titled "[Fine-grained error analysis on English-to-Japanese machine translation in the medical domain.](https://aclanthology.org/2020.eamt-1.17/)", which was published in the European Association for Machine Translation (EAMT) journal. The corpus has been carefully annotated to identify five types of translation errors in machine-generated translations from English into Japanese based on [Multidimensional Quality Metrics (MQM)](https://themqm.org/the-mqm-full-typology/).
In the dataset, five types of translation errors are labeled at the token level:

1. **Under-generation (ug)**: Missing translations (annotated on the source sentence).
2. **Over-generation (og)**: Unnecessary or extra translations.
3. **Mis-translation (mt)**: Incorrect translations.
4. **Syntax error (se)**: Grammatical errors.
5. **Lexical choice (lc)**: Incorrect word or phrase choice.

The corpus is designed to support research in machine translation error analysis and quality estimation.

## Table of Contents

- [Dataset Description](#dataset-description)
- [File Structure](#file-structure)
- [Data Sources and Machine Translation Systems](#data-sources-and-machine-translation-systems)
- [License](#license)
- [Citation](#citation)
- [Contact](#contact)

## Dataset Description

The dataset consists of token-level annotations for machine-translated sentences. Each token is labeled as either **O** (no error) or **E** (error), depending on whether it contains one of the five types of translation errors. The dataset is structured as follows:

### Error Labelling:

The error typology in the dataset is based on the MQM framework customized to better suit the evaluation of English-to-Japanese translations by NMT systems. While MQM has been widely used for translation quality assessment in European languages, our dataset extends its application to Japanese, a language with distinct grammatical and sociolinguistic features. We selected and adapted five error subtypes from MQM, focusing on key issues identified in NMT translations.

- **Languages**: [Source language (e.g., Japanese)] and [Target language (e.g., English)]
- **Error Types**:
  - **ug**: Under-generation (missing translations, annotated on the source sentence)
  - **og**: Over-generation (extra translations)
  - **mt**: Mis-translation (incorrect translations)
  - **se**: Syntax error (grammatical errors)
  - **lc**: Lexical choice (incorrect word or phrase choice)
- **File Format**: Text files with token-level annotations
- **Tokenization**: Japanese sentences are tokenized using [MeCab](https://taku910.github.io/mecab/).

### Example Data Structure:

Each annotated file (`lab_xx`, where `xx` refers to the error type) follows the format:

```
Sentence No: token {label}
 token {label}
 token {label}
 ...
```

For example:

```
Sentence 1: He O
 goes O
 to O
 school O
 私 E
 は O
 会社 E
 に O
 行きます O
```

In addition to the labeled files, the `parallel_corpus` files contain only the source and target sentence pairs without annotations.

## File Structure

```
translation-error-annotation/
│
├── data/
│   ├── lab_ug    # Under-generation annotations
│   ├── lab_og    # Over-generation annotations
│   ├── lab_mt    # Mis-translation annotations
│   ├── lab_se    # Syntax error annotations
│   ├── lab_lc    # Lexical choice annotations
│   ├── lab_all   # Annotations of all types of error
│   └── parallel_corpus      # Source and target sentence pairs
│
├── README.md
```

- **data/**: Contains the annotated corpus files.
- **LICENSE**: License information for the repository.
- **README.md**: This file, providing an overview of the project.

## Data Sources and Machine Translation Systems
### Data Sources
The dataset used for evaluation consists of 2,480 sentences from the medical/pharmaceutical domain in English. The sentences were collected from five different types of documents, as listed below:
1.	[**MSD Manual Consumer Version**](https://www.msdmanuals.com/home)
•	Aimed at the general population without domain-specific knowledge.
2.	[**MSD Manual Professional Version**](https://www.msdmanuals.com/professional)
•	Contains highly technical terms for health professionals.
3.	[**New England Journal of Medicine (NEJM)**](https://www.nejm.org/)
•	A standard academic journal in the field of medicine.
4.	[**Journal of Clinical Oncology (JCO)**](https://ascopubs.org/journal/jco)
•	A leading journal in the field of clinical oncology.
5.	[**ICH Guidelines**](https://www.ich.org/page/ich-guidelines)
•	International regulations for pharmaceutical manufacturing processes.

The source sentences were randomly extracted from these documents. Two versions of the MSD Manual were differentiated by the difficulty levels of their content: the Professional Version includes highly technical terms, while the Consumer Version is written for a general audience.

### Machine Translation Systems
We obtained Japanese translations of the dataset from two different Neural Machine Translation (NMT) systems. The target text was produced by randomly selecting each translated sentence from the two NMT outputs in a 1:1 ratio, resulting in bilingual pairs of the 2,480 sentences.
Reference Translations
The sources used in this study had corresponding Japanese versions, which were prepared by human translators with professional review. These Japanese versions were used as reference translations to calculate evaluation metrics such as BLEU score and Levenshtein distance ratio for further analysis.

## License

This dataset is licensed under a [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/) International License.

## Citation

If you use this dataset in your research, please cite our paper:

```
@inproceedings{hayakawa2020fine,
  title={Fine-grained error analysis on English-to-Japanese machine translation in the medical domain},
  author={Hayakawa, T. and Arase, Y.},
  booktitle={Proceedings of the 22nd Annual Conference of the European Association for Machine Translation},
  pages={155--164},
  year={2020},
  month={November}
}
```
## Reference
Burchardt, Aljoscha. "Multidimensional quality metrics: a flexible system for assessing translation quality." Proceedings of Translating and the Computer 35. 2013.

## Contact

For any questions or issues, please contact Takeshi Hayakawa at taqueci@gmail.com.

---
