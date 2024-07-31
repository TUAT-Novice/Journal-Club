MProtoNet: A Case\-Based Interpretable Model for Brain Tumor Classification with 3D Multi\-parametric Magnetic Resonance Imaging

![](img%5CJC_MProtoNet0.png)

MIDL 2023 Oral paper

[pdf](https://arxiv.org/abs/2304.06258)

[code](https://github.com/aywi/mprotonet)

1\. Interpretability

Definition:  <span style="color:#000000">The degree to which a human can understand the cause of a decision that the machine makes</span> \.

| Positive | Negative |
| :-: | :-: |
| 97.5% | 2.5% |

Image attribution maps

![](img%5CJC_MProtoNet1.png)

The result is positive\, because …

Attribution maps can be also seen as weakly supervised object localization results\, obtained from classification data\.

---

Let’s begin with the interpretability. It can be defined as the degree to which a human can understand the cause of a decision that the machine makes. And it can usually represented by image attribution maps, annotation text and so on. In this work we mainly talk about the attribution maps, and the maps can be also seen as weakly supervised object localization results, obtained from classification data.

1\. Interpretability: Related Work on Attribution Maps

__Post hoc methods __

Attribution maps

__Concept\-based methods__

__In\-model methods__

Post hoc methods are simple\, and can get maps directly by gradients no matter what the CNN structure is \(besides vanilla CAM\)

In\-model methods need additional well\-designed structure for concept or prototype\, but usually gets better localization results

This work introduces case\-based method \(ProtoPNet\) into 3D brain tumor classification

ProtoPNet\, XProtoNet

__Case\-based methods__

---

Currently, there are mainly 2 kinds of methods for attribution maps. 

2\. ProtoPNet \(NIPS 2019\): Framework

<span style="color:#121212">Learnable prototype vectors in </span>  <span style="color:#121212">latent</span>  <span style="color:#121212"> space\, shaped \(m\, 1\, 1\, 512\)</span>

<span style="color:#FF0000">Corresponds to a 32\*32 patch in the input size</span>

<span style="color:#121212">Receptive radio: 32:1</span>

m features for classification

![](img%5CJC_MProtoNet2.png)

m \* 7 \* 7 similarity scores

Input shaped \(224\, 224\,3\)

Feature shaped \(7\, 7\, 512\)

__VGG__

__ResNet__

__DenseNet__

__…__

---

In the ProtoPNet, we need to learn the prototype vectors, which is defined in the image latent space. With the image, we first use the pre-trained model such as VGG, ResNet for feature extraction.

2\. ProtoPNet \(NIPS 2019\): Training

![](img%5CJC_MProtoNet3.png)

L2 distance in practice

Clst to minimize to distance \(max score\) between prototype vector and feature which are in same class

![](img%5CJC_MProtoNet4.png)

![](img%5CJC_MProtoNet5.png)

m \* 7 \* 7 scores

![](img%5CJC_MProtoNet6.png)

2\. ProtoPNet \(NIPS 2019\): Visualization

![](img%5CJC_MProtoNet7.png)

2\. ProtoPNet: Visualization Result

![](img%5CJC_MProtoNet8.png)

Activation map\, and the learned top3 prototypes from training images

3\. MProtoNet: Framework & Contribution

![](img%5CJC_MProtoNet9.png)

__log\-sum\-exp \(LSE\) pooling__

Contribution

First attempt to introduce case\-based method into 3D mpMRI data

Propose the \(1\) novel attention structure and soft masking \(2\) Online\-CAM loss for the task

More interpretability metrics are evaluated

![](img%5CJC_MProtoNet10.png)

3\. MProtoNet: Framework

![](img%5CJC_MProtoNet11.png)

XProtoNet \(CVPR 2021\)

![](img%5CJC_MProtoNet12.png)

![](img%5CJC_MProtoNet13.png)

Fusion through dot product rather than attention

![](img%5CJC_MProtoNet14.png)

Soft masking                                                 to sharpen the activation value

![](img%5CJC_MProtoNet15.png)

Attention                                                               to get highly\-activated regions

---

Rough result


![](img%5CJC_MProtoNet16.png)

3\. MProtoNet: Framework

![](img%5CJC_MProtoNet17.png)

![](img%5CJC_MProtoNet18.png)

3\. MProtoNet: Training

XProtoNet \(CVPR 2021\)

![](img%5CJC_MProtoNet19.png)

![](img%5CJC_MProtoNet20.png)

<span style="color:#FF0000">Loss for prototypes vectors</span>

![](img%5CJC_MProtoNet21.png)

![](img%5CJC_MProtoNet22.png)

---

They use the 3-stage training method. In Stage-1, they mainly focus on the 

3\. MProtoNet: Results on BraTS2020

![](img%5CJC_MProtoNet23.png)

Ablation experience on Classification and Interpretability\. The performance on interpretability is better\.

3\. MProtoNet: Visualization Results on BraTS2020

![](img%5CJC_MProtoNet24.png)

The learned top3 prototypes from training images\. The prototypes are meaningful\, and the attention map is similar to the prototypes\.

3\. MProtoNet: Visualization Results on BraTS2020

![](img%5CJC_MProtoNet25.png)

3\. MProtoNet: Conclusion & Expectation

![](img%5CJC_MProtoNet26.png)

Conclusion

Introduce case\-based into 3D mpMRI

Propose 2 tricks \(soft masking & online\-CAM loss\)

Achieve competitive results

No labels for localization are required

Expectation

Dynamic prototype vector rather than a fixed one

Other fusion methods rather than attention

Ideas from other interpretable models

