---
title: "[DL/ML]Regularization"
categories:
  - DL-ML
tags:
  - DeepLearning
  - Regularization
  - EalryStopping
  - ParameterNormPenalty
  - DataArgumentation
  - NoiseRobustness
  - LabelSmoothing
  - Dropout
  - BatchNormalization
last_modified_at: 2021-08-10T00:00:00-00:00
---


## Summary 🤙
<hr/>
Generalization을 높이기 위해 학습을 방해하는 방법이다. 다시 말해 test set에서 잘 동작하게 하기 위한 방법이다.

<br><br/>


## Index 👀       
  * [Early Stopping](#early-stopping)
  * [Parameter Norm Penalty](#parameter-norm-penalty)
  * [Data argumentation](#data-argumentation)
  * [Noise robustness](#noise-robustness)
  * [Label smoothing](#label-smoothing)
  * [Dropout](#Dropout)
  * [Batch normalization](#batch-normalization)

<br/>


## Early Stopping
<hr/>

추가적인 Validation Data를 구성하고, Training Error와 Validation Error의 차이가 증가할 때 학습을 멈추는 방법이다.

<br><br/>

## Parameter Norm Penalty
<hr/>

$$
\begin{aligned}
&\text { total } \operatorname{cost}=\operatorname{loss}(\mathcal{D} ; W)+\frac{\alpha}{2}\|W\|_{2}^{2}
\end{aligned}
$$

Weight Parameter의 크기(절대값)를 정규화하여 작게 만드는 것이다.    
부드러운 함수가 Generalization 성능이 높을 것이라는 가정에서 출발한다.

<br><br/>


## Data argumentation
<hr/>

데이터가 많을 수록 성능이 높아진다. 단, 데이터가 한정적인 경우에 Label이 변하지 않는 선에서 데이터를 변형하여 데이터 셋을 증가시킬 수 있다.

<br><br/>


## Noise Robustness
<hr/>

입력이나 Weight에 Noise를 중간에 지속적으로 넣어주면 더 학습률이 높아질 수 있다. (이유는 아직 모름)

<br><br/>


## Label smoothing
<hr/>

* Mixup : 두개의 이미지를 섞고 label도 섞는다.
* Cutout : 이미지의 일정 영역을 뺀다.
* CutMix : 특정 영역을 잘라 다른 이미지를 넣는다.

<br><br/>


## Dropout
<hr/>

weight의 일부 파라미터를 0으로 초기화 하여 특정 feature에 국한되지 않도록 한다. 


<br><br/>



## Batch Normalization
<hr/>

$$
\begin{aligned}
\mu_{B} &=\frac{1}{m} \sum_{i=1}^{m} x_{i} \\
\sigma_{B}^{2} &=\frac{1}{m} \sum_{i=1}^{m}\left(x_{i}-\mu_{B}\right)^{2} \\
\hat{x}_{i} &=\frac{x_{i}-\mu_{B}}{\sqrt{\sigma_{B}^{2}+\epsilon}}
\end{aligned}
$$

 layer의 weight 파라미터를 정규화한다. (논란이 많으나 대부분의 경우에 성능이 향상된다.)

<br><br/>