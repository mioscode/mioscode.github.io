# Neural Network

## 개념
Input(입력층), Hidden(은닉층), Output(출력층)
![](/Users/somi.han/Documents/Deep%20Learning/300px-Colored_neural_network.svg.png)

## Activation Function

출력 값 결정하게 하는 역할, 변환기
AND, OR, NAND, XOR Gate 다음 단계

### 계단 함수 (Step Function)

![](/Users/somi.han/Documents/Deep%20Learning/download.png)

### 시그모이드 함수 (Sigmoid Function)

극단적인 계단 함수 대체하여 사용

![](/Users/somi.han/Documents/Deep%20Learning/sigmoid.png)

# 오차 역전파 (Error Backpropagatin)

* 순전파(Forwardpropagation) : 순차적으로 Input -> Output 가중치를 업데이트하면서 활성화 함수를 통해서 결과값을 가져오는 것

* 역전파 : 결과 값을 통해서 다시 역으로 input 방향으로 오차를 다시 보내며 가중치를 재업데이트 하는 것이다. 물론 결과에 영향을 많이 미친 노드(뉴런)에 더 많은 오차를 돌려줄 것이다.

![](/Users/somi.han/Documents/Deep%20Learning/H1KsG.png)

* 한번 역전파를 실행하는 것을 1 epoch 주기라고함
* epoch를 늘릴 수록 가중치가 계속 업데이트(학습)되면서 점점 오차가 줄어나가는 방법
 
![](/Users/somi.han/Documents/Deep%20Learning/997C7A3359EEF5CA1F.png)