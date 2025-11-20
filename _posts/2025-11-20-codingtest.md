---
layout: post
title: 코딩 테스트 준비
date: 2025-11-20
categories: [기타]
tags: [Misc,C++]
---

# 난이도
- 프로그래머스 3레벨 정도 까지
1. 0레벨: 기본 문법 위주
2. 1레벨: 맞는 STL을 사용하는지
3. 2레벨: 문제풀이 방식이 필요

# 준비 방법
- 많은 문제 풀기
- STL 사용 익히기

# 문제 해결 방식
- 어떻게 재귀할 것인가
- 2레벨까지는 보통 아래 4개로 해결됨

## Greedy
- 지금 당장 최적처럼 보이는 행동을 일단 하고 봄
- 최적화된 방법이 아니어도 될 때
- 예시 : A* 알고리즘

## BackTracking
- 최적해 나올 때 까지 순서대로 체크
- 예시 : DFS

### Greedy vs BackTracking
- 빠름 vs 느림
- 최적 보장 x vs 최적 보장 o

## Divide and Conquer
- 같은 로직으로 나누면서 명령 하달 (하향식 접근)
- 예시 : merge sort, octree 충돌 검사

## Dynamic Programming
- Memoization vs Tabulation
- 가면서 필요한 것들을 테이블에 메모 vs 테이블 다 만들어 놓고 진행

# STL 사용 팁
해시는 unordered_map, unordered_set (multi도)
이진탐색트리(BST)는 map, set (multi도)

## 기본 외에 게임쪽에서 나오는 것들
- AABB, OBB
- 보로노이
- 돌로네 삼각분할
- A*
- 플러드 필
