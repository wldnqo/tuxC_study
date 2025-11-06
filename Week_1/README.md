# C_Study
c스터디 과제 공지 및 제출을 위한 레포입니다.
---
# 과제 참고사항
## 과제 목표는 `깃에 대한 간단한 체험`, `링크드 리스트 이해하기`, `스스로 구글링 통해 정보 찾아보기`입니다 LLM(chatGPT)는 사용하지 마시고 적어주세요~
#### `모르는 것들`이 있으면 `구글링`을 통해 찾아가면 됩니다 모르는 것들이 있으면 정보를 빠르게 찾아서 학습하고 내것으로 만들면 됩니다 요번 과제를 하다가 익숙하지 않은 것들이 있으면 바로 `검색`하고, `질문`은 언제든지 `카톡`으로 해주세요
#### `https://m.blog.naver.com/coding-abc/222487705914`, 이 블로그를 기반으로 제작한 과제입니다 모르면 찾아보고 빠르게 익히는게 좋다고 생각해요! 참고해주세요
#### `https://printf-hellojudyworld.tistory.com/66` 마크다운 언어
---
# 과제 제출 방법
#### 참고 `https://jtm0609.tistory.com/145`을 참고해서 `<type>: <subject>` 의 형식으로 작성해주세요
#### 1. C_Studty 레포를 `fork` 한뒤 `git clone`으로 vscode/visual studio에서 열어보자
#### 2. `git checkout -b (NAME)`으로 자신의 브랜치를 생성합니다
#### 3. 밑에 명시되있는 세부 구현 기능의 세부 기능별로 `git commit` 및 `git push`를 합니다.
#### 4. `git commit message`는 `컨벤션`을 지켜야합니다
#### 5. 과제를 완성하면 `pull request`를 합니다

---
## 과제
### 요구사항 1
#### 1. `struct`와 `포인터`를 활용하여 `연결 리스트`를 C언어로 구현해보세요
#### 세부 구현 기능
[연결 리스트 정의]
+ [삽입]
- [X] 노드를 맨끝에 삽입하는 함수를 정의하세요
- [X] 노드를 맨앞에 삽입하는 함수를 정의하세요
+ [삭제]
- [X] 특정 값을 입력받아 일치하는 노드를 삭제하세요(특정 값은 key값으로 취급합니다 -> 중복될 수 없다는 말입니다)
+ [출력]
- [X] 모든 연결리스트의 노드의 원소를 순차적으로 출력하는 함수를 정의하세요

### 요구사항 2
- [X] 노드에는 키값과 다음 노드를 가리키는 데이터가 존재해야합니다
- [X] `노드`를 구조체를 활용하여 정의하세요
- [X] 노드의 HEAD와 TAIL은 전역 변수로 지정하세요
- [X] 변수를 나타낼 때는 주석이 없어도 이 변수의 역할을 명확히 나타내게 해주세요

### 요구사항 3
- [X] 과제를 하다가 고민이었던 부분, 몰랐던 부분을 적어주세요. 그리고 그 부분을 어떻게 해결했는지 간단하게만 적어주세요
> 예시 : 노드를 어떻게 연결하는 지 몰랐음 -> 구글링을 통해 다른 사람들 포인터를 통해 다음 노드의 위치를 가리키게 함을 이해 (해결 못했으면, 해결못했다고 적어주세요)


### 요구사항 4
- [X] 프로그램을 기능별로 원리를 간단하게 설명하세요
  + 프로그램의 전체 논리 순서, 각 기능별 동작 원리 등을 README.md 파일 아래 `프로그램 설명`에 Mark Down 언어로 작성해주세요 (전체 프로그램의 흐름, 각 기능들의 원리를 설명하면 되요)
---

#### 예시
+ addNode(10); // key값 10을 받아 노드를 생성해 뒤에 추가한다
+ insertNode(10); // key값 10을 받아 노드를 맨앞에 추가한다
+ deleteNode(10); // key값이 10인 노드를 찾아 제거한다
+ printAll(); // 전체 연결리스트를 출력합니다


### 프로그램 설명
+ typedef struct list
{
	int num;
	struct list* next;

}node; // 노드를 구조체로 구현

+ node* head = NULL; // 노드의 head를 전역변수로 지정
+ node* tail = NULL; // 노드의 tail을 전역변수로 지정

+ s_insert(10); // 10을 노드 맨 앞에 추가
+ e_insert(40); // 40을 노드 맨 뒤에 추가

+ int n; // 특정한 값을 저장할 변수 선언
+ scanf("%d", &n); // 특정한 값 입력
+ delete(n); // 입력 받은 특정한 값 n과 일치하는 노드가 있으면 삭제
+ print(); // 모든 연결리스트의 원소들을 순차적으로 출력하는 함수

+ void delete(n) {
	node* search, * previous; // 입력 받은 특정한 값n과 일치하는 노드를 찾는 search와 일치하는 노드 제외하고 다음 노드로 이어줄 previous 생성.
	search = head; // 연결리스트의 처음부터 찾아야하므로 search는 head로 지정
	previous = NULL; // 연결리스트 처음 부분의 전 부분은 NULL이므로 NULL지정
	while (search != NULL) { // search가 NULL이 될 때까지 즉 연결리스트의 끝이 될 때까지 반복
		if (search->num == n) { // search의 num이 특정한 값 n과 같다면 
			previous = search; // 이전의 previous
			search = search->next;
		}
		else { // search의 num이 특정한 값 n과 같지 않다면
			search = search->next; // search는 다음 연결리스트로 지정
		}
	}
}

+ void s_insert(n) {
	node* temp; //n을 연결리스트 맨 앞에 집어넣기 위해 임시 temp생성
	temp = (node*)malloc(sizeof(node)); // temp 동적할당
	if (head == NULL) { // 연결리스트의 값이 아무것도 없다면
		head = temp; // 연결리스트의 head를 temp로 지정
		temp->num = n; // temp의 num에 n추가
		temp->next = NULL; // temp가 다음으로 가리킬 곳은 끝이기 때문에 NULL로 지정.
	}
	else { // 연결리스트의 값이 있다면
		temp->next = head; // 맨 앞에 추가하기 위해서 temp의 next가 head를 가리키도록.
		temp->num = n; // temp의 num에 n추가
	}

}

+ void e_insert(n) {
	node* temp; //n을 연결리스트 맨 뒤에 집어넣기 위해 임시 temp생성
	temp = (node*)malloc(sizeof(node)); // temp 동적할당
	node* search; // 맨 뒤를 찾기 위한 search 생성
	search = head; // 현재 연결리스트의 맨 앞을 가리키도록.
	while (search != NULL) { //search 노드가 연결리스트의 끝을 가리킬때까지 반복.
		search = search->next; //search 노드가 연결리스트의 끝을 가리킬때까지 반복.
	}
	search->next = temp->num; //search노드가 연결리스트의 끝을 가리키고 있으므로 삽입할 temp노드의 num을 가리키도록 함.
	temp->num = n; // temp노드의 num에 n을 삽입
	temp->next = NULL; // temp노드가 다음으로 가리킬 부분은 연결리스트의 끝이므로 NULL 지정

}

+ void print() {
	node* search;
	search = head;
	while (search != NULL) {
		printf("%d\n", search->num);
		search = search->next;
	}
} // 찾는 노드 생성, search 노드는 head노드를 가리킴, search 노드가 NULL을 가리킬 때까지 search가 가리키는 노드의 값을 출력 후 search는 search의 다음으로 연결된 리스트를 가리킴. search 노드가 NULL을 가리키면 즉 연결리스트의 끝을 가리키면 반복 종료.



