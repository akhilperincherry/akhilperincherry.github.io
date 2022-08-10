## [An Image Is Worth 16X16 Words:Transformers For Image Recognition At Scale](https://arxiv.org/pdf/2010.11929.pdf) - Paper Summary

### Introduction

- This paper proposes using a completely transformer based model for vision data (sequences of image patches) and tasks i.e. without using CNNs.

- The approach is similar to transformer model's usage in NLP. Here, an image is split into a sequence of non-overlapping patches. These patches are treated in the same way as tokens(words) i.e. the linear embeddings of the patches are input to a transformer model. Since transformers are scalable in general, ViTs come with computational benefits.

- The authors warn that transformers lack some of the inductive biases that are common to CNNs such as translation equivariance, 2D neighborhood structure and locality. This is evident when ViT is trained with mid-size datasets such as ImageNet, it performs marginally lower than a comparable sized ResNet. However, the authors state that this problem is alleviated by large-scale training. When pre-trained on large datasets such as ImageNet-21k and JFT-300M and transferred/fine-tuned to tasks with fewer training samples, ViT beats SOTA benchmarks.

### Method

<img src="../paperSummaries/vit1.PNG?raw=true"/>

- Input image is split into sequence of flattened patches, where the number of patches N = HW/P.P. H, W is the image resolution and the patch size is PxP. N is the input sequence length to the transformer. 

- Like the original transformer, the transformer in this paper uses a latent fixed dimension D, so all the patches are flattened and mapped to D dimensions via learned linear projection resulting in patch embeddings.

- For class token, a learnable embedding is prepended to sequence of patch embeddings. It's state at transformer output layer is attached to a classification head which is a one hidden layer MLP during pre-training and a single linear layer at fine-tuning time.

- Learnable 1D positional encodings are used like in the original transformer paper.

- Fine-tuning: ViT is pre-trained on large datasets and then fine-tuned on smaller downstream tasks. To achieve this, the pre-trained prediction head is replaced by a zero initialized feedforward layer. The authors find that it is beneficial to fine-tune at higher resolutions than pre-training. The patch sizes are kept the same for higher resolution images which results in longer input sequences.

### Observations from the paper

- Vision Transformers dominate ResNets on the performance/compute trade-off. ViT uses approximately 2 to 4 times less compute to attain the same performance.

- Model learns to encode distance within the image in the similarity of position embeddings, i.e. closer patches tend to have more similar position embeddings.

- While inspecting trained vision transformers, the authors find that "some heads attend to most of the image already in the lowest layers, showing that the ability to integrate information globally is indeed used by the model. Other attention heads have consistently small attention distances in the low layers. This highly localized attention is less pronounced in hybrid models that apply a ResNet before the Transformer, suggesting that it may serve a similar function as early convolutional layers in CNNs. Further, the attention distance increases with network depth. Globally, they see that the model attends to image regions that are semantically relevant for classification."

