---
layout: post
title: 소스코드 빌드에 관하여
date: 2025-11-24
categories: [Computer Science]
tags: [C++, Build]
---
# 빌드 과정
- 소스코드 -> 빌드 -> 어셈블리어
## 빌드 4가지 과정
- Preprocessing
- Compilation
- Assemble
- Linking
### Postprocessing
1. `#include<iostream>` : iostream 파일 복사해서 해당 위치에 붙여넣기
	- `<>`로 불러오기 위해서는 include path 내에 파일이 있어야함
2. `#if, #elif, #else,#endif` : 조건에 따라 컴파일
3. `#define텍

### Compilation
- 소스코드를 각 CPU아키텍쳐에 맞는 어셈블리어로 변환
#### CPU Architecture
1. x86, x64
	- 인텔, AMD
2. ARM
	- 애플, 스냅드래곤, 미디어텍
### Assemble
- 어셈블리어로 된 코드를 실행 가능한 오브젝트 파일(.o)로 변환
### Linking
- 여러 오브젝트 파일을 하나의 실행 파일(.exe)로 연결
## C#의 경우
- 결과물이 Virtual Machine용 코드
- CPU 아키텍쳐 별로 Virtual Machine이 다름
- 실행 시, virtual machine이 코드를 실행해줌
- virtual machine이 메모리 관리를 하므로 포인터가 없음

## 게임 엔진에서 스크립트 작성 후 에디터에서 테스트 할 때
- Unreal : 바뀐 스크립트만 오브젝트 파일로 만들어줌
- Unity : C# 스크립트를 인터프리터로 실행할 수 있도록 되어있다고 함
- 최종 빌드와 테스트환경에서 차이가 발생할 수 있음

## EXE파일을 더블클릭하면...
1. 소스코드를 메모리 구조의 코드 영역에 복사
	- 제일 낮은 영역(보통 0x00000000)에 복사됨
2. 프로세스가 코드 처음 실행 위치를 갖게됨(아까의 0x00000000)
3. main함수가 저 시작 위치에 옴
4. ProgramCounter(PC)가 이동하며 명령어 실행
5. 함수 호출시 Stack영역에 돌아올 위치를 저장하고 종료 시 PC를 그 위치로 되돌림
6. 다형성을 구현할 때는 가상함수테이블을 사용함
	- 어느 자식의 함수쪽에 PC를 위치시켜야 하는지 모르기 때문에 호출시에 참고해야함
	- 클래스내에 하나라도 virtual 함수가 있으면 가상함수 테이블이 생성됨
	- CPU는 가상함수테이블이라는 개념을 모름. 컴파일러의 영역
	- 자식 클래스 인스턴스가 만들어질 때는 부모를 생성하고 자식 부분을 붙이게 됨
	- 부모에서 vtable에 virtual함수 주소 넣어둠
	- 자식에서 함수 override 하면 vtable의 주소를 override 
	- `Monster::Attack()` 호출과 그냥 `Attack()` 호출이 vtable 조회여부에 따라 속도 차이가 난다는데 원리가 명확하지 않음
## 추가로 살펴볼 것
- 멀티 프로세스, 멀티 스레드
- CPU, GPU의 협업과정
	- Command Queue, Batch, Render Pipeline
	- Direct X나 Open GL이 어떻게 돌아가는지