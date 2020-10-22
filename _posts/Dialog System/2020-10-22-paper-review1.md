---
layout: post
title:  "[논문 리뷰] Agenda-Based User Simulation for Bootstrapping a POMDP Dialogue System"
data:   2020-10-22 13:00:00 
categories: DialogSystem
comments: true
---

## 0. Abstract

---
(논문 링크: [http://mi.eng.cam.ac.uk/~sjy/papers/stwy07.pdf](http://mi.eng.cam.ac.uk/~sjy/papers/stwy07.pdf))

(코드 링크: [https://github.com/truthless11/GDPL](https://github.com/truthless11/GDPL)를 참조)

(저자: Schatzmann et al., 2007 NAACL)

---
  
&nbsp;
  
  
이번 포스팅에서는 Task-oriented dialog에서 정말 많이 쓰이는 Agenda-based user simulator에 대해 알아보려고 합니다. 2007년에 나온 논문이지만 현재까지 여러 논문에서 많이 쓰이고 있어서 꼭 알아두어야 하는 논문입니다. 이 논문에서 지적하는 기존의 statistical dialogue manager의 가장 큰 문제점은 bootstrapping에 있다고 얘기합니다.


&nbsp;


여기서 bootstrap이란 통계쪽에서 사용되는 용어로 데이터에서 얻어진 통계량의 표본오차를 확률 분포의 가정을 두지 않고 non-parametric하게 평가하기 위한 방법을 의미합니다. 쉽게말해서 주어진 데이터셋을 모집단을 대표하는 독립표본으로 가정하고, 그 자료로부터 중복을 허용한 무작위 재추출로 얻어진 통계량을 의미합니다. 주어진 데이터에 대해 평균과 표준편차등의 통계량을 계산하겠다는 의미입니다.


&nbsp;


이 논문에서 제안하는 user simulator는 이러한 bootstrapping 문제를 해결하기 위한 새로운 probabilistic agenda-based method라고 소개하고 있습니다. 여기서 나오는 agenda는 아래에서 자세히 설명 드리겠습니다. 실험같은 경우는 task completion rate를 지표로 평가하였으며 무려 90%의 성능을 보여준다고 말하고 있습니다.  


---

## 1. Background and Introduction

---

### 1.1 Bootstrapping Statistical Dialogue Managers

---

이 장에서는 기존의 Dialogue Manager(DM)를 statistical approach로 디자인 하는 문제점을 나열하고 있습니다.   
