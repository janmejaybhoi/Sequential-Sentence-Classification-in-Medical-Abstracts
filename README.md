
# Sequential Sentence Classification in Medical Abstracts
Replicating the deep learning model behind the 2017 paper [*PubMed 200k RCT: a Dataset for Sequenctial Sentence Classification in Medical Abstracts*](https://arxiv.org/abs/1710.06071).

When it was released, the paper presented a new dataset called PubMed 200k RCT which consists of ~200,000 labelled Randomized Controlled Trial (RCT) abstracts.

The goal of the dataset was to explore the ability for NLP models to classify sentences which appear in sequential order.

In other words, given the abstract of a RCT, what role does each sentence serve in the abstract?

![Results](https://github.com/janmejaybhoi/Sequential-Sentence-Classification-in-Medical-Abstracts/blob/main/img/Model.JPG)


## Overview

1. *Classify a Randomized clinical trials (RCTs) abstarct to subclasses for easier to read and understand*.
2. *Basically convert a medical abstarct to chunks of sentences of particaular classes like "Background", "Methods", "Results" and "Conclusion".* 
3. *Its a Many to One Text Classification problem. Where we categorize a sequence to a prticular class.*


## Dataset

[*PubMed 200k RCT: a Dataset for Sequential Sentence Classification in Medical Abstracts*](https://arxiv.org/abs/1710.06071)

  
## Models

1. **Model-0 :** **Baseline (TF-IDF Multinomial Naive Bayes)**
2. **Model-1 :** **Conv1D (token embeddings)**
3. **Model-2 :** **USE (Universal Sentence Encoder Pretrained embeddings)**
4. **Model-3 :** **Conv1D (character embeddings)**
5. **Model-4 :** **Pretrained token embeddings(USE) + character embeddings (Hybrid embedding)**
6. **Model-5 :** **Pretrained token embeddings(USE) + character embeddings + positional embeddings(Tribrid embedding)**


baseline	72.183238	0.718647	0.721832	0.698925
custom_token_embed_conv1d	80.828810	0.804780	0.808288	0.805473
pretrained_token_embed	75.105918	0.745737	0.751059	0.746384
custom_char_embed_conv1d	66.933669	0.663860	0.669337	0.659734
hybrid_char_token_embed	75.983053	0.756189	0.759831	0.754541
tribrid_pos_char_token_embed	84.800741	0.849911	0.848007	0.844585



## Visualize Tribrid Model (Pretrained token embeddings(USE) + character embeddings + positional embeddings)
![Results](https://github.com/janmejaybhoi/Sequential-Sentence-Classification-in-Medical-Abstracts/blob/main/img/Model_fig.JPG)

## Results
![Results](https://github.com/janmejaybhoi/Sequential-Sentence-Classification-in-Medical-Abstracts/blob/main/img/Model_scores.JPG)
|Model                        |accuracy   |precision |  recall  |  f1     |
|----------------------------| --------  | :------: | :------: | ------: |
|baseline                     | 0.721832  | 0.718647 | 0.721832 | 0.698925|
|custom_token_embed_conv1d    | 0.808288  | 0.804780 | 0.808288 | 0.805473|
|pretrained_token_embed       | 0.751059  | 0.745737 | 0.751059 | 0.746384|
|custom_char_embed_conv1d     | 0.669337  | 0.663860 | 0.669337 | 0.659734|
|hybrid_char_token_embed      |0.759831   | 0.756189 | 0.759831 | 0.754541|
|tribrid_pos_char_token_embed |0.848007   | 0.849911 | 0.848007 | 0.844585|
