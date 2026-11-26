---
layout: post
title: 톰슨 샘플링 정리
date: 2023-05-02 12:00:00+0900
description: 멀티 암 밴딧 문제와 톰슨 샘플링, UCB를 공부하며 적어둔 메모.
tags: ms
categories: research
---

석사 1학기에 톰슨 샘플링을 다목적 분자 최적화에 적용해 보려고 공부하면서 적어둔 메모입니다.

## 멀티 암 밴딧 문제

- 톰슨 샘플링은 멀티 암 밴딧(multi-armed bandit) 문제에서 쓰이는 확률적인 알고리즘이다.
- 강화학습과 온라인 러닝 문제의 한 분류이다.
- 멀티 암 밴딧 문제는 여러 슬롯머신 중 어떤 arm을 당길지 결정하는 겜블러에 비유할 수 있다. 최대 보상을 주는 arm을 당기는 것이 목표이다.
- 각 arm은 알려지지 않은 확률 분포로부터 보상을 제공한다.
- 목표는 탐험(exploration)과 활용(exploitation)의 균형을 맞추는 가장 효과적인 전략을 찾는 것이다.

## 톰슨 샘플링이 동작하는 방식

- 각 arm의 expected reward에 대한 확률 분포를 유지한다. 즉 reward에 대한 확률 분포를 가지고 있어야 한다.
- 이 분포들은 매 시행마다 arm을 당겼을 때 나오는 새로운 정보로 업데이트된다.
- 각 스텝마다 알고리즘은 각 arm의 posterior distribution에서 샘플을 하나씩 뽑고, 가장 높은 값의 샘플이 나온 arm을 선택한다.
- 이 방식은 true reward distribution에 대한 불확실성을 고려하면서 탐험과 활용 사이의 균형을 자연스럽게 맞춰준다.

## 톰슨 샘플링을 쓰기 위한 조건

1. 일련의 의사결정에 대한 누적 보상을 최대화하는 것이 목표인 멀티 암 밴딧 문제여야 한다.
2. 각 arm의 reward distribution을 알고 있거나 사전분포(prior distribution)가 할당되어 있어야 한다. 흔히 베르누이 밴딧(이진 보상)에는 Beta 분포를, 정규 분포 보상에는 가우스 분포를 사전분포로 쓴다.
3. 관측된 데이터로 각 arm의 확률 분포를 업데이트할 수 있어야 한다.
4. 에이전트가 업데이트된 분포에서 샘플을 뽑을 수 있어야 하고, 가장 높은 값의 샘플을 만든 arm을 선택할 수 있어야 한다.

## UCB 알고리즘과 비교

- 매 턴마다 `mean + exploration bonus`가 가장 큰 arm을 당긴다. arm마다 값이 하나씩 정해진다.
- 탐사 보너스는 그 arm을 당긴 횟수(n_a)가 늘수록 감소하고, 모든 arm을 당긴 총 횟수(t)가 늘수록 천천히 증가한다.

## 베르누이 보상일 때

- 톰슨 샘플링은 posterior에서 나온 샘플을 기반으로 arm을 고른다.
- 베르누이 분포는 파라미터가 하나뿐이다.
- 파라미터가 하나인 분포의 사전분포로는 보통 Beta 분포를 쓴다. 성공과 실패 횟수만 세면 되는 분포이기 때문이다.

## 참고

- Choi, J., Seo, S., Choi, S., Piao, S., Park, C., Ryu, S. J., Kim, B. J., & Park, S. (2023). ReBADD-SE: Multi-objective molecular optimisation using SELFIES fragment and off-policy self-critical sequence training. _Computers in Biology and Medicine_. <https://doi.org/10.1016/j.compbiomed.2023.106721>
