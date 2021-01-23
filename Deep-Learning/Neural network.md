# 신경망 기초

## 인공신경망(Artificial neural network, ANN)

<details>
<summary>자세히</b></summary>   
<div markdown="1">   

+ 생물학의 신경망에서 영감을 얻은 통계학적 학습 알고리즘
   + 사람 뇌의 정보처리(뉴런)를 모방   
   
      → 퍼셉트론 고안

+ 구조
   + 노드들의 그룹으로 연결되어있음.
   + 여기서 노드(원)은 인공 뉴런을 나타내고, 화살표는 하나의 뉴런의 출력에서 다른 하나의 뉴런으로의 입력을 나타냄.   
   
      > <img src="https://user-images.githubusercontent.com/72974863/105278335-911bf180-5be8-11eb-9a10-11c14604d6d8.png">   

      > [그림 출처](https://ko.wikipedia.org/wiki/%EC%9D%B8%EA%B3%B5_%EC%8B%A0%EA%B2%BD%EB%A7%9D)

+ 다양한 모델이 존재함
   + 전방(forward) 신경망, 순환(recurrent) 신경망, 얕은(shallow) 신경망, 깊은(deep) 신경망
   
   + 결정론적(deterministic) 신경망 : **모델의 매개변수와 조건**에 의해 **출력이 완전히 결정**되는 신경망
   + 확률론적(stochastic) 신경망 : 고유의 임의성을 가지며 매개변수와 조건이 같더라도 **다른 출력**을 가지는 신경망

</div>
</details>


## 퍼셉트론(Perceptron)

<details>
<summary> 자세히 </summary>   
<div markdown="1"> 
   
+ 구조 : node, weight, layer과 같은 새로운 개념의 구조 도입
   > <img src="https://user-images.githubusercontent.com/72974863/105280727-d131a300-5bed-11eb-9c2e-57cdbd438758.png">   
   
   > [그림 출처](https://en.wikipedia.org/wiki/Perceptron) 

+ 동작 
   + 선형 연산 → 비선형 연산
      + **선형** : 입력(특징)값과 가중치를 곱하고 더해서 s를 구함
      + **비선형** : 활성함수를 적용
      
+ 원시적 신경망으로, 현대 인공신경망의 중요한 구성 요소가 됨.

+ 일반적인 분류기의 학습과정 ✨
   + 1단계 : **과업 정의**와 분류 과정의 수학적 정의(**가설 설정**)   
      > 퍼셉트론 이용한다면   
      
   + 2단계 : 해당 분류기의 **목적함수 정의**   
      + 목적함수 <a href="https://www.codecogs.com/eqnedit.php?latex=J(\mathbf{w})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J(\mathbf{w})" title="J(\mathbf{w})" /></a> 상세 설계
         + 조건 1 : <a href="https://www.codecogs.com/eqnedit.php?latex=J(\mathbf{w})\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J(\mathbf{w})\geq&space;0" title="J(\mathbf{w})\geq 0" /></a>   
         + 조건 2 : **w**가 최적이면(모든 샘플을 맞추면) <a href="https://www.codecogs.com/eqnedit.php?latex=J(\mathbf{w})=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J(\mathbf{w})=&space;0" title="J(\mathbf{w})= 0" /></a>   
         + 조건 3 : 틀리는 샘플이 많은 **w**일수록 <a href="https://www.codecogs.com/eqnedit.php?latex=J(\mathbf{w})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J(\mathbf{w})" title="J(\mathbf{w})" /></a>는 큰 값을 가짐    
                  
                  
          > <a href="https://www.codecogs.com/eqnedit.php?latex=J(\mathbf{w})=\sum_{x_k&space;\in&space;Y}-y_k&space;(\mathbf{w}^T&space;\mathbf{x}_k)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J(\mathbf{w})=\sum_{x_k&space;\in&space;Y}-y_k&space;(\mathbf{w}^T&space;\mathbf{x}_k)" title="J(\mathbf{w})=\sum_{x_k \in Y}-y_k (\mathbf{w}^T \mathbf{x}_k)" /></a>   
      
          > Y는 **w**가 틀리는 샘플의 집합
         
          > 상세 조건 1,2,3 모두 만족 → 퍼셉트론의 목적함수로 적합    
      
   + 3단계 : **목적함수를 최소화하는 파라미터**를 찾기 위한 **최적화 방법 수행**   
      > 경사하강법을 통해 반복 탐색해서 극값을 찾음
   

+ 퍼셉트론 학습 알고리즘
   + stochastic version
      + 샘플 순서 섞고, 틀린 샘플 발생하는 즉시 매개변수 갱신  
   
      + 실험으로 더 좋은 성능이 입증 → 현대 기계학습은 이 버전을 채택하였음.
      
   + batch version
      + batch로 확장해도 동일(틀린샘플을 모두 모아 한꺼번에 매개변수 갱신)
   
   
   + 선형 분류기(linear classifier) 한계
      > 즉, 직선 하나로 나눈 영역만 표현가능함.
      
      > 예를 들어, XOR 문제에서 75% 정확도 한계가 존재 (퍼셉트론으로 XOR 게이트 표현 X) ❗

</div>
</details>

## 다층 퍼셉트론
+ 쉽게 생각하면, **여러 퍼셉트론을 쌓은 것** 

+ **핵심 아이디어** ✨
   + **은닉층**
      > 원래 특징 공간을 분류하는 데 훨씬 **유리한 새로운 특징 공간**으로 변환 ❗
      
   + **시그모이드 활성함수** 도입
      > 퍼셉트론에서 경성(hard) 의사결정에 해당하는 계단함수를 활성함수로 사용하였음 ❗   
      
      > 반면, 다층 퍼셉트론은 연성(soft) 의사결정이 가능한 시그모이드 함수를 사용. (더 융통성있게 의사결정 가능 ❗)
      
   + **오류 역전파 알고리즘** 사용
      > 역방향으로 진행하면서 한번에 한 층씩 gradient 계산하고 가중치 갱신하는 알고리즘 ❗  
      
+ 퍼셉트론 2개의 병렬 결합을 통해 XOR 문제 해결 가능 ❗
   > 원래 공간을 **새로운 특징 공간으로 변환** (새로운 특징 공간에서 선형 분리 가능)
      
   > 단층 퍼셉트론으로 표현하지 못한 것을 층을 하나 늘려 구현할 수 있음.
   
   > 즉, **펴셉트론의 병렬결합**을 통해 **선형 분리** 
      
   + 다층 퍼셉트론의 용량
      > **p개의 퍼셉트론을 결합**하면, **P차원 공간으로 변환** 
      
      > <img src="https://user-images.githubusercontent.com/72974863/105579024-37255280-5dc7-11eb-8baf-3392ffb81a24.png" width="70%" height="70%">   
            
      > [그림 출처 & 참고하기 👍](http://www.aistudy.com/neural/MLP_kim.htm) 
      
+ **활성함수**       
   + **활성함수**에 따른 **다층 퍼셉트론의 공간 분할 능력 변화** (경성 부분 변화) ⭐   
   
   + 다양한 활성함수 ✨   
   
   > <img src="https://user-images.githubusercontent.com/72974863/105579188-4f49a180-5dc8-11eb-8795-4b1cb658216a.png" width="120%" height="120%">   
   
   > [참고하기 - wiki](https://en.wikipedia.org/wiki/Activation_function)   
   
   + 대표적인 비선형 함수로 **s자 모양의 sigmoid**를 사용
   + logistic sigmoid, tanh : 위의 그림 기준으로 x의 계수가 커질수록 계단함수에 가까워짐
   
   + 활용 예 
      + 퍼셉트론 - 계단함수
      + 다층 퍼셉트론 - logistic sigmoid & tanh (logistic sigmoid 많이 사용)
         > s자 모양의 넓은 포화곡선은 오류역전파(경사도 기반 학습)를 어렵게 함 💥
         > 따라서, 깊은 신경망에서 ReLU 활용 ⭐   
         
      + 심층학습 - ReLU(Rectified Linear Activation)
   