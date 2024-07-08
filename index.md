## Research

My research interests are in domain adaptation (via generative modeling, semi/self/un-supervised learning), multimodal learning and task-agnostic learning. In general, I am interested in solving problems that stem from a lack of annotated or domain-specific data and problems where testing data is distributionally different from training data.

In my current job, I primarily work on object detection, tracking and segmentation using camera data and point cloud data. I graduated from the University of Florida in 2016. Before that, I worked at the Indian Institute of Science under [Prof. K R Ramakrishnan](https://iiscprofiles.irins.org/profile/3742) at the Computer Vision and Artificial Intelligence (CVAI) lab where I worked on touch-interface applications using a projector-camera based setup.

---

### Publications

* Yujiao Shi, Hongdong Li, **Akhil Perincherry**, Ankit Vora, Weakly-supervised Camera Localization by Ground-to-satellite Image Registration, In Proc. European conference on computer vision (ECCV), 2024

* Yanhao Zhang, Yujiao Shi, Shan Wang, Ankit Vora, **Akhil Perincherry**, Yongbo Chen, Hongdong Li, [Increasing SLAM Pose Accuracy by Ground-to-Satellite Image Registration](https://arxiv.org/pdf/2404.09169), In Proc. IEEE Conference on Robotics and Automation (ICRA), 2024

* Yujiao Shi, Fei Wu, **Akhil Perincherry**, Ankit Vora, Hongdong Li, [Boosting 3-DoF Ground-to-Satellite Camera Localization Accuracy via Geometry-Guided Cross-View Transformer](https://arxiv.org/pdf/2307.08015), In Proc. IEEE International Conference on Computer Vision (ICCV), 2023

* Shan Wang, Yanhao Zhang, **Akhil Perincherry**, Ankit Vora, Hongdong Li, [View Consistent Purification for Accurate Cross-View Localization](https://arxiv.org/pdf/2308.08110), In Proc. IEEE International Conference on Computer Vision (ICCV), 2023

* Shan Wang, Yanhao Zhang, Ankit Vora, **Akhil Perincherry**, Hongdong Li, [Satellite image based cross-view localization for autonomous vehicle](https://ieeexplore.ieee.org/abstract/document/10161527), In Proc. IEEE Conference on Robotics and Automation (ICRA), 2023

* Adarsh Appaiah (equal contribution), **Akhil Perincherry** (equal contribution), Ajinkya Sanjeev Keskar (equal contribution) and Vijaya Krishna "[Spectrum Sensing in Cognitive Radio Based
on Compressive Measurements](https://ieeexplore.ieee.org/abstract/document/6749450)". IEEE International conference on Emerging trends in Communication, Control, Signal Processing and
Computing Applications (IEEE-C2SPCA), 2013

---

### Patents

* **A Perincherry**, C Cruise "[Domain Generation via Learned Partial Domain Translations](https://patents.google.com/patent/DE102021101850A1/en)" US Patent 11321587 - Generative modeling to generate novel domain data.

* **A Perincherry**, K Singh, N Nagraj Rao "[Vehicle Intersection Operation](https://patents.google.com/patent/US20210001844A1/en)" US Patent 11420625 - CNN+LSTM based model to predict vehicle right-of-way at intersections.

* **A Perincherry**, A Chand "[Generating Artificial Video with Changed Domain](https://patents.google.com/patent/US20240202533A1/en)" US Patent App. 18/065672 - Guiding video generation using associated audio.

* N Nagraj Rao, **A Perincherry** "[Sensor Domain Adaptation](https://patents.google.com/patent/US20220383040A1/en)" US Patent App. 17/330692 - Generative modeling to translate legacy sensor data domain to newer domain.

* **A Perincherry**, A Mordovanakis, S Suthar, A Chand "[Neural Network Object Identification](https://patents.google.com/patent/US20220327320A1/en)" US Patent App. 17/228765 - Radar camera sensor fusion to perform object 3D shape identification.

* **A Perincherry**, I Patel, K Min "[RCCC to RGB Domain Translation with Deep Neural Networks](https://patents.google.com/patent/US11068749B1/en)" US Patent 11068749 - Generative modeling to translate automotive sensor domain to common domains.

* N Jaipuria, G Sholingar, V Murali, R Bhasin, **A Perincherry** "[Vehicle Image Generation](https://patents.google.com/patent/US11042758B2/en)" US Patent 11042758 - Generative modeling to improve driving safety features via domain adaptation.

---

### Knowledge Distillation Series (Paper Summaries)

- [SimCLR](paperSummaries/simCLRsummary.md)
- [SimCLRv2](paperSummaries/simCLRv2Summay.md)
- [Big Self-Supervised Models Advance Medical Image Classification](paperSummaries/medicalImageSelfSupervisedLearning.md)
- [Contrastive Training for Improved Out-of-Distribution Detection](paperSummaries/contrastiveTrainingForOOD.md)
- [Improving domain adaptation in de-identification of electronic health records through self-training](paperSummaries/healthDeidentificationSelfSupervisedSummary.md)
- [Transformers](paperSummaries/attentionSummary.md)
- [ViT](paperSummaries/vitPaperSummary.md)
- [DALL-E](paperSummaries/dalleSummary.md)
- [Training data-efficient image transformers & distillation through attention](paperSummaries/deitSummary.md)
- [BERT Pre-Training of Image Transformers](paperSummaries/BEITSummary.md)
- [Masked Autoencoders Are Scalable Vision Learners](paperSummaries/maeSummary.md)

### Past Research

[Rat whisker tracking - Univ. of Florida (2016)](/whiskerTracking.md)
<img src="images/Whisker_1.PNG?raw=true"/>

---
[Table-top touch interface using Kinect - Indian Institute of Science (2014)](/touchHyperlink.md)  

 <img src="images/cvai_video1.gif?raw=true"/>

---
[Compressive sensing as a solution to Cognitive Radio (2013)](/compressiveSensing.md)
<img src="images/CS_3.PNG?raw=true"/>

---

<!-- ### Other Projects

- [Adaptive Speaker Recognition using Online Learning](/pdf/AdaptiveSpeakerRecognition_OnlineLearning_AkhilPerincherry.pdf)

   A novel technique was proposed to perform speaker recognition using adaptive algorithms such as Recursive Least Squares (RLS), Normalized Least Mean Squares (NLMS). The filter coefficients were seen to model the voice characteristics. The developed model was compared with the state of the art MFCC-VQ technique.

---

- [Motor Imagery Classification (2015)](https://github.com/akhilperincherry/MotorImageryClassification)
<img src="images/MotorImagery.PNG?raw=true"/>
Motor imagery tasks are tasks where a person imagines performing a task and the neural signals are recorded. The model classifies between left finger and tongue imagery movements using Common Spatial Pattern and Support Vector Machines from EEG recorded signals. The model developed recorded an accuracy of 92%, the highest that has been reported for the BCI 2000 dataset at the time.

---

- [Manatee Call Detection Using Recursive Least Squares (2015)](/pdf/Manatee_Sound_Detection_AkhilPerincherry.pdf)

   The problem of detecting Manatee calls in a signal plus noise situation is studied. Trained models were obtained for Manatee calls and noise, and an ensemble of models were applied and compared.

---

- Majorized Multi-class Kernel SVM

   A Majorized Multi-class kernel SVM was derived and designed from scratch, and compared with other ML algorithms such as Random Forests, Logistic Regression, Deep Neural Networks, Decision Trees and libSVM implementation.

--- -->

## Service

- Served as a reviewer for NeurIPS 2024.

- Served as a reviewer for ACM SIGGRAPH 2024.

- Served as a reviewer for ICCV 2023.

- MentorUF, University of Florida (2016) -
Mentored a middle-school student for a year.

- IEEE Eta Kappa Nu, University of Florida (2016)

- Teaching Assistant for graduate course "Foundations of Digital Signal Processing" at University of Florida during fall 2015.

- Cluster coordinator for South-East Bangalore, Youth For Seva (2013-2014) - 
Involved in sapling planting and providing kids with computer training.

<p style="font-size:11px"></p>
