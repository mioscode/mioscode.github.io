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

<center><img src="https://mioscode.github.io/assets/images/dl2/linear_function.png" width="50%"></center>

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

($e^{-t}$ : 자연로그의 역함수인 지수 함수)
($e$ : 오일러 상수; 근사값=$2.718281828459...$)

### 1.2.4. Tahn Function
- 장단점이 sigmoid와 유사하다.
- Sigmoid와 같이 잘 사용하지 않는 함수이다.

<center><img src="https://mioscode.github.io/assets/images/dl2/tahn_function.png" width="50%"></center>

### 1.2.5 Relu Function
- 선형 함수의 개선된 버전이다. ( Rectified Linear Function )
- CNN에서 좋은 성능을 보였고, 현재 딥러닝에서 가장 많이 사용하는 활성화 함수이다.
- 실제 뇌와 같이 모든 정보에 반응하는 것이 나닌 일부 정보에 대해 무시와 수용을 통해 보다 효율적인 결과를 낸다.
- 미분값이 상수가 아닌 함수이며 backpropagation을 허용한다.
- 비선형함수이고 도함수를 가지며 backpropagation을 허용한다.
  - 도함수 : (유)도함수, 미분 원하는 함수를 미분계수 구하는 식에 a대신 x로 넣었을 떄 모두 유도 된 함수를 도함수

<center><img src="https://mioscode.github.io/assets/images/dl2/relu_function.png" width="50%"></center>

### 1.2.6 Swish & Leacky ReLU & ELU

<center><img src="https://mioscode.github.io/assets/images/dl2/swish_function.png" width="50%"></center>

<center><img src="https://mioscode.github.io/assets/images/dl2/leaky_relu_function.png" width="50%"></center>

<center><img src="https://mioscode.github.io/assets/images/dl2/elu_function.png" width="50%"></center>

## 1.3. 다차원 배열 연산
- 앞서 설명한 가중치의 값을 보다 편하게 하기 위해서 행렬 연산을 이용하는 것이다. 한 두개의 신경망 층은 인간이 계산할 수 있을지 모르겠지만 그 이상의 수 많은 차원의 수많은 뉴런층으로 구성된 신경망의 weight를 일일이 계산하는 것은 불가능한 일이다. 이를 컴퓨팅적으로도 쉽게 할 수 있도록 돕는 것이 행렬 연산이다. 
- 여기서 중요한 개념은 다차원 배열(행렬) 간의 곱 연산이다. 행렬의 곱이 성립하기 위해서는 기본적으로 아래의 조건을 따라야 한다. 
  $$a \times b  *  c \times d  =  a \times d \ (when \ b = c )$$
  - $*$(곱 연산)의 안쪽에 있는 $b$와 $c$의 값이 일치해야 하며, 곱 연산을 했을 때 결과값은 $a \times d$의 형태로 나온다는 점이다. 이는 한쪽이 1차원 배열일 때도 동일하게 적용된다.

### 예제
```python
import numpy as np

X = np.array([[1,2]])
print(X.shape)

W = np.array([[1,2,3], [4,5,6]])
print(W.shape)

Y = np.dot(X, W)
print(Y)
```

<center><img src="https://mioscode.github.io/assets/images/dl2/times.png" width="50%"></center>

- 이런식으로 어떤 층의 노드(뉴런)의 개수가 몇 개가 되든 (위에서는 3개) 한 번의 연산으로 이 작업을 빠르게 수행할 수 있다. 행렬의 내적은 신경망에서 아주 중요한 개념인 것이다. 층이 몇 개이든 이와 같은 방법으로 가중치를 계속해서 계산해 나가는 것이라고 보면 된다.

## 1.4. 신경망 용어 정의
- 타깃(target) : 기대 출력
- 매핑(mapping) : 입력과 타깃의 관계로 입력을 representation로 변환, 연관시키는 것
- 가중치(weight) : 머신 러닝, 딥러닝 모두 결국은 가장 효율적인 식을 찾는 것이 목표이며, 이런 식 또는 식에 필요한 파라미터
- 손실함수(loss function) : 타깃과 출력값의 차이를 계산하는 함수
- 역전파(Backpropagation) : 손실함수의 결과를 개선하기 위해서 다시 결과에서부터 가중치를 수정하는 과정,  이를 옵티마이저(optimizer)가 담당

## 1.5. 신경망의 훈련 순서
1. 데이터를 입력한다.
2. 여러 layer를 통해 예상 결과값을 만든다. (매핑)
3. 실제 값과 비교해서 그 차이를 구한다. (타깃과 손실함수)
4. 차이를 줄이기 위한 방법으로 앞의 layer들의 가중치를 수정해준다. (역전파)
5. 이 방법의 반복으로 규칙을 계속 개선한다.

<center><img src="https://mioscode.github.io/assets/images/dl2/flowchart.png" width="50%"></center>

## 1.6. 신경망 3층 구현하기
```python
def init_network():
    network = {}
    network['W1'] = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
    network['b1'] = np.array([0.1, 0.2, 0.3])
    network['W2'] = np.array([[0.1, 0.4], [0.2, 0.5], [0.3, 0.6]])
    network['b2'] = np.array([0.1, 0.2])
    network['W3'] = np.array([[0.1, 0.3], [0.2, 0.4]])
    network['b3'] = np.array([0.1, 0.2])

    return network

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def relu(x):
    return np.maximum(0, x)

def forward(network, x):
    W1, W2, W3 = network['W1'], network['W2'], network['W3']
    b1, b2, b3 = network['b1'], network['b2'], network['b3']

    a1 = np.dot(x, W1) + b1
    z1 = sigmoid(a1)
    a2 = np.dot(z1, W2) + b2
    z2 = sigmoid(a2)
    a3 = np.dot(z2, W3) + b3
    y = a3

    return y

def main():
    network = init_network()
    x = np.array([1.0, 0.5])
    y = forward(network, x)
    print(y)

if __name__ == '__main__':
    main()
```

# 2. Loss Function
> Neural Net을 거쳐서 나온 결과값과 실제 결과 값의 차이를 계산하는 함수 

<center><img src="https://mioscode.github.io/assets/images/dl2/loss_function.png" width="50%"></center>

## 2.1. 손실함수를 왜 사용하는가?
1. Loss Function이 있어야 학습이 올바르게 진행되는지를 알 수 있다.
2. Loss function은 연속적으로 변화되는 값을 표시한다.
  - 정답률을 파라미터로 사용하면,
  - 100개 중 33개가 정답으로 판명된다면 정답률은 33%이다. 
  - 만약 정확도를 개선한다 하더라도 33.32%와 값이 연속적인 값으로 변화하지 않는다.

## 2.2. 손실함수 종류
### 2.2.1. MSE

$$MSE = \frac{1}{n} \sum_{i=1}^N (y_i-\tilde{y}_i)^2$$

### 2.2.2. Cross Function

$$\mathcal{L} (y_i-\tilde{y}_i) = - \sum_{i=1}^N y_i \log \hat{y_i}$$

## 2.3. 손실함수 테스트

1. Mean Squared Error 를 python으로 구현 해보자.
2. Cross Entropy Error를 python을 구현 해보자.
3. 실제 테스트를 해보자.


# Reference
- <https://subinium.github.io/Keras-1/>
- <https://sacko.tistory.com/17?category=632408>
- <https://sacko.tistory.com/37?category=632408>