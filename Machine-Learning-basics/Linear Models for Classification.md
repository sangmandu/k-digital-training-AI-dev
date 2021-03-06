# 선형 분류(Linear Classification)

+ 분류 목표 : 입력벡터 **x**를 **K**개의 가능한 클래스 중 하나의 클래스로 할당

+ 분류를 위한 결정이론 
   + **확률적 모델(probabilistic model)**
      + 생성모델(generative model)   
      
         > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}|\mathcal{C}_k),&space;p(\mathcal{C}_k)&space;\rightarrow&space;p(\mathcal{C}_k|\bf&space;x)" title="p({\bf x}|\mathcal{C}_k), p(\mathcal{C}_k) \rightarrow p(\mathcal{C}_k|\bf x)" /> 클래스의 사후확률 (using 베이즈 정리) 또는 <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}|\mathcal{C}_k)" title="p({\bf x}|\mathcal{C}_k)" /> 직접 모델링   
         
      + 식별모델(discriminative model)   
      
         > <img src="https://latex.codecogs.com/gif.latex?p(\mathcal{C}_k|{\bf&space;x})" title="p(\mathcal{C}_k|{\bf x})" /> 직접 모델링
      
   + **판별함수(discriminant model)** 
   
      > 확률 계산 없이 입력 **x**를 클래스로 할당하는 판별함수 구하기(찾기)
      
## 판별함수 (Discriminant model)   

+ 선형함수에 관한 판별함수에 대해 생각하자.

+ 두개의 클래스에 대한 선형판별함수
   > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})={\bf&space;w^Tx}&plus;w_0" title="y({\bf x})={\bf w^Tx}+w_0" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\bf&space;w" title="\bf w" /> : wight vector   
      
   > <img src="https://latex.codecogs.com/gif.latex?w_0" title="w_0" /> : bias   
   
   > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})&space;\ge&space;0" title="y({\bf x}) \ge 0" />이면 클래스 1로 판별, <0이면 클래스 2로 판별   
   
+ **결정 경계(decision boundary)**
   + y(**x**)=0을 만족하는 **x**의 집합 (**x**가 D차원의 입력벡터일 때, D-1차원의 hyperplane)
   
   + 결정 경계면 위 <img src="https://latex.codecogs.com/gif.latex?{\bf&space;x}_A,&space;{\bf&space;x}_B" title="{\bf x}_A, {\bf x}_B" />   
   
      > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x}_A)=y({\bf&space;x}_B)=0" title="y({\bf x}_A)=y({\bf x}_B)=0" />   
      
      > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;w^T}({\bf&space;x}_A-{\bf&space;x}_B)=0" title="{\bf w^T}({\bf x}_A-{\bf x}_B)=0" /> → 즉, <img src="https://latex.codecogs.com/gif.latex?w^{T}" title="w^{T}" />는 결정경계면에 수직   
      
   + 원점에서 결정 경계면까지의 거리
   
      + 벡터 x⊥ : 원점에서 결정 경계면에 대한 사영(projection)일 때 (아래 그림 참고)
         
         > <img src="https://latex.codecogs.com/gif.latex?r\frac{{\bf&space;w}}{\|&space;{\bf&space;w}\|}&space;=&space;{\bf&space;w}_{\perp}" title="r\frac{{\bf w}}{\| {\bf w}\|} = {\bf w}_{\perp}" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;w}_{\perp})&space;=&space;0&space;\Rightarrow&space;{\bf&space;w}^T{\bf&space;w}_{\perp}&space;&plus;&space;w_0&space;=&space;0" title="y({\bf w}_{\perp}) = 0 \Rightarrow {\bf w}^T{\bf w}_{\perp} + w_0 = 0" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?\Rightarrow&space;\frac{{\bf&space;w}^T{\bf&space;w}}{\|{\bf&space;w}\|}r&space;&plus;&space;w_0&space;=&space;0" title="\Rightarrow \frac{{\bf w}^T{\bf w}}{\|{\bf w}\|}r + w_0 = 0" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?\Rightarrow&space;\|{\bf&space;w}\|&space;r&space;&plus;&space;w_0&space;=&space;0" title="\Rightarrow \|{\bf w}\| r + w_0 = 0" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?\Rightarrow&space;r&space;=&space;-\dfrac{w_0}{\|{\bf&space;w}\|}" title="\Rightarrow r = -\dfrac{w_0}{\|{\bf w}\|}" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?w_0<0" title="w_0<0" />이면, 결정 경계면은 원점으로부터 **w**가 향하는 방향으로 멀어져있음.
         
         > <img src="https://latex.codecogs.com/gif.latex?w_0>0" title="w_0>0" />이면, 결정 경계면은 원점으로부터 **w**가 반대 방향으로 멀어져있음.
         
         > 즉, <img src="https://latex.codecogs.com/gif.latex?w_0" title="w_0" />는 결정 경계면 위치 결정 ❗   
         

         
      + x⊥ : 임의의 한점 **x**의 결정 경계면에 대한 사영일 때
          
         > y(**x**)는 **x**와 결정 경계면 사이의 부호화된 거리에 비례
          
         > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;x}={\bf&space;x}_\perp&space;&plus;&space;r\dfrac{\bf&space;w}{\|{\bf&space;w}\|}" title="{\bf x}={\bf x}_\perp + r\dfrac{\bf w}{\|{\bf w}\|}" />  
          
         > 정리하면,   
          
         > <img src="https://latex.codecogs.com/gif.latex?r=\dfrac{y({\bf&space;x})}{\|{\bf&space;w}\|}" title="r=\dfrac{y({\bf x})}{\|{\bf w}\|}" />
         
         > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})&space;>&space;0" title="y({\bf x}) > 0" />이면, **x**는 결정 경계면 기준으로 **w**가 향하는 방향에 있음   
         
         > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})&space;<&space;0" title="y({\bf x}) < 0" />이면, **x**는 결정 경계면 기준으로 **-w**가 향하는 방향에 있음.   
                  
         > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})" title="y({\bf x})" />의 절댓값이 클수록 더 멀리 떨어져있음.   
         
         
         > <img src="https://user-images.githubusercontent.com/72974863/104458561-e2c3eb00-55ee-11eb-9ead-88dbaab9b5be.png" width="40%" height="40%">    
               
      + (수식 단순화) 가짜입력 dummy input <img src="https://latex.codecogs.com/gif.latex?x_0=1" title="x_0=1" /> 이용
      
         + <img src="https://latex.codecogs.com/gif.latex?{\bf&space;\widetilde{w}}=(w_0,&space;{\bf&space;w})" title="{\bf \widetilde{w}}=(w_0, {\bf w})" />   
         
         + <img src="https://latex.codecogs.com/gif.latex?{\bf&space;\widetilde{x}}=(x_0,&space;{\bf&space;x})" title="{\bf \widetilde{x}}=(x_0, {\bf x})" />   
         
         + <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})={\bf&space;\widetilde{w}}^T{\bf&space;\widetilde{x}}" title="y({\bf x})={\bf \widetilde{w}}^T{\bf \widetilde{x}}" />   
         

+ **다수의 클래스**에 대한 판별함수
   + 클래스 <img src="https://latex.codecogs.com/gif.latex?k=1,\ldots,K" title="k=1,\ldots,K" />에 대해 표현하면 다음과 같음.   
   
      > <img src="https://latex.codecogs.com/gif.latex?y_k({\bf&space;x})={\bf&space;w}_k^T{\bf&space;x}&plus;w_{k0}" title="y_k({\bf x})={\bf w}_k^T{\bf x}+w_{k0}" />   
      
      > <img src="https://latex.codecogs.com/gif.latex?j{\neq}k" title="j{\neq}k" />일 때, <img src="https://latex.codecogs.com/gif.latex?y_k({\bf&space;x})>y_j({\bf&space;x})" title="y_k({\bf x})>y_j({\bf x})" />를 만족하면, x를 클래스 <img src="https://latex.codecogs.com/gif.latex?C_k" title="C_k" />로 판별   

- - - - - - - - - - - - - -
## 분류를 위한 최소제곱법 (Least squares for classification)   

+ **사실 분류를 위해 최소제곱법 쓰는건 별로 좋지 x** ❗

+ 클래스를 판별하는 판별식은 다음과 같음   

   > <img src="https://latex.codecogs.com/gif.latex?y_k({\bf&space;x})={\bf&space;w}k^T{\bf&space;x}&plus;w{k0}" title="y_k({\bf x})={\bf w}k^T{\bf x}+w{k0}" />   

   > 행렬 <img src="https://latex.codecogs.com/gif.latex?\tilde{W}" title="\tilde{W}" />에 대해 나타내면,
   
   > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})=\tilde{W}^T\tilde{\bf&space;x}" title="y({\bf x})=\tilde{W}^T\tilde{\bf x}" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\tilde{W}" title="\tilde{W}" />의 k번째 열 : <img src="https://latex.codecogs.com/gif.latex?\tilde{w}_k=(w_{k0},&space;{\bf&space;w}_k^T)^T&space;\" title="\tilde{w}_k=(w_{k0}, {\bf w}_k^T)^T \" />   
   
+ **제곱합 에러 함수(sum-of-squared error function)**
   + 학습 데이터 <img src="https://latex.codecogs.com/gif.latex?\{{\bf&space;x}_n,&space;{\bf&space;t}_n\}" title="\{{\bf x}_n, {\bf t}_n\}" />, <img src="https://latex.codecogs.com/gif.latex?\left&space;(&space;n=1,\ldots,N&space;\right&space;)" title="\left ( n=1,\ldots,N \right )" />, n번째항이 <img src="https://latex.codecogs.com/gif.latex?{\bf&space;t}_n^T" title="{\bf t}_n^T" />인 행렬 T, n번째 행이 <img src="https://latex.codecogs.com/gif.latex?{\bf&space;\widetilde{x}}_n^T" title="{\bf \widetilde{x}}_n^T" />인 행렬 <img src="https://latex.codecogs.com/gif.latex?{\bf&space;\widetilde{x}}" title="{\bf \widetilde{x}}" />이 주어졌을 때, 제곱합 에러함수는 다음과 같음.   
   
   > <img src="https://latex.codecogs.com/gif.latex?E_D({\bf&space;\widetilde{W}})&space;=&space;\frac{1}{2}\mathrm{tr}\left\{&space;\left({\bf&space;\widetilde{X}}{\bf&space;\widetilde{W}}-{\bf&space;T}&space;\right)^T&space;\left({\bf&space;\widetilde{X}}{\bf&space;\widetilde{W}}-{\bf&space;T}&space;\right)&space;\right\}" title="E_D({\bf \widetilde{W}}) = \frac{1}{2}\mathrm{tr}\left\{ \left({\bf \widetilde{X}}{\bf \widetilde{W}}-{\bf T} \right)^T \left({\bf \widetilde{X}}{\bf \widetilde{W}}-{\bf T} \right) \right\}" />   
   
   > 유도 과정은 다음과 같음.
   
   > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;\widetilde{X}}&space;=&space;\begin{bmatrix}&space;\vdots\\&space;\rule[.5ex]{1.7ex}{0.5pt}&space;{\bf&space;\widetilde{x}}_n^T&space;\rule[.5ex]{1.7ex}{0.5pt}\\&space;\vdots&space;\end{bmatrix},~~&space;{\bf&space;\widetilde{W}}&space;=&space;\begin{bmatrix}&space;\vert\\&space;\cdots&space;{\bf&space;\widetilde{w}}_k&space;\cdots\\&space;\vert&space;\end{bmatrix},~~&space;{\bf&space;T}=&space;\begin{bmatrix}&space;\vdots\\&space;\rule[.5ex]{1.7ex}{0.5pt}&space;{\bf&space;t}_n^T&space;\rule[.5ex]{1.7ex}{0.5pt}\\&space;\vdots&space;\end{bmatrix}" title="{\bf \widetilde{X}} = \begin{bmatrix} \vdots\\ \rule[.5ex]{1.7ex}{0.5pt} {\bf \widetilde{x}}_n^T \rule[.5ex]{1.7ex}{0.5pt}\\ \vdots \end{bmatrix},~~ {\bf \widetilde{W}} = \begin{bmatrix} \vert\\ \cdots {\bf \widetilde{w}}_k \cdots\\ \vert \end{bmatrix},~~ {\bf T}= \begin{bmatrix} \vdots\\ \rule[.5ex]{1.7ex}{0.5pt} {\bf t}_n^T \rule[.5ex]{1.7ex}{0.5pt}\\ \vdots \end{bmatrix}" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;E_D({\bf&space;\widetilde{W}})&space;&=&space;\frac{1}{2}\sum_{n=1}^N\sum_{k=1}^K&space;\left({\bf&space;\widetilde{x}}_n^T{\bf&space;\widetilde{w}}_k&space;-&space;{\bf&space;t}_{nk}\right)^2\\&space;\end{align*}" title="\begin{align*} E_D({\bf \widetilde{W}}) &= \frac{1}{2}\sum_{n=1}^N\sum_{k=1}^K \left({\bf \widetilde{x}}_n^T{\bf \widetilde{w}}_k - {\bf t}_{nk}\right)^2\\ \end{align*}" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;&=&space;\frac{1}{2}\sum_{n=1}^N&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)^T\\&space;&=&space;\frac{1}{2}\sum_{n=1}^N&space;\mathrm{tr}\left\{&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)^T&space;\right\}\\&space;\end{align*}" title="\begin{align*} &= \frac{1}{2}\sum_{n=1}^N \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right) \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right)^T\\ &= \frac{1}{2}\sum_{n=1}^N \mathrm{tr}\left\{ \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right) \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right)^T \right\}\\ \end{align*}" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;&=&space;\frac{1}{2}\sum_{n=1}^N&space;\mathrm{tr}\left\{&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)^T&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)&space;\right\}\\&space;&=&space;\frac{1}{2}\mathrm{tr}\left\{&space;\sum_{n=1}^N&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)^T&space;\left(&space;{\bf&space;\widetilde{x}}_n^T&space;{\bf&space;\widetilde{W}}&space;-&space;{\bf&space;t}_n^T&space;\right)&space;\right\}\\&space;&=&space;\frac{1}{2}\mathrm{tr}\left\{&space;\left({\bf&space;\widetilde{X}}{\bf&space;\widetilde{W}}-{\bf&space;T}&space;\right)^T&space;\left({\bf&space;\widetilde{X}}{\bf&space;\widetilde{W}}-{\bf&space;T}&space;\right)&space;\right\}&space;\end{align*}" title="\begin{align*} &= \frac{1}{2}\sum_{n=1}^N \mathrm{tr}\left\{ \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right)^T \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right) \right\}\\ &= \frac{1}{2}\mathrm{tr}\left\{ \sum_{n=1}^N \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right)^T \left( {\bf \widetilde{x}}_n^T {\bf \widetilde{W}} - {\bf t}_n^T \right) \right\}\\ &= \frac{1}{2}\mathrm{tr}\left\{ \left({\bf \widetilde{X}}{\bf \widetilde{W}}-{\bf T} \right)^T \left({\bf \widetilde{X}}{\bf \widetilde{W}}-{\bf T} \right) \right\} \end{align*}" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\tilde{\bf&space;W}" title="\tilde{\bf W}" />에 대해 미분하고 식 전개하면,   
   
   > <img src="https://latex.codecogs.com/gif.latex?\tilde{\bf&space;W}=(\tilde{\bf&space;X}^T\tilde{\bf&space;X})^{-1}\tilde{\bf&space;X}^T\tilde{\bf&space;T}=\tilde{\bf&space;X}^{\dagger}\tilde{\bf&space;T}" title="\tilde{\bf W}=(\tilde{\bf X}^T\tilde{\bf X})^{-1}\tilde{\bf X}^T\tilde{\bf T}=\tilde{\bf X}^{\dagger}\tilde{\bf T}" /> (<img src="https://latex.codecogs.com/gif.latex?\tilde{\bf&space;X}^{\dagger}" title="\tilde{\bf X}^{\dagger}" /> : pseudo-inverse 행렬)    
   
+ 따라서 판별함수는 다음과 같음.

   > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})=\widetilde{\bf&space;W}^T\widetilde{\bf&space;x}={\bf&space;T}^T\left(\widetilde{\bf&space;X}^{\dagger}\right)^T\widetilde{\bf&space;x}" title="y({\bf x})=\widetilde{\bf W}^T\widetilde{\bf x}={\bf T}^T\left(\widetilde{\bf X}^{\dagger}\right)^T\widetilde{\bf x}" />   
   
+ **분류를 위한 최소제곱법의 문제점** ✨
   + outlier에 민감
   + 목표값의 확률분포에 대한 잘못된 가정에 기초 ❗ 
   
- - - - - - - - -

## 퍼셉트론 알고리즘 (The perceptron algorithm)

+ 기저함수를 넣어 일반화된 식으로 표현하면 다음과 같음.  

   > <img src="https://latex.codecogs.com/gif.latex?y({\bf&space;x})=f({\bf&space;w}^T\phi({\bf&space;x}))" title="y({\bf x})=f({\bf w}^T\phi({\bf x}))" />   
   
   > 여기서 <img src="https://latex.codecogs.com/gif.latex?\phi_0({\bf&space;x})=1" title="\phi_0({\bf x})=1" />이며, f는 활성함수(activation function)로 계단형 함수임
   
   > <img src="https://latex.codecogs.com/gif.latex?f(a)=\begin{cases}&space;&plus;1,&space;&&space;a\geq&space;0&space;\\&space;-1,&space;&&space;a<0&space;\end{cases}" title="f(a)=\begin{cases} +1, & a\geq 0 \\ -1, & a<0 \end{cases}" />   
   
+ 에러 함수
   > <img src="https://latex.codecogs.com/gif.latex?E_P({\bf&space;w})=-\sum_{n&space;\in&space;\mathcal{M}}{\bf&space;w}^T\phi_nt_n" title="E_P({\bf w})=-\sum_{n \in \mathcal{M}}{\bf w}^T\phi_nt_n" />   
   
   > <img src="https://latex.codecogs.com/gif.latex?\mathcal{M}" title="\mathcal{M}" /> : 잘못 분류된 데이터들의 집합
   
+ Stochastic gradient descent의 적용하면,

   > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;w}^{(\tau&plus;1)}={\bf&space;w}^{(\tau)}-\eta\triangledown&space;E_p({\bf&space;w})={\bf&space;w}^{(\tau)}&plus;\eta\phi_n{t_n}" title="{\bf w}^{(\tau+1)}={\bf w}^{(\tau)}-\eta\triangledown E_p({\bf w})={\bf w}^{(\tau)}+\eta\phi_n{t_n}" />   
   
+ 위 업데이트가 실행될 때 잘못 분류된 샘플에 미치는 영향
   > <img src="https://latex.codecogs.com/gif.latex?-{\bf&space;w}^{(\tau&plus;1)T}{\phi}_n{t_n}&space;=&space;-{\bf&space;w}^{(\tau)T}{\phi_n}{t_n}-(\phi_n{t_n})^T\phi_n{t_n}&space;<&space;-{\bf&space;w}^{(\tau)T}\phi_n{t_n}" title="-{\bf w}^{(\tau+1)T}{\phi}_n{t_n} = -{\bf w}^{(\tau)T}{\phi_n}{t_n}-(\phi_n{t_n})^T\phi_n{t_n} < -{\bf w}^{(\tau)T}\phi_n{t_n}" />   

⭐ 최소제곱법과 퍼셉트론 모두 output 출력하지만, 확률을 계산하진 않음 ❗

- - - - - - - - - - -
      
## 확률적 생성 모델 (Probabilistic Generative Models)

+ <img src="https://latex.codecogs.com/gif.latex?p(\mathbf{x}|C_k),&space;p(C_k)" title="p(\mathbf{x}|C_k), p(C_k)" /> 모델링 한 다음 → 클래스의 사후확률 <img src="https://latex.codecogs.com/gif.latex?p(C_k|\mathbf{x})" title="p(C_k|\mathbf{x})" />을 구함 ❗ (using 베이즈 정리)    

+ 이전 **판별함수**에서는 **에러함수를 최소화하는 최적의 파라미터를 찾는 것**이 목적이지만, **확률적 모델**은 **데이터 분포를 모델링**하면서 분류 문제를 결과적으로 풀게됨 ❗

+ 2-class를 가정하고, x가 클래스 1(C1)에 속할 확률

   > <img src="https://latex.codecogs.com/gif.latex?p(C_1|{\bf&space;x})&space;=&space;\dfrac{p({\bf&space;x}|C_1)p(C_1)}{p({\bf&space;x}|C_1)p(C_1)&plus;p({\bf&space;x}|C_2)p(C_2)}=\dfrac{1}{1&plus;\exp(-a)}&space;=&space;\sigma(a)" title="p(C_1|{\bf x}) = \dfrac{p({\bf x}|C_1)p(C_1)}{p({\bf x}|C_1)p(C_1)+p({\bf x}|C_2)p(C_2)}=\dfrac{1}{1+\exp(-a)} = \sigma(a)" /> (a에 관한 **logistic sigmoid function**)   
   
   > <img src="https://latex.codecogs.com/gif.latex?a=\ln{\dfrac{p({\bf&space;x}|C_1)p(C_1)}{p({\bf&space;x}|C_2)p(C_2)}}" title="a=\ln{\dfrac{p({\bf x}|C_1)p(C_1)}{p({\bf x}|C_2)p(C_2)}}" />   
   
   
   + **logistic sigmoid function**
      
      > <img src="https://latex.codecogs.com/gif.latex?\sigma(a)=\dfrac{1}{1&plus;\exp(-a)}" title="\sigma(a)=\dfrac{1}{1+\exp(-a)}" />   
      
     
      > <img src="https://user-images.githubusercontent.com/72974863/104664910-bd7ccd00-5713-11eb-82d3-b18e090adb63.png" width="30%" hegiht="30%">   
   
      > [sigmoid 함수-위키백과 참고](https://user-images.githubusercontent.com/72974863/104664910-bd7ccd00-5713-11eb-82d3-b18e090adb63.png)
   
      + 성질
         + 대칭 : <img src="https://latex.codecogs.com/gif.latex?\sigma(-a)&space;=&space;1&space;-&space;\sigma(a)" title="\sigma(-a) = 1 - \sigma(a)" />   
         
         + 역(inverse) : <img src="https://latex.codecogs.com/gif.latex?a=\ln\left(\dfrac{\sigma}{1-\sigma}\right)" title="a=\ln\left(\dfrac{\sigma}{1-\sigma}\right)" />   
         
+ **일반 선형 모델(generalized linear model)** - 클래스가 k>2인 경우 (일반화) ❗

   + <img src="https://latex.codecogs.com/gif.latex?p(C_k|{\bf&space;x})&space;=&space;\dfrac{p({\bf&space;x}|C_k)p(C_k)}{\sum_j{p({\bf&space;x}|C_j)p(C_j)}}=\dfrac{\exp(a_k)}{\sum_j{\exp(a_j)}}" title="p(C_k|{\bf x}) = \dfrac{p({\bf x}|C_k)p(C_k)}{\sum_j{p({\bf x}|C_j)p(C_j)}}=\dfrac{\exp(a_k)}{\sum_j{\exp(a_j)}}" /> (a에 관한 **softmax function**)   
   
   + <img src="https://latex.codecogs.com/gif.latex?a_k&space;=&space;\ln(p({\bf&space;x}|C_k)p(C_k))" title="a_k = \ln(p({\bf x}|C_k)p(C_k))" />    
   
⭐ 2-class : **logistic sigmoid function**를 이용, k-class : **softmax function**를 이용 ❗

- - - - - - - - -
+ 연속적 입력 (continuous inputs)
   
   + <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}|C_k)" title="p({\bf x}|C_k)" />가 가우시안 분포를 따르고, 모든 클래스에 대해 공분산이 동일하다고 가정하자.
   
   + 가정 하에 어떤 클래스가 주어졌다면, 해당 데이터를 output하는 확률은 다음과 같음.
   
      > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}|C_k)&space;=&space;\dfrac{1}{(2\pi)^{D/2}|\Sigma|^{1/2}}\exp&space;\left&space;\{&space;-\dfrac{1}{2}({\bf&space;x}-{\bf&space;\mu}_k)^T\Sigma^{-1}({\bf&space;x}-{\bf&space;\mu}_k)&space;\right&space;\}" title="p({\bf x}|C_k) = \dfrac{1}{(2\pi)^{D/2}|\Sigma|^{1/2}}\exp \left \{ -\dfrac{1}{2}({\bf x}-{\bf \mu}_k)^T\Sigma^{-1}({\bf x}-{\bf \mu}_k) \right \}" />   
      
   + **2-class**에 대해서,
   
      > <img src="https://latex.codecogs.com/gif.latex?p(C_1|{\bf&space;x})=\sigma(a)=\sigma({\bf&space;w}^T{\bf&space;x}&plus;w_0)" title="p(C_1|{\bf x})=\sigma(a)=\sigma({\bf w}^T{\bf x}+w_0)" />   
      
      > 이때, w벡터와 w0는 다음과 같음.
      
      > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;{\bf&space;w}&space;&=&space;\Sigma^{-1}({\pmb&space;\mu}_1&space;-&space;{\pmb&space;\mu}_2)\\&space;w_0&space;&=&space;-&space;\frac{1}{2}{\pmb&space;\mu}_1^T\Sigma^{-1}{\pmb&space;\mu}_1&space;&plus;&space;\frac{1}{2}{\pmb&space;\mu}_2^T\Sigma^{-1}{\pmb&space;\mu}_2&space;&plus;&space;\ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)}&space;\end{align*}" title="\begin{align*} {\bf w} &= \Sigma^{-1}({\pmb \mu}_1 - {\pmb \mu}_2)\\ w_0 &= - \frac{1}{2}{\pmb \mu}_1^T\Sigma^{-1}{\pmb \mu}_1 + \frac{1}{2}{\pmb \mu}_2^T\Sigma^{-1}{\pmb \mu}_2 + \ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)} \end{align*}" />   
      
      
      <details>
      <summary>a에 대한 전개</summary>   
      <div markdown="1">  
   
      > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;a&space;&=&space;\ln{\dfrac{p({\bf&space;x}|\mathcal{C}_1)p(\mathcal{C}_1)}{p({\bf&space;x}|\mathcal{C}_2)p(\mathcal{C}_2)}}\\&space;&=&space;-\frac{1}{2}({\bf&space;x}-{\pmb&space;\mu}_1)^T\Sigma^{-1}({\bf&space;x}-{\pmb&space;\mu}_1)&plus;\frac{1}{2}({\bf&space;x}-{\pmb&space;\mu}_2)^T\Sigma^{-1}({\bf&space;x}-{\pmb&space;\mu}_2)&plus;\ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)}\\&space;&=&space;\left\{\left(&space;{\pmb&space;\mu}_1^T&space;-&space;{\pmb&space;\mu}_2^T&space;\right)\Sigma^{-1}\right\}{\bf&space;x}&space;-&space;\frac{1}{2}{\pmb&space;\mu}_1^T\Sigma^{-1}{\pmb&space;\mu}_1&space;&plus;&space;\frac{1}{2}{\pmb&space;\mu}_2^T\Sigma^{-1}{\pmb&space;\mu}_2&space;&plus;&space;\ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)}&space;\end{align*}" title="\begin{align*} a &= \ln{\dfrac{p({\bf x}|\mathcal{C}_1)p(\mathcal{C}_1)}{p({\bf x}|\mathcal{C}_2)p(\mathcal{C}_2)}}\\ &= -\frac{1}{2}({\bf x}-{\pmb \mu}_1)^T\Sigma^{-1}({\bf x}-{\pmb \mu}_1)+\frac{1}{2}({\bf x}-{\pmb \mu}_2)^T\Sigma^{-1}({\bf x}-{\pmb \mu}_2)+\ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)}\\ &= \left\{\left( {\pmb \mu}_1^T - {\pmb \mu}_2^T \right)\Sigma^{-1}\right\}{\bf x} - \frac{1}{2}{\pmb \mu}_1^T\Sigma^{-1}{\pmb \mu}_1 + \frac{1}{2}{\pmb \mu}_2^T\Sigma^{-1}{\pmb \mu}_2 + \ln\frac{p(\mathcal{C}_1)}{p(\mathcal{C}_2)} \end{align*}" />   
      
      > a를 x에 관한 선형식으로 표현할 수 있음.
      
      
      
      </div>
      </details>
      
   + **k-class**에 대해서는 다음과 같이 확장 가능.
   
      + <img src="https://latex.codecogs.com/gif.latex?{\bf&space;w}_k&space;=&space;\Sigma^{-1}{\pmb&space;\mu}_k" title="{\bf w}_k = \Sigma^{-1}{\pmb \mu}_k" />   
      
      + <img src="https://latex.codecogs.com/gif.latex?w_{k0}&space;=&space;-\frac{1}{2}{\pmb&space;\mu}_{k}^{T}\Sigma^{-1}{\pmb&space;\mu}_k&space;&plus;&space;\ln&space;p(\mathcal{C}_k)" title="w_{k0} = -\frac{1}{2}{\pmb \mu}_{k}^{T}\Sigma^{-1}{\pmb \mu}_k + \ln p(\mathcal{C}_k)" />   
      
- - - - - - - - - - - - - -

+ **최대우도해 (Maximum likelihood solution)**

   + 2-class의 경우
   
      + 데이터와 파라미터들
         + 실제 데이터 <img src="https://latex.codecogs.com/gif.latex?\left&space;\{&space;{\bf&space;x}_n,&space;t_n&space;\right&space;\}" title="\left \{ {\bf x}_n, t_n \right \}" />에 대해 <img src="https://latex.codecogs.com/gif.latex?t_n=1" title="t_n=1" />이면 클래스 1로 분류하고, <img src="https://latex.codecogs.com/gif.latex?t_n=0" title="t_n=0" />은 클래스 2로 분류.
         
         + <img src="https://latex.codecogs.com/gif.latex?p(\mathcal{C}_1)=\pi" title="p(\mathcal{C}_1)=\pi" />라 할때, 구하고자하는 파라미터는 <img src="https://latex.codecogs.com/gif.latex?{\pmb&space;\mu}_1,&space;{\pmb&space;\mu}_2,&space;\Sigma,&space;\pi" title="{\pmb \mu}_1, {\pmb \mu}_2, \Sigma, \pi" /> ❗
        
      
      + 우도함수
         
         + 각 클래스에 대해 다음과 같이 표현할수 있음
         
            > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}_n,&space;C_1)&space;=&space;p(C_1)p({\bf&space;x}_n|C_1)&space;=&space;\pi&space;N({\bf&space;x}_n;\mu_1,&space;\Sigma)" title="p({\bf x}_n, C_1) = p(C_1)p({\bf x}_n|C_1) = \pi N({\bf x}_n;\mu_1, \Sigma)" />   
            
            > p({\bf x}_n, C_2) = p(C_2)p({\bf x}_n|C_2) = (1-\pi) N({\bf x}_n;\mu_2, \Sigma)   
            
            > 따라서,
            
            > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;t}|&space;\pi,&space;{\bf&space;\mu}_1,&space;{\bf&space;\mu}2,&space;\Sigma)&space;=&space;\prod_{n=1}^N\left(\pi&space;N({\bf&space;x}_n|{\bf&space;\mu}_1,&space;\Sigma)\right)^{t_n}\left((1-\pi)N({\bf&space;x}_n|{\bf&space;\mu}_2,&space;\Sigma)\right)^{1-t_n}" title="p({\bf t}| \pi, {\bf \mu}_1, {\bf \mu}2, \Sigma) = \prod_{n=1}^N\left(\pi N({\bf x}_n|{\bf \mu}_1, \Sigma)\right)^{t_n}\left((1-\pi)N({\bf x}_n|{\bf \mu}_2, \Sigma)\right)^{1-t_n}" />   
            
            
         <details>
         <summary>π 구하기</summary>   
         <div markdown="1"> 
         
         + 로그우도함수에서 <img src="https://latex.codecogs.com/gif.latex?\pi" title="\pi" /> 관련항들만 정리하면 다음과 같음.
            
            > <img src="https://latex.codecogs.com/gif.latex?\sum_{n=1}^{N}\left\{&space;t_n\ln\pi&space;&plus;&space;(1-t_n)\ln(1-\pi)&space;\right\}" title="\sum_{n=1}^{N}\left\{ t_n\ln\pi + (1-t_n)\ln(1-\pi) \right\}" />   
            
            > <img src="https://latex.codecogs.com/gif.latex?\pi" title="\pi" />에 대해 미분 후, 0으로 놓고 계산하면
            
            > <img src="https://latex.codecogs.com/gif.latex?\pi&space;=&space;\dfrac{1}{N}\sum_{n=1}^{N}t_n&space;=&space;\dfrac{N_1}{N}&space;=&space;\dfrac{N_1}{N_1&plus;N_2}" title="\pi = \dfrac{1}{N}\sum_{n=1}^{N}t_n = \dfrac{N_1}{N} = \dfrac{N_1}{N_1+N_2}" />   
            
            > <img src="https://latex.codecogs.com/gif.latex?N_1,&space;N_2" title="N_1, N_2" />는 각각 클래스 1과 2에 속하는 샘플 수.
            
            > <img src="https://latex.codecogs.com/gif.latex?\pi" title="\pi" />는 클래스 1에 속하는 샘플의 비율을 의미 ❗   
            
         </div>
         </details>
      
      
         <details>
         <summary>μ 구하기 </summary>   
         <div markdown="1"> 
         
         + <img src="https://latex.codecogs.com/gif.latex?\pi" title="\pi" /> 구할때와 동일하게, 로그우도함수에서 μ 관련항들 정리한후, μ에 대해 미분하여 값을 구함.   
            
            > μ 관련항들은 다음과 같음. 
            
            > <img src="https://latex.codecogs.com/gif.latex?\sum_{n=1}^{N}t_n\ln&space;\mathcal{N}({\bf&space;x}_n|{\pmb&space;\mu}_1,&space;\Sigma)&space;=&space;-\dfrac{1}{2}\sum_{n=1}^{N}t_n({\bf&space;x}_n-{\pmb&space;\mu}_1)^T\Sigma^{-1}({\bf&space;x}_n-{\pmb&space;\mu}_1)&space;&plus;&space;\mathrm{const}" title="\sum_{n=1}^{N}t_n\ln \mathcal{N}({\bf x}_n|{\pmb \mu}_1, \Sigma) = -\dfrac{1}{2}\sum_{n=1}^{N}t_n({\bf x}_n-{\pmb \mu}_1)^T\Sigma^{-1}({\bf x}_n-{\pmb \mu}_1) + \mathrm{const}" />
             
            > <img src="https://latex.codecogs.com/gif.latex?{\pmb&space;\mu}_1" title="{\pmb \mu}_1" />에 관해 미분 후, 0으로 놓고 정리하면
            
            > <img src="https://latex.codecogs.com/gif.latex?{\pmb&space;\mu}_1=\dfrac{1}{N_1}\sum_{n=1}^{N}t_n{\bf&space;x}_n" title="{\pmb \mu}_1=\dfrac{1}{N_1}\sum_{n=1}^{N}t_n{\bf x}_n" />   
            
            > <img src="https://latex.codecogs.com/gif.latex?{\pmb&space;\mu}_2" title="{\pmb \mu}_2" />에 관해 미분 후, 0으로 놓고 정리하면
            
            > <img src="https://latex.codecogs.com/gif.latex?{\pmb&space;\mu}_2=\dfrac{1}{N_2}\sum_{n=1}^{N}(1-t_n){\bf&space;x}_n" title="{\pmb \mu}_2=\dfrac{1}{N_2}\sum_{n=1}^{N}(1-t_n){\bf x}_n" />   
            
            
         </div>
         </details>    
         
         
         <details>
         <summary>∑ 구하기 </summary>   
         <div markdown="1"> 
         
         + 이 부분은 제일 복잡한 부분...  
         
         + 여기도 동일하게 로그우도함수로부터 공분산 ∑ 미분하여 구함.
            
            > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;&-\dfrac{1}{2}\sum_{n=1}^{N}t_n\ln&space;|\Sigma|&space;-\dfrac{1}{2}\sum_{n=1}^{N}t_n({\bf&space;x}_n-{\pmb&space;\mu}_1)^T\Sigma^{-1}({\bf&space;x}_n-{\pmb&space;\mu}_1)\\&space;&-\dfrac{1}{2}\sum_{n=1}^{N}(1-t_n)\ln&space;|\Sigma|&space;-\dfrac{1}{2}\sum_{n=1}^{N}(1-t_n)({\bf&space;x}_n-{\pmb&space;\mu}_2)^T\Sigma^{-1}({\bf&space;x}_n-{\pmb&space;\mu}_2)\\&space;&=&space;-\dfrac{N}{2}\ln&space;|\Sigma|&space;-&space;\dfrac{N}{2}\mathrm{tr}\left(\Sigma^{-1}{\bf&space;S}\right)&space;\end{align*}" title="\begin{align*} &-\dfrac{1}{2}\sum_{n=1}^{N}t_n\ln |\Sigma| -\dfrac{1}{2}\sum_{n=1}^{N}t_n({\bf x}_n-{\pmb \mu}_1)^T\Sigma^{-1}({\bf x}_n-{\pmb \mu}_1)\\ &-\dfrac{1}{2}\sum_{n=1}^{N}(1-t_n)\ln |\Sigma| -\dfrac{1}{2}\sum_{n=1}^{N}(1-t_n)({\bf x}_n-{\pmb \mu}_2)^T\Sigma^{-1}({\bf x}_n-{\pmb \mu}_2)\\ &= -\dfrac{N}{2}\ln |\Sigma| - \dfrac{N}{2}\mathrm{tr}\left(\Sigma^{-1}{\bf S}\right) \end{align*}" />   
            
            > 여기서 S는 다음과 같음. (using 이전 강의에서 배웠던 가우시안 분포의 최대우도-확률분포II)
            
            > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;S}&space;=\dfrac{N_1}{N}{\bf&space;S}_1&plus;\dfrac{N_2}{N}{\bf&space;S}_2" title="{\bf S} =\dfrac{N_1}{N}{\bf S}_1+\dfrac{N_2}{N}{\bf S}_2" />   
            
            > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;S}_1&space;=&space;\dfrac{1}{N_1}\sum_{n&space;\in&space;C_1}&space;({\bf&space;x}_n-{\pmb&space;\mu}_1)({\bf&space;x}_n-{\pmb&space;\mu}_1)^T" title="{\bf S}_1 = \dfrac{1}{N_1}\sum_{n \in C_1} ({\bf x}_n-{\pmb \mu}_1)({\bf x}_n-{\pmb \mu}_1)^T" />   
            
            > <img src="https://latex.codecogs.com/gif.latex?{\bf&space;S}_2&space;=&space;\dfrac{1}{N_2}\sum_{n&space;\in&space;C_2}&space;({\bf&space;x}_n-{\pmb&space;\mu}_2)({\bf&space;x}_n-{\pmb&space;\mu}_2)^T" title="{\bf S}_2 = \dfrac{1}{N_2}\sum_{n \in C_2} ({\bf x}_n-{\pmb \mu}_2)({\bf x}_n-{\pmb \mu}_2)^T" />   
            
            > 가우시안 분포의 최대우도를 구하는 방법을 사용하면 ∑=S   
         
         
         </div>
         </details>  

      

## 데이터가 이산일 때 (Discrete features)

+ 각 특성 <img src="https://latex.codecogs.com/gif.latex?x_i" title="x_i" />이 0 또는 1, 하나의 값만 가질 수 있는 경우

   + 클래스가 주어졌을 때 특성들이 **조건부 독립(conditional independence)이라는 가정**을 할 경우 문제는 단순화됨! → **naive Bayes** 가정
   
     > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;x}|\mathcal{C}_k)&space;=&space;\prod_{i=1}^{D}\mu_{ki}^{x_i}(1-\mu_{ki})^{1-x_i}" title="p({\bf x}|\mathcal{C}_k) = \prod_{i=1}^{D}\mu_{ki}^{x_i}(1-\mu_{ki})^{1-x_i}" />   
     
     > 이때, <img src="https://latex.codecogs.com/gif.latex?\mu_{ki}=p(x_i=1|C_k)" title="\mu_{ki}=p(x_i=1|C_k)" />이며, 위 식을 k-class의 <img src="https://latex.codecogs.com/gif.latex?a_k" title="a_k" />에 대입하면 다음과 같음.   
     
     > <img src="https://latex.codecogs.com/gif.latex?a_k({\bf&space;x})=\ln&space;p({\bf&space;x}|\mathcal{C}_k)p(\mathcal{C}_k)" title="a_k({\bf x})=\ln p({\bf x}|\mathcal{C}_k)p(\mathcal{C}_k)" />   
     
     > <img src="https://latex.codecogs.com/gif.latex?a_k({\bf&space;x})=\ln&space;p({\bf&space;x}|\mathcal{C}_k)p(\mathcal{C}_k)=\sum_{i=1}^{D}\left\{x_i\ln&space;\mu_{ki}&plus;(1-x_i)\ln(1-\mu_{ki})\right\}&plus;\ln&space;p(\mathcal{C}_k)" title="a_k({\bf x})=\ln p({\bf x}|\mathcal{C}_k)p(\mathcal{C}_k)=\sum_{i=1}^{D}\left\{x_i\ln \mu_{ki}+(1-x_i)\ln(1-\mu_{ki})\right\}+\ln p(\mathcal{C}_k)" />   
     
     > <img src="https://latex.codecogs.com/gif.latex?a_k" title="a_k" /> 함수가 <img src="https://latex.codecogs.com/gif.latex?x_{k}" title="x_{k}" /> 함수에 대해 선형인 것을 확인할 수 있음. 
     

## 확률적 식별 모델 (Probabilistic discriminative model)

+ x가 주어졌을 때, 클래스의 확률을 x에 관한 함수로 가정하고, 파라미터를 바로 구하는 모델

+ **로지스틱 회귀(Logistic regression)** : 대표적인 방법 ✨

   + 클래스 C1의 사후 확률 = 특성벡터 <img src="https://latex.codecogs.com/gif.latex?\phi" title="\phi" />의 선형함수가 logistic sigmoid 를 통과 함수   
         
      > <img src="https://latex.codecogs.com/gif.latex?p(C_1|\phi)=y(\phi)=\sigma({\bf&space;w}^T\phi)" title="p(C_1|\phi)=y(\phi)=\sigma({\bf w}^T\phi)" />   
      
      > 이때, 입력함수 x대신 비선형 기저함수 <img src="https://latex.codecogs.com/gif.latex?\phi(\mathbf{x})" title="\phi(\mathbf{x})" /> 사용함.
      
      > 위 식의 logistic sigmoid 함수 : <img src="https://latex.codecogs.com/gif.latex?\sigma(a)=\dfrac{1}{1&plus;\exp(-a)}" title="\sigma(a)=\dfrac{1}{1+\exp(-a)}" />   
         
   + 클래스 C2의 사후 확률은 다음과 같음.   
      
      > <img src="https://latex.codecogs.com/gif.latex?p(\mathcal{C}_2|\phi)&space;=&space;1&space;-&space;p(\mathcal{C}_1|\phi)" title="p(\mathcal{C}_2|\phi) = 1 - p(\mathcal{C}_1|\phi)" />   
         
   + <img src="https://latex.codecogs.com/gif.latex?\phi" title="\phi" />가 M차원 일 때, 구해야할 파라미터 w의 개수는 M
      > 셍성모델의 경우에는, M(M+5)/2+1개의 파라미터 구해야함
         
      > 이에 반면, 로지스틱 회귀는 훨씬더 작은 M의 linear한 개수의 파라미터만 구해도 됨.   
      
   + 최대우도해

      + 데이터 셋 : <img src="https://latex.codecogs.com/gif.latex?\{\phi_n,&space;t_n\},&space;\textup{&space;for&space;}n=1,\ldots,N" title="\{\phi_n, t_n\}, \textup{ for }n=1,\ldots,N" />   
   
      + <img src="https://latex.codecogs.com/gif.latex?t_n&space;\in&space;\{0,&space;1\}" title="t_n \in \{0, 1\}" />   
   
      + <img src="https://latex.codecogs.com/gif.latex?{\bf&space;t}&space;=&space;(t_1,\ldots,t_N)^T" title="{\bf t} = (t_1,\ldots,t_N)^T" />   
   
      + <img src="https://latex.codecogs.com/gif.latex?\phi_n&space;=&space;\phi({\bf&space;x}_n)" title="\phi_n = \phi({\bf x}_n)" />   
   
      + <img src="https://latex.codecogs.com/gif.latex?y_n&space;=&space;p(\mathcal{C}_1|\phi_n)&space;=&space;\sigma({\bf&space;w}^T\phi_n)&space;\" title="y_n = p(\mathcal{C}_1|\phi_n) = \sigma({\bf w}^T\phi_n) \" />   
   
      + 우도함수
         > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;t}|{\bf&space;w})&space;=&space;\prod_{n=1}^{N}y_n^{t_n}(1-y_n)^{1-t_n}" title="p({\bf t}|{\bf w}) = \prod_{n=1}^{N}y_n^{t_n}(1-y_n)^{1-t_n}" />   
      
      + 음의 로그우도
   
         > <img src="https://latex.codecogs.com/gif.latex?E({\bf&space;w})=&space;-\ln{p({\bf&space;t}|{\bf&space;w})}&space;=&space;-&space;\sum_{n=1}^{N}\left&space;\{t_n\ln{y_n}&plus;(1-t_n)\ln(1-y_n)\right\}" title="E({\bf w})= -\ln{p({\bf t}|{\bf w})} = - \sum_{n=1}^{N}\left \{t_n\ln{y_n}+(1-t_n)\ln(1-y_n)\right\}" />   
      
      
         > 모수 추정을 위해 사용하며, 이는 **크로스 엔트로피 에러함수(cross entropy error function)** ❗
   
      + **크로스 엔트로피(cross entropy error function)**    
   
         + 정보이론에서 <img src="https://latex.codecogs.com/gif.latex?H(p,q)&space;=&space;-\mathbb{E}_p[\ln&space;q]" title="H(p,q) = -\mathbb{E}_p[\ln q]" />   
      
            > 이산확률변수의 경우, <img src="https://latex.codecogs.com/gif.latex?H(p,q)&space;=&space;-\sum_{x}p(x)\ln&space;q(x)" title="H(p,q) = -\sum_{x}p(x)\ln q(x)" />   
      
         + 일반적으로 **크로스 엔트로피가 최소화**될 때, **두 확률분포의 차이가 최소화**  
      
            > 따라서, **에러함수 최소화 = 우도 최대화 = 목표 변수(분포)와 예측값 분포 차이 최소화** ❗   
         

      + 에러함수 w의 gradient
   
          > <img src="https://latex.codecogs.com/gif.latex?\triangledown&space;E({\bf&space;w})&space;=&space;\sum_{n=1}^N&space;\triangledown&space;E_n({\bf&space;w})" title="\triangledown E({\bf w}) = \sum_{n=1}^N \triangledown E_n({\bf w})" />
       
          > 이때, <img src="https://latex.codecogs.com/gif.latex?E_n({\bf&space;w})=&space;-\left\{t_n\ln{y_n}&plus;(1-t_n)\ln(1-y_n)\right\}" title="E_n({\bf w})= -\left\{t_n\ln{y_n}+(1-t_n)\ln(1-y_n)\right\}" />으로 나타낼 수 있음.   
       
          > 따라서, <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;\triangledown&space;E_n({\bf&space;w})&space;&=&space;\frac{\partial&space;E_n({\bf&space;w})}{\partial&space;y_n}\frac{\partial&space;y_n}{\partial&space;a_n}\triangledown&space;a_n\\&space;&=&space;\left\{&space;\frac{1-t_n}{1-y_n}&space;-&space;\frac{t_n}{y_n}\right\}&space;y_n(1-y_n)\phi_n\\&space;&=&space;(y_n&space;-&space;t_n)\phi_n&space;\end{align*}" title="\begin{align*} \triangledown E_n({\bf w}) &= \frac{\partial E_n({\bf w})}{\partial y_n}\frac{\partial y_n}{\partial a_n}\triangledown a_n\\ &= \left\{ \frac{1-t_n}{1-y_n} - \frac{t_n}{y_n}\right\} y_n(1-y_n)\phi_n\\ &= (y_n - t_n)\phi_n \end{align*}" />이므로   
       
          > 전체적인 에러 함수 w의 gradient는 다음과 같음.   
       
          > <img src="https://latex.codecogs.com/gif.latex?\triangledown&space;E({\bf&space;w})&space;=&space;\sum_{n=1}^N&space;(y_n&space;-&space;t_n)\phi_n" title="\triangledown E({\bf w}) = \sum_{n=1}^N (y_n - t_n)\phi_n" />   
       

+ **다중 클래스 로지스틱 회귀(Multiclass logistic regression)**
   
   + 또는 **소프트맥스 회귀(Softmax regression)** 라고 함.   
   
      > <img src="https://latex.codecogs.com/gif.latex?p(C_k|\phi)&space;=&space;y_k(\phi)&space;=&space;\frac{\exp(a_k)}{\sum_j&space;\exp(a_j)}" title="p(C_k|\phi) = y_k(\phi) = \frac{\exp(a_k)}{\sum_j \exp(a_j)}" />    
      
      > <img src="https://latex.codecogs.com/gif.latex?a_k&space;=&space;{\bf&space;w}_k^T&space;\phi" title="a_k = {\bf w}_k^T \phi" />   
      
      + 샘플 x가 주어지면 소프트맥스 회귀 모델이 각 클래스에 대한 점수 계산
      + 이에 소프트맥스 함수를 적용해서 각 클래스의 확률 추정, 확률이 가장 큰 클래스 선택(모든 확률의 합=1)
   
   + 우도함수
      + 특성 벡터 <img src="https://latex.codecogs.com/gif.latex?\phi_n" title="\phi_n" />를 위한 목표벡터 <img src="https://latex.codecogs.com/gif.latex?\mathbf{t}_n" title="\mathbf{t}_n" />는 클래스에 해당하는 하나의 원소만 1(나머지 0)인 1-of-k 인코딩 방법으로 표현   
      
         > <img src="https://latex.codecogs.com/gif.latex?p({\bf&space;T}|{\bf&space;w}_1,...{\bf&space;w}_K)&space;=&space;\prod_{n=1}^{N}\prod_{k=1}^{K}&space;p(\mathcal{C}_k|\phi_n)^{t_{nk}}&space;=&space;\prod_{n=1}^{N}\prod_{k=1}^{K}y_{nk}^{t_{nk}}" title="p({\bf T}|{\bf w}_1,...{\bf w}_K) = \prod_{n=1}^{N}\prod_{k=1}^{K} p(\mathcal{C}_k|\phi_n)^{t_{nk}} = \prod_{n=1}^{N}\prod_{k=1}^{K}y_{nk}^{t_{nk}}" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?y_{nk}&space;=&space;y_k(\phi_n)" title="y_{nk} = y_k(\phi_n)" />이며,
         
         > <img src="https://latex.codecogs.com/gif.latex?\bf&space;T" title="\bf T" /> : <img src="https://latex.codecogs.com/gif.latex?t_{nk}" title="t_{nk}" />를 원소로 갖는 N x K 크기의 행렬   
         
   + 음의 로그 우도
      
      > 위의 우도함수를 음의 로그를 취하면, 
      
      > <img src="https://latex.codecogs.com/gif.latex?E({\bf&space;w}_1,&space;...,&space;{\bf&space;w}_K)&space;=&space;-\ln&space;p({\bf&space;T}|{\bf&space;w}_1,&space;...,{\bf&space;w}_K)&space;=&space;-&space;\sum_{n=1}^{N}&space;\sum_{k=1}^{K}&space;t_{nk}\ln(y_{nk})" title="E({\bf w}_1, ..., {\bf w}_K) = -\ln p({\bf T}|{\bf w}_1, ...,{\bf w}_K) = - \sum_{n=1}^{N} \sum_{k=1}^{K} t_{nk}\ln(y_{nk})" />    
      
      + 에러함수 최소화 → 파라미터 구하기(<img src="https://latex.codecogs.com/gif.latex?\mathbf{w}_j" title="\mathbf{w}_j" />에 대한 gradient)   
      
         > 하나의 샘플에 대한 에러에 대해 아래와 같이 정의하면,
         
         > <img src="https://latex.codecogs.com/gif.latex?E_n({\bf&space;w}_1,\ldots,{\bf&space;w}_K)&space;=&space;-\sum_{k=1}^{K}&space;t_{nk}\ln(y_{nk})" title="E_n({\bf w}_1,\ldots,{\bf w}_K) = -\sum_{k=1}^{K} t_{nk}\ln(y_{nk})" />   
         
         > <img src="https://latex.codecogs.com/gif.latex?\mathbf{w}_j" title="\mathbf{w}_j" />에 대한 gradient   
         
         > <img src="https://latex.codecogs.com/gif.latex?\nabla_{&space;{\bf&space;w}_j&space;}E({\bf&space;w}_1,&space;...,{\bf&space;w}_K)&space;=&space;\sum_{n=1}^{N}\nabla_{&space;{\bf&space;w}_j&space;}E_n({\bf&space;w}_1,&space;...,{\bf&space;w}_K)" title="\nabla_{ {\bf w}_j }E({\bf w}_1, ...,{\bf w}_K) = \sum_{n=1}^{N}\nabla_{ {\bf w}_j }E_n({\bf w}_1, ...,{\bf w}_K)" />   
         
         
         <details>
         <summary>풀이는 다음과 같음</summary>   
         <div markdown="1">  
         
         > <img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;\nabla_{&space;{\bf&space;w}_j&space;}E_n&space;&=&space;\frac{\partial&space;E_n}{\partial&space;a_{nj}}&space;\frac{\partial&space;a_{nj}}{\partial&space;{\bf&space;w}_j}\\&space;&=&space;\frac{\partial&space;E_n}{\partial&space;a_{nj}}\phi_n&space;&&space;\left&space;(\because&space;a_nj=\mathbf{w}^T_{nj}\phi_n&space;\right&space;)\\&space;&=&space;\sum_{k=1}^K&space;\left(&space;\frac{\partial&space;E_n}{\partial&space;y_{nk}}&space;\frac{\partial&space;y_{nk}}{\partial&space;a_{nj}}&space;\right)\phi_n\\&space;&=&space;\phi_n&space;\sum_{k=1}^K&space;\left\{&space;-\frac{t_{nk}}{y_{nk}}y_{nk}(I_{kj}-y_{nj})&space;\right\}\\&space;&=&space;\phi_n&space;\sum_{k=1}^K&space;t_{nk}(y_{nj}&space;-&space;I_{kj})\\&space;&=&space;\phi_n&space;\left(&space;y_{nj}\sum_{k=1}^K&space;t_{nk}&space;-&space;\sum_{k=1}^K&space;t_{nk}I_{kj}&space;\right)\\&space;&=&space;\phi_n&space;(y_{nj}&space;-&space;t_{nj})&space;\end{align*}" title="\begin{align*} \nabla_{ {\bf w}_j }E_n &= \frac{\partial E_n}{\partial a_{nj}} \frac{\partial a_{nj}}{\partial {\bf w}_j}\\ &= \frac{\partial E_n}{\partial a_{nj}}\phi_n & \left (\because a_nj=\mathbf{w}^T_{nj}\phi_n \right )\\ &= \sum_{k=1}^K \left( \frac{\partial E_n}{\partial y_{nk}} \frac{\partial y_{nk}}{\partial a_{nj}} \right)\phi_n\\ &= \phi_n \sum_{k=1}^K \left\{ -\frac{t_{nk}}{y_{nk}}y_{nk}(I_{kj}-y_{nj}) \right\}\\ &= \phi_n \sum_{k=1}^K t_{nk}(y_{nj} - I_{kj})\\ &= \phi_n \left( y_{nj}\sum_{k=1}^K t_{nk} - \sum_{k=1}^K t_{nk}I_{kj} \right)\\ &= \phi_n (y_{nj} - t_{nj}) \end{align*}" />
      

         </div>
         </details>
         
         > 결과적으로, 다음과 같음 ❗
         
         > <img src="https://latex.codecogs.com/gif.latex?\nabla_{&space;{\bf&space;w}_j&space;}E({\bf&space;w}_1,&space;...,{\bf&space;w}_K)&space;=&space;\sum_{n=1}^{N}&space;(y_{nj}-t_{nj})\phi_n" title="\nabla_{ {\bf w}_j }E({\bf w}_1, ...,{\bf w}_K) = \sum_{n=1}^{N} (y_{nj}-t_{nj})\phi_n" />   


#### [✨️ 공부하면서 참고한 사이트](http://norman3.github.io/prml/docs/chapter04/0)
