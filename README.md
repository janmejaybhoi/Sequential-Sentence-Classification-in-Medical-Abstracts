
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


## Resources

> 📖 Before going through the code in this notebook, you might want to get a background of what we're going to be doing. To do so, spend an hour (or two) going through the following papers and then return to this notebook:
1. Where our data is coming from: [*PubMed 200k RCT: a Dataset for Sequential Sentence Classification in Medical Abstracts*](https://arxiv.org/abs/1710.06071)
2. Where our model is coming from: [*Neural networks for joint sentence
classification in medical paper abstracts*](https://arxiv.org/pdf/1612.05251.pdf).
3. You can grab the data from Author's github repo also.([PubMed RCT200k from GitHub](https://github.com/Franck-Dernoncourt/pubmed-rct))

  
## Models

1. **Model-0 :** **Baseline (TF-IDF Multinomial Naive Bayes)**
2. **Model-1 :** **Conv1D (token embeddings)**
3. **Model-2 :** **USE (Universal Sentence Encoder Pretrained embeddings)**
4. **Model-3 :** **Conv1D (character embeddings)**
5. **Model-4 :** **Pretrained token embeddings(USE) + character embeddings (Hybrid embedding)**
6. **Model-5 :** **Pretrained token embeddings(USE) + character embeddings + positional embeddings(Tribrid embedding)**



## Visualize Tribrid Model (Pretrained token embeddings(USE) + character embeddings + positional embeddings)
![Results](https://github.com/janmejaybhoi/Sequential-Sentence-Classification-in-Medical-Abstracts/blob/main/img/Model_fig.JPG)

## Results

Since the [*PubMed 200k RCT:
a Dataset for Sequential Sentence Classification in Medical Abstracts*](https://arxiv.org/pdf/1710.06071.pdf) paper compares their tested model's F1-scores on the test dataset, let's take at our model's F1-scores.

Though, in comparison to the results reported in Table 3 of the [*PubMed 200k RCT:
a Dataset for Sequential Sentence Classification in Medical Abstracts*](https://arxiv.org/pdf/1710.06071.pdf) paper, our model's F1-score is still underperforming (the authors model achieves an F1-score of 90.0 on the 20k RCT dataset versus our F1-score of ~84.4).

There are some things to note about this difference:
* Our models (with an exception for the baseline) have been trained on ~18,000 (10% of batches) samples of sequences and labels rather than the full ~180,000 in the 20k RCT dataset.
  * This is often the case in machine learning experiments though, make sure training works on a smaller number of samples, then upscale when needed (an extension to this project will be training a model on the full dataset).

### Ploting Metrics:
![Results](https://github.com/janmejaybhoi/Sequential-Sentence-Classification-in-Medical-Abstracts/blob/main/img/Model_scores.JPG)

The table shows the **Metrics** of all the model:

|Model                        |accuracy   |precision |  recall  |  f1     |
|----------------------------| --------  | :------: | :------: | ------: |
|baseline                     | 0.721832  | 0.718647 | 0.721832 | 0.698925|
|custom_token_embed_conv1d    | 0.808288  | 0.804780 | 0.808288 | 0.805473|
|pretrained_token_embed       | 0.751059  | 0.745737 | 0.751059 | 0.746384|
|custom_char_embed_conv1d     | 0.669337  | 0.663860 | 0.669337 | 0.659734|
|hybrid_char_token_embed      |0.759831   | 0.756189 | 0.759831 | 0.754541|
|tribrid_pos_char_token_embed |0.848007   | 0.849911 | 0.848007 | 0.844585|
