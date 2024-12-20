# 🎲 더 지니어스 : 흑과백 with AI 🎲

[![Python](https://img.shields.io/badge/Python-3.12%2B-blue)]()
[![Pygame](https://img.shields.io/badge/Pygame-2.5.2-green)]()

***더 지니어스*** 시리즈의 데스매치 게임 "***흑과백***"을 파이썬으로 구현한 프로젝트입니다. **강화학습으로 훈련된 AI**와 대결하며 당신의 전략을 시험해보세요!

## 📌 목차
- [소개](#-소개)
- [데모 비디오](#-데모-비디오)
- [주요 기능](#-주요-기능)
- [게임 규칙](#-게임-규칙)
- [실행 방법](#-실행-방법)
- [AI 모델](#-강화학습에-사용된-ai-모델과-고찰-후기)
- [기술 스택](#-기술-스택)
- [향후 계획](#-향후-계획)
- [참조](#-참조)

## 🌟 소개
**더 지니어스: 흑과백 with AI**는 tvN의 인기 예능 프로그램 '더 지니어스'의 데스매치 게임인 '흑과백'을 강화학습을 접목시켜 구현한 프로젝트입니다. Pygame으로 구현된 게임 인터페이스와 강화학습 기반의 AI를 통해 전략적이고 몰입도 높은 게임 경험을 제공합니다.

## 📺 데모 비디오

[![Watch the video on youtube](https://github.com/kstone-285/oss_project/blob/main/images/bnw.png)](https://youtu.be/-MmGbWzX8nk)
***(사진을 누르면 영상으로 넘어갑니다)*** <br>

## ✨ 주요 기능
- 🤖 **강화학습** 기반의 지능형 AI 플레이어
- 👯 AI와 상대하지 않고 두 명이서도 즐길 수 있는 **2P모드**
- 🎮 직관적인 게임 인터페이스와 실제 더 지니어스를 플레이하는 듯한 몰입감
- 🕰 게임 내 **모드 선택 및 재시작** 기능

## 🎯 게임 규칙

[![Watch the video on youtube](https://github.com/kstone-285/oss_project/blob/main/images/bnwrule.png)](https://youtu.be/tffgFa6xFvg)<br>
***(사진을 누르면 영상으로 넘어갑니다)*** <br>

1. **기본 설정**

![tiles](https://github.com/user-attachments/assets/0ba36cd4-1cb1-47e7-8e0d-c7f2daf1da98)

   - 각 플레이어는 **0-8** 까지의 숫자 타일을 보유합니다.
   - 보유한 타일은 그 숫자에따라 **흑**(짝수타일)과 **백**(홀수타일)로 구분됩니다.
   - 게임 시작 전, 자신의 타일 배치를 마음대로 변경할 수 있습니다.
   - 당연하게도, **역심리**를 이용해 배치를 안하고 상대하셔도 좋습니다.

2. **게임 진행**
   - 기본적으로 매 라운드 각자 제시할 타일을 1개 선택합니다.
   - 이전 라운드의 승자가 먼저 타일을 선택하고, 상대 플레이어는 제시한 **타일의 색깔**만 알 수 있습니다.
   - 선택한 타일은 라운드가 끝난 후 소멸됩니다.
   
![end](https://github.com/user-attachments/assets/50f0df69-fcf5-4764-a865-90d4bb32e302)

   - 총 9라운드로 진행하고, 5점을 먼저 선취하거나, 9라운드 이후 점수가 더 높은 플레이어가 승리합니다.

3. **점수 계산**

![draw PNG](https://github.com/user-attachments/assets/d0e69b0b-ff70-4cd2-be51-3e1dad191ad6)

   - 내가 제시한 타일이 더 큰 값이면, 점수를 1 얻습니다. 무승부이면 누구의 점수도 증가하지 않습니다.

4. **제작자의 팁**
   - **질 때는 큰 차이**로, **이길 때는 작은 차이**로 이겨야 합니다!
   

## 🎮 실행 방법

### 1. 리포지토리에서 📝blacknwhite.py 파일 다운로드 후 실행
```bash
python blacknwhite.py
```
   - AI 대전 모드
   - 2P 대전 모드
   - 둘 중 원하는 모드를 선택하여 플레이하시면 됩니다.
   - **main.py, game.py, utils.py** 로 **추상화 한 버전**도 존재하니, 기호에 맞게 사용하시면 됩니다.

### 2. 게임파일 실행 전 설치해주셔야 하는 것들입니다.  
```bash
pip install numpy torch pygame
```
```
📝game_ai_integration.py  
학습된 AI 모델을 적용하는 객체를 구현해둔 파일입니다.  

📁dqn/*
DQN 모델을 구현해둔 파일들입니다. (네트워크 구성, 트레이닝)

📁a2c/*
A2C 모델을 구현해둔 파일들입니다. (정책 네트워크, 트레이닝) 

📁ppo/train_ppo.py  
PPO 모델을 구현해둔 파일입니다. 

📁trained_AI/*
학습된 모델들의 pth 파일입니다. 위 세 모델의 pth 파일이 모두 담겨있습니다.
대결해보고 싶은 AI 파일을 경로를 지정해 클래스를 바꾸며 적용시키시면 됩니다.

📝images/HeirofLightBold.ttf
게임에 적용된 폰트 파일입니다.

📝main.py, game.py, utils.py
blacknwhite.py를 메인, 상수지정, 게임로직으로 분리해둔 파일입니다.
```

### 3. 게임의 극초창기 버전을 즐기고 싶다면?
```bash
python blacknwhite_beta.py
```
**📝blacknwhite_beta.py** 를 다운 받으신 후, 플레이 해보세요! 상대는 **완전히 random한 선택**을 합니다.


## 🤖 강화학습에 사용된 AI 모델과 고찰, 후기

- **알고리즘**: **Deep Q-Network (DQN)**, **Actor-critic (A2C)**, **Proximal Policy** **Optimization** (PPO)를 사용했습니다.
- **학습 데이터**: 각 모델마다 평균 **40,000+** 에피소드를 두 AI가 대전하며 학습했습니다.
- **각 AI 모델의 특징**:
  - ## ***DQN***

    <img width = "700" height = "260" src="https://github.com/user-attachments/assets/b6b910be-e1df-42e8-afe9-a840a7909a91"> <br>
    ***(본인의 경우는 MSE loss function을 사용했습니다.)***

    - **DQN**은 가장 처음 적용해본 모델로, 가장 접근성이 좋고 배우기 쉬운 모델이었기에 선택했습니다.<br>
    그러나 DQN은 흑과백과 같은 **실시간 확률기반, 장기전략**이 중요한 게임에서는 적합하지 않았습니다.<br>
    해당 이유는 크게 3가지 입니다.  

      1. DQN은 한 번의 행동에 따른 **즉각적인 보상을 기반으로 학습**하는 경향이 있었습니다. <br><br>
         이런 류의 게임은 개별 행동에 대한 리워드보다는 전체 전략, 상대방보다 얼마나 작은 차이로 이기고 큰차이로 지는지에 대한 보상이 중요합니다.<br><br>
      2. **확률적인 요소**와 **심리전 요소**가 행동으로의 **소극적 반영**이 있었습니다.<br><br>
         매 라운드, 매 에피소드마다 상대방의 행동은 확률적으로 변화하기에, 심리패턴이나 블러핑에 대한 반응 또한 존재해야 합니다.  
         DQN은 e-greedy로 학습하긴하나, 최종적으로는 **고승률 패턴에 최적화**되는 경향이 있었습니다.  
         아래는 에이전트의 행동 설정에 대한 주요 코드입니다.<br><br>
         ```python
         self.epsilon = 1.0
         self.epsilon_min = 0.01
         self.epsilon_decay = 0.995

         def act(self, state, valid_actions):
            
            if random.random() <= self.epsilon:
                  return random.choice(valid_actions)
            
            # 현재 상태에 대한 Q-값 예측
            state = torch.FloatTensor(state).unsqueeze(0).to(self.device)
            with torch.no_grad():
                  action_values = self.model(state)
            
            # 유효한 액션 중 최고 가치 액션 선택
            valid_action_values = action_values.cpu().numpy()[0]
            valid_action_values = {action: valid_action_values[action] for action in valid_actions}
            return max(valid_action_values, key=valid_action_values.get)
         ```
         <br>
      3. **에피소드 기반 최적화**를 진행하기 때문입니다.<br><br>
         DQN은 일반적으로 **마르코프 결정 과정**을 기반으로 설계되었고, 이는 게임의 전체적인 맥락을 파악하지 못하며, 해당 에피소드 내에서만 학습하는 결과를 낳습니다.
         이로인해 고정된 패턴에 갇혀 학습을 진행한 결과가 일련의 **선택순서**였고, 이는 AI 모델에 적합하지 않다 판단하여 폐기했습니다.
         위의 코드를 보아도, e-greedy로는 한계가 존재하고, 전략의 다양성 자체가 부족해 예측을 제대로 하지 못했습니다.
         이를 개선하기 위해서는 **softmax**를 이용하거나, **엔트로피**를 이용한 다양성을 부여해야 할 것 같습니다.<br><br>
         ```python
         def replay(self, batch_size):

            if len(self.memory) < batch_size:
                  return
            
            # 무작위로 미니배치 샘플링
            minibatch = random.sample(self.memory, batch_size)
            
            # 배치 데이터를 텐서로 변환
            ...
            
            current_q_values = self.model(states).gather(1, actions.unsqueeze(1))
            next_q_values = self.target_model(next_states).max(1)[0].detach()
            
            # 목표 Q-값 계산 (벨만 방정식)
            target_q_values = rewards + (1 - dones) * self.gamma * next_q_values
            
            # 손실 함수 계산 및 모델 업데이트
            loss = nn.MSELoss()(current_q_values.squeeze(), target_q_values)
            self.optimizer.zero_grad()
            loss.backward()
            self.optimizer.step()
            
            # 탐험률 점진적 감소
            if self.epsilon > self.epsilon_min:
                  self.epsilon *= self.epsilon_decay
         ```

  - ## ***A2C***
    
    <img width = "700" height = "260" src="https://github.com/user-attachments/assets/eb6f67ab-4c3e-433e-af1c-72bb137391f1"> <br>
    ***(본인의 경우는 log loss function을 사용했습니다.)***

    - **A2C**는 **정책 기반 학습**과 **가치 기반 학습**을 결합한 알고리즘으로, DQN보다는 확률을 사용하기에 해당 게임에 더 적합하다고 판단해 적용했습니다.  
      이 모델은 특히 **확률적 요소**가 많고 **장기적인 전략**이 중요한 흑과백 게임에서 더욱 효과적이었습니다.  
      당연히 DQN보다는 성능이 좋았지만, 게임에 적용했을 때의 **장점**과 **한계**는 다음과 같습니다.  

      - **장점:**
         1. **장기적인 전략 학습** 
            ```python
            def forward(self, state):
               
               x = F.relu(self.fc1(state))
               x = F.relu(self.fc2(x))
               
               # 행동 확률 분포 생성
               action_probs = F.softmax(self.actor(x), dim=-1)
               
               # 상태 가치 추정
               state_value = self.critic(x)
               
               return action_probs, state_value
            ```
            A2C는 **정책 네트워크**와 **가치 네트워크**를 동시에 학습하여, **장기적인 보상**을 고려한 전략을 세울 수 있습니다.  
            게임과 같은 **확률적, 전략적 요소**를 고려하는 데 있어 유리하며, 한 번의 행동에 대한 보상뿐만 아니라 **전체 게임의 승리**를 목표로 학습합니다.  
            이로 인해 **개별 행동**이 아닌 **전체적인 전략**을 학습하는 데 유리합니다.

         2. **정책 기반 학습의 장점**  <br><br>
            A2C는 **정책 기반 학습**을 사용하여 **지속적인 policy의 개선**이 가능했습니다.  
            특히 **탐험**(exploration)과 **활용**(exploitation)을 적절하게 사용하며 학습할 수 있기 때문에, **확률적**이고 **다양한 패턴**을 가진 대결에서 유리한 결과를 얻을 수 있었습니다.  
            예를 들자면, 상대방이 다양한 방식으로 **블러핑**을 할 때, 이런 변수를 잘 캐치하며 학습할 수 있었습니다.  

      - **한계:**
         1. **정책 업데이트의 불안정성**  <br><br>
            A2C는 **정책**과 **가치**를 업데이트하는 방식에서 **변동성**이 있을 수 있습니다.  
            때때로 **policy network**가 너무 급격하게 업데이트되어 **불안정한 학습**을 초래할 수 있었습니다.  
            특히 **흑과백** 게임에서처럼, **전략의 미세한 차이**가 승패를 가를 때, 정책 업데이트의 불안정성으로 인해 **일관된 성능**을 보장하기 어려웠습니다.  

         2. **Exploration과 Exploitation의 균형 문제**  <br><br>
            위에 설명했듯이 A2C는 **탐험과 활용의 균형**을 잘 맞추는 것이 중요합니다.  
            게임에서 일정한 패턴에 머물러 있다면 **탐험 부족**으로 인해 **새로운 전략**을 학습하는 데 어려움을 겪을 수 있습니다.  
            **흑과백** 게임에서는 상대방의 전략을 예측하는 것이 중요한데, **탐험 부족**은 이를 방해할 수 있습니다.  

         3. **복잡한 Hyper parameter 설정**  <br><br>
            A2C는 **Hyper parameter**에 민감한 알고리즘입니다. **학습률**, **탐험 비율**, **배치 크기** 등 다양한 hyper parameter들이 **모델의 성능에 큰 영향을 미칩니다.**  
            **흑과백**과 같은 게임에서 이를 잘 조정하지 않으면 **훈련이 제대로 되지 않거나 성능이 떨어지는 결과**를 초래할 수 있었습니다.

  - ## ***PPO***

    <img width = "740" height = "300" src="https://github.com/user-attachments/assets/41d8a537-c848-4b19-b43b-9cd8af22062d"> <br>
    ***(본인의 경우는 loss function을 surrogate loss function을 사용했습니다.)***

    - PPO는 **정책 기반 학습의 효율성과 안정성을 극대화**한 알고리즘으로, A2C의 상위호환 격인 모델이라 판단해 적용해보았습니다.
      PPO는 현재 주어진 데이터를 기반으로 policy의 performance를 **최대한 빠르게 향상**시키면서, 동시에 **overshooting은 막고자** 하는 모델입니다.
      해당 모델의 **장점**과 **한계**는 다음과 같습니다.

      - **장점:**
         ```python
         def update(self):
            # 메모리에서 상태, 행동, 보상 추출
            states = torch.FloatTensor([m[0] for m in self.memory]).to(self.device)
            actions = torch.LongTensor([m[1] for m in self.memory]).unsqueeze(1).to(self.device)
            returns = self.compute_returns(rewards, dones)
            
            # 반환값과 이점 계산
            returns = self.compute_returns(rewards)
            advantages = returns - self.value_net(states)
            
            # 정책 네트워크 업데이트
            action_probs = self.policy_net(states)
            ratio = action_probs.gather(1, actions) / action_probs.gather(1, actions).detach()
            
            # PPO 클리핑을 이용한 손실 계산
            policy_loss = -torch.min(
               ratio * advantages, 
               torch.clamp(ratio, 1-self.epsilon, 1+self.epsilon) * advantages
            ).mean()
            
            # 네트워크 파라미터 업데이트
            self.optimizer.zero_grad()
            policy_loss.backward()
            self.optimizer.step()
         ```
         
         1. **정책 업데이트 안정성** <br><br>
            PPO는 **클리핑(clipping)** 기법을 사용해, policy network의 **업데이트 폭을 제한**합니다.
            이로 인해, policy의 급격한 변화를 방지하면서 안정적인 학습이 가능했습니다.
            흑과백 게임처럼 장기적인 전략이 중요한 상황에서도, **변동성을 최소화**하며 점진적인 학습을 수행할 수 있었습니다.

         2. **효율적인 탐험과 활용** <br><br>
            PPO는 policy network를 통해 다양한 행동을 탐색하고, 장기적인 보상을 최대화하는 행동을 학습할 수 있습니다.
            특히 A2C와 달리, 탐험(exploration)과 활용(exploitation)의 균형을 적절히 맞추어,  
            상대방의 행동 패턴을 분석하고 대응 전략을 학습하는 데 효과적이었습니다.

         3. **정책 기반 학습의 장점** <br><br>
            PPO 또한 A2C처럼 policy network를 이용하여 **확률적으로 의사결정**을 하는 모델입니다.
            A2C의 정책 기반 학습 장점을 그대로 PPO 또한 가지고 있습니다.

      - **한계:**

         1. **높은 계산 비용** <br><br>
            PPO는 **배치 학습과 epoch를 기반**으로 policy를 업데이트하므로, 상대적으로 높은 cost가 요구됩니다.
            이는 복잡한 환경에서 **학습 속도를 저하**시킬 수 있으며, **하드웨어 리소스**에 대한 요구사항이 커질 수 있었습니다.

         2. **정책 네트워크에 의존적인 성능** <br><br>
            PPO는 policy network의 **설계와 초기화**에 따라 성능이 크게 달라질 수 있었습니다.
            네트워크 구조가 **복잡하거나 초기 학습이 잘못되면**, 오히려 **비효율적인 전략을 학습**하는 경우도 있었습니다.

         3. **복잡한 Hyper parameter 설정**  <br><br>
            PPO도 A2C처럼 **클리핑 계수**, **Learning rate**, **Epochs** 등의 다양한 **hyper paremeter**가 성능에 직접적인 영향을 미칩니다.
            동적으로도 시도해보고, 계속 여러 값을 테스트해보았지만 아직은 만족 할 수 있는 값은 찾지 못했습니다.

- ## **결론** 

   - 세 가지 중에서는 **PPO 모델과 A2C 모델**을 상대할 때 어려움을 느꼈습니다. 흑과백은 개인적으로 자부해서  
     **80~90% 이상의 승률을 생각**했으나, 약 **60~70%의 승률**을 기록했습니다.  

     생각보다 **예상 외의 선택**을 하는 경우도 잦았고,   
     **압도적으로 지는 판**도 있었습니다. **반대로 매우 쉽게 이기는 판**도 있었습니다.  
     그 부분은 아마 제가 AI 상대하는 법을 학습하지 않았나 싶습니다.  

     개인적으로는 알파고의 근간인 **몬테 카를로 트리 서치를 활용한 모델링**도 해보고 싶었으나,  
     너무 복잡하여서 공부한 다음에 해야겠다는 생각이 들어 **추후에 evaluation하며 진행**해보려 합니다.  
     강화학습에 대해 더 깊게 공부하여서 최적의 hyper parameter를 구하는 방법도 배워보고 싶습니다.
     

## 🛠 기술 스택

- **게임 엔진**: Pygame 2.5.2+
- **AI 프레임워크**: Torch 2.4.1
- **데이터 처리**: NumPy, Torch(Tensor)
- **개발 환경**: Python 3.12+, VScode

## 🚀 향후 계획

- [ ] AI 난이도 다양화 및 학습 개선
- [ ] 게임 UI/UX 개선
- [ ] 추후 멀티플레이 구현 및 배포

## 📝 참조

- https://www.pygame.org/wiki/tutorials?parent= (**pygame**에 대한 공부)
- https://ai-com.tistory.com/ (**강화학습** 모델에 대한 공부)
- https://velog.io/@uonmf97/ (**강화학습** 모델에 대한 공부)
- https://blog.quantylab.com/rl.html (**강화학습** 모델 사진 참조)
- **Thanks to 🤖Chat-GPT🤖 a lot** for error correction!
