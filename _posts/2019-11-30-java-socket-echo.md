---
layout: post
title: 자바 소켓 통신 - 에코 서버와 클라이언트
date: 2019-11-30 12:00:00+0900
description: 1학년 2학기 자바 과제로 만든 TCP 에코 서버와 Swing 클라이언트.
tags: bs
categories: dev
---

🚧 초안입니다. 정리 중이에요.

`java.net.Socket`과 `ServerSocket`으로 만든 에코 서버/클라이언트 과제입니다. 클라이언트는 `JFrame`에 `JTextArea`와 `JTextField`를 올려서, 입력한 문자열을 서버로 보내고 되돌아온 문자열을 텍스트 영역에 붙이는 구조였습니다.

기숙사 랜선 IP를 코드에 직접 박아두고 친구 컴퓨터와 연결해서 테스트했던 기억이 납니다.

<!-- TODO: 코드 정리, 포트/IP 하드코딩 대신 인자로 받도록 다듬기 -->
