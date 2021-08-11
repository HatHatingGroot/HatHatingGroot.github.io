---
title: "[DL/ML]CNN - Intro"
categories:
  - DL-ML
tags:
  - DeepLearning
  - CNN
  - Convolution
  - ConvolutionNeuralNetwork
  - Stride
  - Padding
  - 1x1Convolution
last_modified_at: 2021-08-11T00:00:00-00:00
---


## Summary 🤙
<hr/>
CNN(Convolution Neural Network)은 일정한 크기의 파라미터(filter, kernel)를 옮겨가며 도장을 찍듯이 옮겨가며 합성곱(Convolution)하는 형태의 뉴럴 네트워크다. 

> 최근의 동향은 레이어를 증가시키고 파라미터를 줄이는 것이다.     


<br><br/>


## Index 👀       
  * [Channel](#channel)
  * [Stride](#Stride)
  * [Padding](#Padding)
  * [Layer(Convolution, pooling, fully connected)](#layerConvolution-pooling-fully-connected)
  * [Accumualte the number of parameters](#accumualte-the-number-of-parameters)
  * [1x1Convolution](#1x1-Convolution)
  
<br><br/>


## Channel  
<hr/>

Channel이란 이미지의 한 픽셀을 구성하는 메타 정보의 차원이라고 할 수 있다.   
예를 들어 100(높이)x80(너비) 픽셀의 컬러 이미지라면 채널은 3이 되어 데이터의 shape는 (3, 100, 80) 이 될 것이다.     
만약 흑백 사진이라면 (2, 100, 80)이 될 것이다.


<br></br>

   

## Stride  
<hr/>

Stride는 kernel 이 이동하는 간격을 의미한다. 

<br></br>

   

## Padding  
<hr/>

kernel을 이미지의 맨처음부터 모두 스캔하게 하는 등의 특정 목적이 있을때 이미지 외부에 임의의 값(0)을 넣어 kernel이 스캔하는 범위를 조절할 수 있다.

<br></br>
   



## Layer(Convolution, pooling, fully connected)  
<hr/>

* Convolution Layer : 하나 또는 여러개의 필터(kernel)로 이루어진 레이어이다. 필터의 갯수만큼의 채널이 만들어진다.(Feature Map||Activation Map)
* Pooling Layer
  * Max pooling : 특정 영역에서 가장 큰값만 취한다.
  * Down sampling : 상대적으로 이미지를 줄여서 같은 사이즈의 kernel이 연산되면 좀더 추상적인 (윤곽에서 특정 사물의 의미를 담는 크기와의 연산) 데이터를 학습할 수 있게 된다.
* Fully connected : MLP개념과 유사하며 분류를 수행한다.



<br></br>



## Accumualte the number of parameters  
<hr/>

CNN이 점차 지향하는 바는 파라미터를 줄이고 레이어를 늘리는 것에 있다고 앞서 언급한 바 있다. 

파라미터의 갯수는 필터사이즈 x 채널수 x 필터수(출력 채널 수)로 구할 수 있다.


<br></br>



## 1x1Convolution
<hr/>

1x1 크기의 필터를 여러개 Convolution 함으로써 채널 Dimension을 감소시킬 수 있다. (입력 채널수 > 필터의 갯수)      
따라서 파라미터의 갯수를 줄이기 위해 사용된다.   


<br></br>


## Refrence   
<hr/>

* https://89douner.tistory.com/57