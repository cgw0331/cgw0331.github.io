---
layout: post
title: 사과박스 게임 자동 플레이 봇
date: 2025-05-24 12:00:00+0900
description: 화면을 캡처해서 숫자를 읽고 합이 10이 되는 영역을 찾아 드래그하는 봇.
tags: phd
categories: game
---

🚧 초안입니다. 정리 중이에요.

사과박스(합이 10이 되는 숫자들을 드래그해서 지우는) 게임을 자동으로 플레이하는 봇입니다.

화면을 캡처해서 숫자를 인식하고, 합이 10이 되는 직사각형 영역을 찾아 마우스로 드래그하는 구조입니다. 템플릿 매칭으로 숫자를 읽었습니다.

예전에 DQN으로 학습시켜 보려고 했는데, 직접 짠 탐색 알고리즘이 더 잘해서 강화학습 쪽은 접었습니다.

- [Fruit_Box_](https://github.com/cgw0331/Fruit_Box_) · [fruitGamebyDQN](https://github.com/cgw0331/fruitGamebyDQN)

<!-- TODO: 탐색 알고리즘 설명, 실행 영상 -->
