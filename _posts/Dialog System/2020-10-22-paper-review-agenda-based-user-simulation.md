---
layout: post
title:  "[논문 리뷰] Agenda-Based User Simulation for Bootstrapping a POMDP Dialogue System"
data:   2020-10-22 13:00:00 
categories: DialogSystem
use_math: true
comments: true
---

## 0. Abstract

---
(논문 링크: [http://mi.eng.cam.ac.uk/~sjy/papers/stwy07.pdf](http://mi.eng.cam.ac.uk/~sjy/papers/stwy07.pdf))

(코드 링크: [https://github.com/truthless11/GDPL](https://github.com/truthless11/GDPL)를 참조)

(저자: Schatzmann et al., 2007 NAACL)

---
  
&nbsp;
  
  
이번 포스팅에서는 Task-oriented dialog에서 정말 많이 쓰이는 Agenda-based user simulator에 대해 알아보려고 합니다. 2007년에 나온 논문이지만 현재까지 여러 논문에서 많이 쓰이고 있고 저도 최근에 논문을 쓰면서 이 시뮬레이터로 실험을 진행하였습니다. 물론 10년도 더 된 논문이니 이 점을 감안하고 보셔야하지만 꼭 알아두셔야 하는 논문입니다. 그럼 시작하겠습니다. 


&nbsp;


이 논문에서 지적하는 기존의 statistical dialogue manager의 가장 큰 문제점은 <span style="color:DeepSkyBlue">bootstrapping</span>에 있다고 얘기합니다. 여기서 <span style="color:DeepSkyBlue">bootstrapping</span>이란 통계쪽에서 사용되는 용어로 데이터에서 얻어진 통계량의 표본오차를 확률 분포의 가정을 두지 않고 non-parametric하게 평가하기 위한 방법을 의미합니다. 쉽게말해서 주어진 데이터셋을 모집단을 대표하는 독립표본으로 가정하고, 그 자료로부터 중복을 허용한 무작위 재추출로 얻어진 통계량을 의미합니다. 주어진 데이터에 대해 평균과 표준편차등의 통계량을 계산하겠다는 의미입니다.


&nbsp;


이 논문에서 제안하는 user simulator는 이러한 bootstrapping 문제를 해결하기 위한 새로운 probabilistic agenda-based method라고 소개하고 있습니다. 여기서 나오는 agenda는 아래에서 자세히 설명 드리겠습니다. 실험같은 경우는 task completion rate를 지표로 평가하였으며 무려 90%의 성능을 보여준다고 말하고 있습니다.  


---

## 1. Background and Introduction

---

### 1.1 Bootstrapping Statistical Dialogue Managers

---

이 장에서는 기존의 Dialogue Manager(DM)를 statistical approach로 디자인 하는 문제점, 즉 statistical dialogue managers를 bootstrapping하는 문제점을 나열하고 있습니다. 통계기반의 DM의 핵심은 design criteria를 objective reward function으로 formalize 하는 능력과 real dialogue data로부터 optimal policy를 학습하는 것에 있다고 합니다. 


&nbsp;


하지만, DM을 학습시키기 위한 각 도메인에 해당하는 적절한 데이터가 없다는 점을 지적합니다. 기존의 <span style="color:DeepSkyBlue">Wizard-of-Oz(WoZ)</span>를 통해 dialogue를 기록할 수 있지만 시간이 많이 소요되고, human-human 대화밖에 기록할 수 없다는 단점이 있고 human-computer dialog가 필요한 이 task에는 적절하지 않다는 점을 지적합니다. 


&nbsp;


human-computer dialogue를 기록하기위한 기존의 handcrafted DM prototype을 이용하면 되지만 앞에서 말한 데이터 부족으로 인한 DM을 학습할 수 없다고 말합니다. 심지어 위의 두가지 방식으로 기록한 corpus는 statistical DM을 학습하기에 많이 부족한 편입니다 ($10^4$ 이상이 필요하지만 그 당시 $10^3$밖에 존재하지 않았음). 

---

### 1.2 User Simulation-Based Training

---

User Simulation-Based Training은 다음과 같은 두 단계로 진행됩니다. (1) 적은 대화 데이터로 user model 학습. (2) 


&nbsp;


하지만, DM을 학습시키기 위한 각 도메인에 해당하는 적절한 데이터가 없다는 점을 지적합니다. 기존의 <span style="color:DeepSkyBlue">Wizard-of-Oz(WoZ)</span>를 통해 dialogue를 기록할 수 있지만 시간이 많이 소요되고, human-human 대화밖에 기록할 수 없다는 단점이 있고 human-computer dialog가 필요한 이 task에는 적절하지 않다는 점을 지적합니다. 


&nbsp;


human-computer dialogue를 기록하기위한 기존의 handcrafted DM prototype을 이용하면 되지만 앞에서 말한 데이터 부족으로 인한 DM을 학습할 수 없다고 말합니다. 심지어 위의 두가지 방식으로 기록한 corpus는 statistical DM을 학습하기에 많이 부족한 편입니다 ($10^4$ 이상이 필요하지만 그 당시 $10^3$밖에 존재하지 않았음). 




