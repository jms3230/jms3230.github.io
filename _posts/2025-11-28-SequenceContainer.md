---
layout: post
title: STL 소개
date: 2025-11-28
categories: [C++]
tags: [C++,STL]
---
### Vector
- 시퀀스, 배열기반
- https://en.cppreference.com/w/cpp/container/vector
- `typeid(vector<int>::size_type).name()`으로 타입 이름 확인
- 원소들이 늘어갈 때 마다 capacity를 늘려가는 정책이 컴파일러마다 다를 수 있음
	- ex) 두배, 이전 메모리의 절반 추가 등등
- capacity를 0으로 만들고 싶다면 크기 0인 임시객체와 swap
	- `vector<int>().swap(v);`
- `at()`과 `[]`의 차이
	- `at()`은 범위점검해서 안전 `[]`는 점검 안해서 속도 빠름
	- `at()`은 범위 넘어가면 `out_of_range` 예외 발생
	- `catch(out_of_range& e){cout<<e.what()<<endl;}`로 출력 가능
- iterator는 `int*`같은 포인터와 비슷
- `const_iterator`는 `const int*`같은 포인터와 비슷
- `const vector<int>::iterator` 하면 `int* const` 같은 형태와 비슷해져서 이동이 안되므로 주의
	- 정확한 구문은 `vector<int>::const_iterator`
- insert는 가리키는 위치에 삽입하고 그 위치 그대로 반환
	- iterator로 범위 넣어서 여러 원소 삽입도 가능
	- insert외에도 erase, assign도 범위로 여러 원소 삽입 가능
- 비교연산 `<`,`>`등
	- 문자열 비교처럼 비교
	- 두 원소들을 각각 인덱스별로 비교해서 큰게 먼저 나온 쪽이 큰 벡터
### Deque
- 시퀀스, 배열기반
- Double-ended queue
- https://en.cppreference.com/w/cpp/container/deque
- 여러 메모리 블록 할당 후 하나처럼 보이게 함
	- 메모리가 더 필요하면 vector처럼 큰 배열 새로 만들어서 옮기지 않고 새 블록 하나만 추가
- vector와 다르게 `push_front`, `pop_front`가짐
- 중간 insert - 앞, 뒤 중 원소 개수 적은 쪽으로 밀어내면서 필요한 메모리 블록 생성

### List
- 시퀀스, 노드기반
- 이중연결리스트
- https://en.cppreference.com/w/cpp/container/list
- `at`함수나 임의접근반복자`[]`사용 못하므로 양방향 반복자 연산`++`,`--`사용
- insert,erase가 반복자 무효화 하지 않음(vector, deque는 메모리 재할당으로 무효화 가능성 있음)
	- 원소 자체는 사라지지 않는다는 의미
	- erase시 가리키는 원소가 List 바깥으로 나가게 되고 insert시 원래 그자리에 있던 원소 가리킴
- 원소로 검색해서 제거 가능한 `remove`, `remove_if` 함수 있음
	- remove_if는 단항 조건자를 넣어서 참일 때 제거
	- 조건자는 bool반환하는 함수류(함수, 함수포인터, 함수객체)
- 잘라붙이는 `splice` 함수 있음
	- 리스트 통째로 붙이기/반복자가 가리키는 원소 붙이기/반복자 범위 붙이기 가능
	- 잘라 붙이므로 기존 원소 사라짐
- 뒤집기 `reverse`함수
- 인접한 중복원소 제거하는 `unique` 함수
	- 중복을 모두 없애려면 정렬한 후에 unique 사용
	- 이항조건자 사용하는 버전도 있어서 참일 경우 뒤의 원소 제거 가능
- 정렬하는 `sort` 함수
	- 기본은 오름차순(less 조건자와 같음)
	- 조건자 넣어서 정렬기준 변경 가능 ex)`greater<int>()`
	- greater, less 조건자는 'functional'이라는 헤더에 들어가지만 보통 컨테이너 헤더에서 포함함
- 합병하는 `merge` 함수
	- 원소를 합치면서 정렬
	- 두 리스트가 미리 같은 방식으로 정렬 되어있어야 제대로 동작
		- 안되어있으면 동작하긴 해도 결과가 이상해짐
	- 정렬이 오름차순인 less 가 아니면 조건자 넣는 버전 사용해서 조건자 넣어줌




