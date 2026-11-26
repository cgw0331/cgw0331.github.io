---
layout: post
title: "C 동적 할당과 연결 리스트 연습"
date: 2019-12-03 12:00:00+0900
description: 1학년 2학기 C프로그래밍2 시험공부를 하며 직접 짜본 연결 리스트 코드.
tags: bs
categories: dev
---

1학년 2학기 C프로그래밍2 수업에서 동적 메모리 할당과 연결 리스트를 배울 때, 교재 예제를 따라 쳐본 다음 주제를 바꿔서 직접 다시 짜본 코드입니다. 주석은 그때 이해하려고 달아둔 것을 거의 그대로 두었습니다.

아이템 이름과 레어도를 입력받아 연결 리스트로 이어 붙이고, 전부 출력한 뒤 메모리를 반납합니다.

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define SIZE 50

typedef struct Item {
	int rare;
	char name[SIZE];
	struct Item *link;
} item;

int main(void) {
	item *list = NULL;
	item *p, *prev, *next;
	char buffer[SIZE];
	int rare;

	while (1) {
		printf("생성할 아이템 이름을 적어주세요 (끝내려면 엔터): ");
		gets_s(buffer, SIZE);
		if (buffer[0] == '\0')
			break; // while 문 탈출

		p = (item *)malloc(sizeof(item));
		strcpy(p->name, buffer);

		printf("아이템에 레어도를 입력해주세요(숫자) : ");
		gets_s(buffer, SIZE);
		rare = atoi(buffer); // 바로 p->rare = atoi(buffer)를 한다면 오류가 발생할까?
		p->rare = rare;

		if (list == NULL) // 처음에는 p의 주소를 list에 대입. 구조체 포인터니까
			list = p; // list는 처음 만든 구조체를 가리킨 채 아무 일도 하지 않음
		else
			prev->link = p; // link가 p의 주소를 가리키게 함
		p->link = NULL; // 링크가 아무것도 가리키지 않게 만듦
		prev = p; // prev는 제일 마지막에 생성된 구조체
	}
	printf("\n");

	// 연결 리스트에 들어있는 정보를 모두 출력한다
	p = list; // 처음 구조체를 가리킴
	while (p != NULL) {
		printf("[%s, %d]->", p->name, p->rare);
		p = p->link; // 링크가 가리키는 구조체로 이동
	}
	printf("\n");

	// 동적 할당을 반납한다. 안 하면 메모리 누수가 생김
	p = list;
	while (p != NULL) {
		next = p->link; // 다음 구조체를 먼저 기억해 둠
		free(p);
		p = next;
	}

	return 0;
}
```
