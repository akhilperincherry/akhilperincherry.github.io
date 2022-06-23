## [Improving domain adaptation in de-identification of electronic health records through self-training](https://academic.oup.com/jamia/article-abstract/28/10/2093/6345434) - Paper Summary

### What
- Aim is to bridge the domain gap in de-identification of health records using unlabeled data from the target domain via a self-training framework.
- They use labeled data from source domain + unlabeled data from target domain.
- F1 score is used as evaluation metric

### Prior Work
- Hartman et al used unlabeled data to fine-tune the word-embedding layer, while our self-training framework uses unlabeled data to retrain the entire model.

- Prior to release, the four publicly available datasets were all manually de-identified, which replaced personal identifiers with plausible but realistic surrogate information; we evaluate our systems on this surrogate Personal Health Information (PHI) with plausible words, e.g., replacing the patient’s name with unique common names.

### Method
- Self-training framework
    - (1) Train a model on labeled samples from the training dataset in source domain.
    - (2) Use the trained model to generate pseudo-labels on unlabeled samples from the training dataset in target domain.
    - (3) Retrain the model with a combination of labeled and pseudo-labeled samples. Steps 2 and 3 can iterate multiple times to further boost performance.

- They stress the Importance of adding noise during training but remove the noise when generating pseudo-labels. (don't exactly understand their reasoning).

- They use data augmentation (word level and character level switch-out) and activation dropout as noise sources.

- In the retraining phase, they continue to train the best performing model from the first phase, and apply a similar training strategy (cross-entropy loss, stochastic gradient descent, and data augmentation). The difference is that each mini-batch contains half a batch of true labeled data and half a batch of pseudo-labeled data. In addition, they retrain the model for a total of fifty epochs and use the current model to update the pseudo-labels for every 5 epochs. They tune the same 3 hyperparameters in the same validation cohort, and the best performing model is chosen for testing.

<img src="paperSummaries/deidentificationSelfSupervised.png?raw=true"/>

### Evaluation
- Cross-domain experiments
    - Train on dataset A, test on B with two scenarios - B has no labeled data, B has some labeled data
    - With no labels, self-training shows an 8% improvement on dataset B.
    - With labels,  they train the model on the source domain first and then fine-tune it with the labeled data from the target domain. The self-training framework further retrains the fine-tuned model with unlabeled data from the target domain. 
		
### Observations
- self-training (after 20 epochs of retraining) helps to correct the whole entity when it contains at least 1 correct word. Specifically, among entities with at least 1 correct word, 37.8% are corrected by self-training, otherwise only 11.8% are corrected. Intuitively, if an entity has a correct word, the self-training framework can make the whole entity more compatible with the target domain, which finally corrects the whole entity.
- For the cases in which the predictions are very wrong, the framework does not significantly improve the performance.
- It was observed that a few additional labeled samples significantly boosted domain adaptation performance.
