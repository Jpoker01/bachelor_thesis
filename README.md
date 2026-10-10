Binary classification of customer incidents using NLP methods

This project folder contains all work performed within the scope of the bachelor thesis 'Binary classification of customer incidents using NLP methods'. The thesis was done in cooperation with SAP and focuses on a model that classifies sentences of SAP customer incidents as related either to an S/4HANA upgrade or to a migration. If an incident contains at least one upgrade sentence, the whole incident is classified as upgrade.

More than 90 experiments were carried out, combining different dataset balancing methods, text representations (TF-IDF, Word2Vec, Doc2Vec, DistilBERT) and classifiers. The best F1 score (74%) was achieved with TF-IDF, random undersampling and logistic regression. The best recall (89%) was achieved both by TF-IDF with KNN and by a fine-tuned DistilBERT trained on back-translated data.

The bachelor thesis (in Czech) is available at: BT.pdf

Notes on the data

Due to the sensitive nature of SAP customer incidents, this repository does not contain any incident data or the code used for data collection. The experiments were run in Jupyter Lab (Python 3.8) on SAP's internal Kubeflow platform, so the notebooks are provided as HTML exports including their outputs and cannot be re-run without the original data.

Main libraries used: scikit-learn, nltk, spaCy, gensim and transformers.

To browse an experiment, open any .html file from the /elektronicka_priloha folder in a web browser.

Project structure

The work can be broken into three main parts:

Thesis - The full text of the bachelor thesis
Experiments - HTML exports of all Jupyter notebooks used for data preprocessing, data augmentation and the classification experiments
Appendices - Supporting documents referenced in the thesis
Thesis (/BT.pdf)

The full text of the bachelor thesis (in Czech).

Experiments (/elektronicka_priloha)

Lists all the experiments done for this bachelor thesis (appendix C of the thesis).

inc_preprocessing.html - Data preprocessing used for the TF-IDF, Word2Vec and Doc2Vec experiments (HTML parsing, sentence segmentation, tokenization, lemmatization, stop word removal, language and noise filtering)
preprocess_last_mod.txt - Supplementary preprocessing code taken from a concurrently developed SAP classification system (not the author's own work)
data_augment.html - Data augmentation of upgrade sentences using back translation (English - German - English) via the transformers library
/tf-idf - Notebooks utilizing the TF-IDF representation
/Word2Vec_avg - Notebooks utilizing Word2Vec (Skip-gram) sentence vectors created by averaging word vectors
/Doc2Vec - Notebooks utilizing the Doc2Vec (DBOW) representation
/DistilBERT - Notebooks utilizing a fine-tuned DistilBERT transformer

Notebook naming convention "inc_classify_representation_variant":

communication - Sentences from the communication part of the incidents are included (otherwise only the title and description are used)
undersampled - Random undersampling of the majority (migration) class
oversampled - Data augmentation of the minority (upgrade) class using back translation
sample_comb - Combination of data augmentation and undersampling
Appendices
/priloha_A/Incident.pdf - Anonymized example of an SAP customer incident (appendix A)
/priloha_B/vysledky_experimentu.pdf - Results of all experiments for each representation, balancing method and classifier
