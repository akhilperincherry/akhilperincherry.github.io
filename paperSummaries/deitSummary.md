## [Training data-efficient image transformers & distillation through attention](https://arxiv.org/pdf/2012.12877.pdf) - Paper Summary

### Introduction

- Vision transformers are pre-trained with incredible amount of image data such as Google's JFT300M which may not be do-able for everyone. Without this large scale pre-training, transformers have difficulty generalizing due to the lack of inductive biases found in convolution based networks. To alleviate this, the authors develop a convolution-free transformer which is pre-trained with just imagenet data and achieves comparable performance.

- They propose a transformer specific teacher-student framework that uses a distillation token which enforces the student learns from the teacher via attention. The distillation token works similar to a class token except that it attempts to reproduce the label generated by the teacher.

- The authors observe that in their distillation framework, the image transformers learn better from a CNN than another comparable transformer. They think that this could be due to inductive biases being learnt by the student transformer from the teacher CNN model.

- They study different variants of distillations:
  - Soft distillation - KL distance between softmax of teacher and the softmax of the student is minimized.
  <img src="../paperSummaries/deit1.PNG?raw=true"/>

  - Hard distillation - hard decision of the teacher is taken as the true label here.   
  <img src="../paperSummaries/deit2.PNG?raw=true"/>
  <img src="../paperSummaries/deit3.PNG?raw=true"/>

### Distillation token technique

<img src="../paperSummaries/deit4.PNG?raw=true"/>

- A Distillation token is added along with a typical combination of class token and patches. Just like the class token, it interacts with other embeddings through self-attention and is regressed by the final layer in the network. The distillation embedding facilitates learning the teacher's output while being complementary to the class embeddings.

- The authors observe that while distillation and class tokens are similar conceptually, they converge to different vectors and become similar only in the later layers of the network (not same however) as they both are trying to make similar prediction (not necessarily identical). 

- The above was not seen to be the case when they used two class tokens which although initialized randomly converged towards the same vector.

- They use the commonly followed approach in transformers of pre-training using low-res and fine-tuning using high-res.

- In the fine-tuning stage, both true label as well as teacher label are used.

- For classification after training, they use just the class embeddings, just the distillation embeddings, along with a linear classifier as well as a late fusion of the two separate heads before a softmax output layer. They observe that the fusion approach works the best, followed by only distillation token approach.


