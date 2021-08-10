---
title: "[DL/ML]Optimization - Important Concept"
categories:
  - DL-ML
tags:
  - optimization
last_modified_at: 2021-08-03T00:00:00-00:00
---


## Summary 🤙
<hr/>

"모델의 성능이 좋다"라는 기준들을 알아보고 어떻게 향상시킬 수 있는지 알아본다.     
>단, 어떤 방법이든 test data를 활용하면 cheating임을 명심하자.

<br><br/>


## Index 👀       
  * [Generalization](#generalization)
  * [fitting(Under|Over)](#underfitting--overfitting)
  * [Cross validation](#cross-validation)
  * [Bias-variance tradeoff](#bias-variance-tradeoff)
  * [BootStrapping](#bootstrapping)
  * [Bagging & Boosting](#bagging--boosting)

<br><br/>


## Generalization  
<hr/>
Trainning Error와 Test Error의 차이를 나타내는 것으로 이 Gap을 줄이는 것을 목표로 가지게 된다.   
훈련 데이터를 통해 얻은 Weight가 실제 데이터(test data)에서도 얼마나 잘 적용되는지 나타낸다.   

<br></br>

   

## Underfitting & Overfitting
<hr/>
__Underfitting__  이란 학습 데이터에 맞는 파라미터가 느슨하게 학습된 형태로서 적절한 파라미터로 판단하기 어려워진다.    
__Overfitting__ 이란 학습 데이터에 과도하게 최적화된 것으로서 앞서 언급한 Generalization gap을 증가시킬 수 있다.    

  
<br></br>

## Cross-validation
<hr/>
K-fold Cross-validation이라고 부르기도 한다.   
데이터셋을 일정한 크기로 k 그룹으로 나누어 1개의 validation set(test set이 절대 아니다.)과 k-1개의 training set으로 나누어 학습에 활용하는 것이다.     

예를 들어 100개의 데이터 셋을 10개의 fold로 나누고 모델A에 대해서는 1~9 fold 데이터셋을 training set으로 활용하고 10 fold 데이터셋을 validation set으로 활용, 모델 B, C에 대해서 각각 다른 validation set을 활용해 각각의 성능을 비교하여 적절한 모델을 택하는 방식이다.    
주로 [hyperparameter](https://machinelearningmastery.com/difference-between-a-parameter-and-a-hyperparameter/)(learing rate...)와 같은 모델의 특징을 평가하고 비교하기 위해 사용한다.    

<br></br>

## Bias-Variance tradeoff
<hr/>
주어진 데이터에 노이즈가 있는 경우 Bias와 Variance는 다음의 관계로 인해 둘다 동시에 줄이는 모델을 찾는 것은 힘들다.    

Cost = Bias^2 + Variance + Noise   
> $\begin{aligned} \mathbb{E}\left[(t-\hat{f})^{2}\right] &=\mathbb{E}\left[(t-f+f-\hat{f})^{2}\right] \\ &=\cdots \\ &=\mathbb{E}\left[\left(f-\mathbb{E}[\hat{f}]^{2}\right)^{2}\right]+\mathbb{E}\left[(\mathbb{E}[\hat{f}]-\hat{f})^{2}\right]+\mathbb{E}[\epsilon] \end{aligned}$

<br></br>



## BootStrapping
<hr/>
학습데이터가 있을 때 sub sampling을 통해 데이터를 나누는 것이다.    


<br><br/>



## Bagging & Boosting
<hr/>
Bagging (Bootstrapping aggregating) : 데이터를 bootstraping 하여 여러개의 모델로 독립적으로 학습하는 방식이다.   
Dectrete한 예측값은 vote, 연속 데이터는 평균으로 결과를 도출한다.    

Related : [Random Forest](https://ko.wikipedia.org/wiki/%EB%9E%9C%EB%8D%A4_%ED%8F%AC%EB%A0%88%EC%8A%A4%ED%8A%B8)

Boosting : Bagging과 동일하나 각 모델이 독립적인 형태가 이닌 Sequential하게 배치하여 여러 개의 weak learner 를 통해 1개의 strong learner를 만드는 방식이다.      




<br><br/>