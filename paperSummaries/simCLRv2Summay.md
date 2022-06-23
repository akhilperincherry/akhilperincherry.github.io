## [Big Self-Supervised Models are Strong Semi-Supervised Learners](https://arxiv.org/abs/2006.10029) - Paper Summary

### What
- Iterative development of SimCLR. Their solution is composed of three parts:
    - Unsupervised or self-supervised pre-training using unlabeled data in task agnostic way.
    - Supervised fine-tuning with labeled data.
    - Knowledge distillation into smaller(or same size) model using unlabeled examples again in a task specific way to transfer task specific knowledge.

- Under the linear evaluation protocol, SimCLRv2 achieves 79.8% top-1 accuracy, a 4.3% relative improvement over the previous state-of-the-art. When fine-tuned on only 1% / 10% of labeled examples and distilled to the same architecture using unlabeled examples, it achieves 76.6% / 80.9% top-1 accuracy, which is a 21.6% / 8.7% relative improvement over previous state-of-the-art.

### Key Ideas
- Using a big (deep and wide) neural network for self-supervised pretraining and fine-tuning greatly improves accuracy.

- They explain that although big models are important for learning general (visual) representations, the extra capacity may not be necessary when a specific target task is concerned. Therefore, with the task-specific use of unlabeled data, the predictive performance of the model can be further improved and transferred into a smaller network.

- A deeper projection head not only improves the representation quality measured by linear evaluation, but also improves semi-supervised performance when fine-tuning from a middle layer of the projection head.

- The first time the unlabeled data is used, it is used in a task-agnostic way, for learning general (visual) representations via unsupervised pretraining. The general representations are then adapted for a specific task via supervised fine-tuning. The second time the unlabeled data is used, it is used in a task-specific way, for further improving predictive performance and obtaining a compact model. For this, they train student networks on the unlabeled data with imputed labels from the fine-tuned teacher network.

### Method
<img src="paperSummaries/simclrv2.PNG?raw=true"/>

- Pre-training:
    - Differences from SimCLR
        - Larger ResNet models - deeper but less wider i.e. from ResNet50 to ResNet 152.

        - Deeper projection head. 

        - Instead of throwing away g (projection network) after pre-training, they fine-tune from a middle layer which helps improve linear evaluation and fine-tuning with a few labeled examples. They go from a 2 layer projection head to a 3 layer projection head and fine tune from the first layer of projection head which yields 14% improvement in top-1 accuracy when fine-tuned on 1% of labeled examples.

        - Memory network - moving average of weights for stabilization.

- Fine-tuning:
    - Instead of throwing it all away, they incorporate part of the MLP projection head into the base encoder during the fine-tuning.

    - Models are fine-tuned from a middle layer of the projection head, instead of the input layer of the projection head as in SimCLR. Note that fine-tuning from the first layer of the MLP head is the same as adding a fully-connected layer to the base network and removing an fully-connected layer from the head, and the impact of this extra layer is contingent on the amount of labeled examples during fine-tuning.

    - Only random crops and horizontal flips are used while training in fine-tuning and distillation phases.

- Knowledge distillation:
    - leverage the unlabeled data directly for the target task; use the fine-tuned network as a teacher to impute labels for training a student network.

    - The teacher network, which produces PT (yjxi), is fixed during the distillation; only the student network, which produces PS(yjxi), is trained.

    - Loss encourages student to match the teacher and also can have an ordinary cross entropy loss on the labels if labeled data is available. They focus on distillation using only unlabeled examples in their paper but when the number of labeled examples is significant, one can also combine the distillation loss with ground-truth labeled examples using a weighted combination.

    - Students can either be used with the same model architecture (self-distillation), which further improves the task-specific performance, or with a smaller model architecture, which leads to a compact model.

    - Only random crops and horizontal flips are used while training in fine-tuning and distillation phases.

    - Distillation with unlabeled examples improves fine-tuned models in two ways:
        - when the student model has a smaller architecture than the teacher model, it improves the model efficiency by transferring task-specific knowledge to a student model.

        - when the student model has the same architecture as the teacher model (excluding the projection head after ResNet encoder), self-distillation can still meaningfully improve the semi-supervised learning performance. To obtain the best performance for smaller ResNets, the big model is self-distilled before distilling it to smaller models.

### Evaluation and observations
- They use same augmentation as SimCLRv1. They also use linear evaluation protocol to evaluate representations and also evaluate on ImageNet, where they use all 1.28M images but only randomly subsampled 1% or 10% of images associated with labels i.e. mostly unlabeled data.

- They fine-tune from first layer of projection when there are 1% or 10% of labeled examples while they fine tune from input of projection head when 100% labels are available.
    - 1% of labels - trained for 60 epochs.
    - 10% of labels - trained for 30 epochs.

- By default only unlabeled examples are used for distillation.

- Increasing the size of the DNN has relatively limited effects for standard supervised learning (4% differences in smallest and largest models), but for self-supervised models, accuracy can differ by as much as 8% for linear evaluation, and 17% for fine-tuning on 1% of labeled images. 

- These results show that bigger models are more label-efficient for both supervised and semi-supervised learning, but gains appear to be larger for semi-supervised learning.

- They observe that using a deeper projection head during pretraining is better when fine-tuning from the optimal layer of projection head, and this optimal layer is typically the first layer of projection head rather than the input (0th layer), especially when fine-tuning on fewer labeled examples.

- When labeled fraction is small, distillation loss alone works almost as well as combining with label loss.
