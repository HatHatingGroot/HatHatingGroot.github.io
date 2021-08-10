---
title: "[DL/ML]Gradient Descent Methods"
categories:
  - 
tags:
  - 
last_modified_at: 2021-08-10T00:00:00-00:00
---


## Summary 🤙
<hr/>
Gradient Descent는 다음으로 간단히 분류할 수 있다.    

* Stochastic Gradient Descent : 한개의 샘플로부터 gradient를 계산하여 업데이트   
* Mini-batch Gradient Descent : 데이터의 subset으로 gradient를 계산하여 업데이트   
* Batch Gradient Descent : 모든 데이터로 gradient를 계산하여 업데이트    

> 배치 사이즈가 크면 sharp minimizers에 수렴하는 경향이 있고, 작으면 flat minimizer에 수렴하는 경향이 있다.
>  [On Large-batch Training for Deep Learning Generalization Gap and Sharp Minima, 2017](https://arxiv.org/abs/1609.04836)
<br><br/>


## Index 👀       
  * [Stochastic Gradient Descent](#stochastic-gradient-descent)
  * [Momentum](#momentum)
  * [Nesterov accelerated gradient](#nesterov-accelerated-gradientnag)
  * [Adagrad](#adagrad)
  * [Adadelta](#adadelta)
  * [RMSprop](#rmsprop)
  * [Adam](#adam)

<br/>


## Stochastic Gradient Descent
<hr/>

$$ W_{t+1} =  W_t - \eta g_t $$    

가장 기본적인 Gradient Descent의 방법이다.   

>이때 Learning Rate를 나타내는 hyperparameter $\eta$를 적절히 설정해는 것이 중요하다.    

<br><br/>

## Momentum
<hr/>

$$\begin{aligned} a_{t+1} & \leftarrow \beta a_{t}+g_{t} \\ W_{t+1} & \leftarrow W_{t}-\eta a_{t+1} \end{aligned}$$

이전 학습의 관성을 유지시켜 Gradient가 변하더라도 이전 정보를 활용한다.   
$\beta$는 momentum의 값을 나타내는 hyper parmeter이다.    
$a_t$는 accumulation으로서 가중치를 조정하는 데 실제로 영향을 미친다.   

> 다만 관성으로 인해 멈춰야할 지점(local minima)에 converge하지 못하는 경우가 생길 수 있다.

<br><br/>

## Nesterov accelerated gradient(NAG)
<hr/>

$$\begin{aligned} a_{t+1} & \leftarrow \beta a_{t}+\nabla \mathcal{L}\left(W_{t}-\eta \beta a_{t}\right) \\ W_{t+1} & \leftarrow W_{t}-\eta a_{t+1} \end{aligned}$$

Momentum의 단점을 보완할 수 있는 방법이다. Momentum은 관성과 gradient를 독립적으로 계산하지만, NAG는 momentum만큼 먼저 이동한 뒤 gradient를 계산한다. 

> 따리서 momentum의 장점은 유지하면서, 멈춰야할 지점에 멈추는데에 훨씬 용이하다.


<br><br/>


## Adagrad
<hr/>

$$W_{t+1}=W_{t}-\frac{\eta}{\sqrt{G_{t}+\epsilon}} g_{t}$$
$G_t$ : sum of gradient squares    
$\epsilon$ : for numerical stability    

Adaptive Gradient로 파라미터 값들의 변화량에 의해 Learning Rate를 조절하는 방법으로, 변화량이 많은 파라미터는 LearningRate를 감소시키고, 적은 파라미터는 LearningRate를 증가시키도록 유도할 수 있다.    


>단, 학습이 진행될 수록 $G_t$ 값이 증가하여 LearningRate가 0에 가까워지는 문제(__monotonically decreasing__)가 발생할 수 있다.     

<br><br/>



## Adadelta
<hr/>

$$
\begin{aligned}
G_{t} &=\gamma G_{t-1}+(1-\gamma) g_{t}^{2} \\
W_{t+1} &=W_{t}-\frac{\sqrt{H_{t-1}+\epsilon}}{\sqrt{G_{t}+\epsilon}} g_{t} \\
H_{t} &=\gamma H_{t-1}+(1-\gamma)\left(\Delta W_{t}\right)^{2}
\end{aligned}
$$

$G_t$ : EMA of gradient squares    
$H_t$ : EMA of difference squares    


Adagrad의 문제점을 보완하기 위해 [EMA(exponential moving average)](https://ko.wikipedia.org/wiki/%EC%9D%B4%EB%8F%99%ED%8F%89%EA%B7%A0#cite_note-3)를 취한다. 

결과적으로는 최근에 gradient에 따라 반대로 학습률을 조정하는 것이다.

>특징은 명시적인 Learning Rate가 없다는 점이다.     
>따라서 커스텀 영역이 적어 실제로는 잘 사용되지 않는다.     


<br><br/>


## RMSprop
<hr/>

$$
\begin{aligned}
G_{t} &=\gamma G_{t-1}+(1-\gamma) g_{t}^{2} \\
W_{t+1} &=W_{t}-\frac{\eta}{\sqrt{G_{t}+\epsilon}} g_{t}
\end{aligned}
$$

$G_t$ : EMA of gradient squares  

논문을 통해 소개된 방법론은 아니고 Geoff Hinton의 강의에서 소개된 독특한 방법이다.    
>특징은 Adadelta에 Learning rate가 추가되었다는 것이다.     

<br><br/>




## Adam
<hr/>

$$
\begin{aligned}
m_{t} &=\beta_{1} m_{t=1}+\left(1-\beta_{1}\right) g_{t} \\
v_{t} &=\beta_{2} v_{t-1}+\left(1-\beta_{2}\right) g_{t}^{2} \\
W_{t+1} &=W_{t}-\frac{\eta}{\sqrt{v_{t}+\epsilon}} \frac{\sqrt{1-\beta_{2}^{t}}}{1-\beta_{1}^{t}} m_{t}
\end{aligned}
$$

$m_t$ : Momentum    
$v_t$ : EMA of gradient squares    

Adaptive Moment Estimation      

> 앞서 소개된 Momentum과 Adaptive, 이 두 개념을 잘 용합한 방법이다. 


<br><br/>

