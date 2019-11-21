---
title: "딥러닝(2) - Multi Layer Network, Activate Function, Loss Function"
categories:
  - Deep Learning
tags:
  - Activate Function
  - Loss Function
  - Deep Learning
comments: true
---

# 1. 신경망 (Neural Network)
> 퍼셉트론이 가중치를 직접 수동으로 설정하는 작업을 했다는 한계가 있었는데 이를 해결할 방법이 바로 신경망이다. 
> 딥러닝을 이야기할 때 '자동으로 알아서 학습하는' 이라는 말을 많이 한다.
> 알아서 가중치 값을 설정하고 조정하는 것이 자동으로 학습한다는 말과 동일하며 이것이 신경망의 가장 큰 특징 중 하나이다.

## 1.1. 다중 퍼셉트론과 신경망 (Multi Layer Perceptron & Neural Network)
- 단일 퍼셉트론 : 여러 개의 신호가 들어오면 이를 조합하여 다음으로 신호를 보낼지 말지 **유무**(0 또는 1)를 결정한다. 
- 다중 퍼셉트론 : 단일 퍼셉트론을 발전 시킨 개념으로 하나의 단일 퍼셉트론에 여러 신호가 들어오면, 다음 퍼셉트론에 보낼 신호의 **강도**를 결정한다. XOR과 같은 비선형 분리도 가능해진다. 
- 신경망 구성
  - Input(입력층)
  - Hidden(은닉층)
  - Output(출력층)

<center><img src="https://mioscode.github.io/assets/images/dl2/multi_layer_network.png" width="50%"></center>

## 1.2. 활성화 함수 (Activate Function)
> 불필요한 모든 자극(Input)에 반응(Output) 한다면 제대로 된 학습이 되었다고 할 수 없다. 
다양하고 수많은 Input 중에 의미 있는 정보만 다음 Perceptron으로 보내야 좋은 신경망이라 할 수 있다. 
이때 다음 퍼셉트론으로 전달하거나 출력하는 값를 정하는(변환하는) 방법이 활성화 함수이다. 
활성화 함수는 모든 입력값을 연산 후 그대로 출력값을 내보내지 않고 변환시켜 내보낸다.

- 단일 퍼셉트론 : 여러 개의 신호가 들어오면 이를 조합하여 다음으로 신호를 보낼지 말지 **유무**(0 또는 1)를 결정한다. 
  - **step function(임계값을 넘어섰을 때 출력을 1로 하는 함수)을 활성화 함수로 사용한 모델**
- 다중 퍼셉트론 : 단일 퍼셉트론을 발전 시킨 개념으로 하나의 단일 퍼셉트론에 여러 신호가 들어오면, 다음 퍼셉트론에 보낼 신호의 **강도**를 결정한다. XOR과 같은 비선형 분리도 가능해진다. 
  - **층이 여러개이며 sigmoid function을 활성화 함수로 사용하는 네트워크**

### 1.2.1. Linear Activation Function (=Linear Function)
- 선형함수는 복잡한 신경망을 쌓을 수 없다.
- 선형함수는 Backpropagation(역전파)이 불가능하다. (왜냐하면 미분값은 상수이기 때문에 입력값과 상관없는 결과를 얻게된다)
> **왜 비션형 함수를 사용해야하는가?**
선형함수를 사용했을 때는 은닉층을 사용하는 이점이 없기 때문이다. 
다시 말해 선형함수를 여러층으로 구성한다 하더라도 이는 선형함수를 세번 연속 반복한 것에 지나지 않는다는 의미와 같기 때문이다. 
$y = ax$라는 선형함수가 있다고 한다면 이 것을 3층으로 구성하면 $y = a(a(a(x)))$ 와 동일한 것으로 이는 $y = a^3(x)$와 같다. 굳이 은닉층 없이 선형함수로 네트워크를 구성하는 것은 의미가 없다는 뜻이다. 
1.2.2.부터는 모두 비선형함수이다.

<center><img src="https://mioscode.github.io/assets/images/dl2/step_function.png" width="50%"></center>

### 1.2.2. Binary Step Function (=Step Function)
- 임계치를 기준으로 출력을 해준다.
- 0보다 크면 1 / 0보다 작으면 0으로 분류를 해준다.
- 이 함수로는 비선형 문제, 다중 분류 문제를 해결할 수 없다.

<center><img src="https://mioscode.github.io/assets/images/dl2/step_function.png" width="50%"></center>

### 1.2.3. Sigmoid Function
- 미분 식이 단순한 형태를 가진다.
- 출력값의 범위가 0과 1로 제한되어 Exploding Gradient 문제를 방지한다.
- 하지만 역으로 Vanishing Gradiend 문제가 발생한다.
- exp 연산 비용이 크다.

<center><img src="https://mioscode.github.io/assets/images/dl2/sigmoid_function.png" width="50%"></center>

$$s(t)=\frac{1}{1+e^{-t}}$$

### 1.2.4. Tahn Function
- 장단점이 sigmoid와 유사하다.
- Sigmoid와 같이 잘 사용하지 않는 함수이다.

<center><img src="https://mioscode.github.io/assets/images/dl2/tahn_function.png" width="50%"></center>

### 1.2.5 Relu Function
- 선형 함수의 개선된 버전이다. ( Rectified Linear Function )
- CNN에서 좋은 성능을 보였고, 현재 딥러닝에서 가장 많이 사용하는 활성화 함수이다.
- 실제 뇌와 같이 모든 정보에 반응하는 것이 나닌 일부 정보에 대해 무시와 수용을 통해 보다 효율적인 결과를 낸다.
- 미분값이 상수가 아닌 함수이며 backpropagation을 허용한다.

<center><img src="https://mioscode.github.io/assets/images/dl2/relu_function.png" width="50%"></center>

### 1.2.6 Swish & Leacky ReLU & ELU

<center><img src="https://mioscode.github.io/assets/images/dl2/swish_function.png" width="50%"></center>

<center><img src="https://mioscode.github.io/assets/images/dl2/leacky_relu_function.png" width="50%"></center>

<center><img src="https://mioscode.github.io/assets/images/dl2/elu_function.png" width="50%"></center>

## 1.1. 신경망 용어 정의
- 타깃(target) : 기대 출력을 의미합니다.
- 매핑(mapping) : 입력과 타깃의 관계로 입력을 representation로 변환, 연관시키는 것을 의미합니다.
- 가중치(weight) : 머신 러닝, 딥러닝 모두 결국은 가장 효율적인 식을 찾는 것이 목표이며, 이런 식 또는 식에 필요한 파라미터를 칭합니다.
- 손실함수(loss function) : 타깃과 출력값의 차이를 계산하는 함수입니다
- 역전파(Backpropagation) : 손실함수의 결과를 개선하기 위해서 다시 결과에서부터 가중치를 수정하는 과정입니다. 이를 옵티마이저(optimizer)가 담당합니다.

## 1.2. 신경망의 훈련 순서
1. 데이터를 입력합니다.
2. 여러 층을 통해 예상 결과값을 만듭니다. (매핑)
3. 실제 값과 비교해서 그 차이를 구합니다. (타깃과 손실함수)
4. 차이를 줄이기 위한 방법으로 앞의 층들의 가중치를 수정해줍니다. (역전파)
5. 이 방법의 반복으로 규칙을 계속 개선합니다.

<center><img src="https://mioscode.github.io/assets/images/dl2/flowchart.jpg" width="50%"></center>

# 2. Loss Function


# Reference
- https://subinium.github.io/Keras-1/