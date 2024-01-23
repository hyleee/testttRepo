# **📌1. 개요**

**자가 균형 이진트리**

일반 이진 트리에서 자식들이 한쪽으로 치우치는 것을 막기 위한 균형 기능이 추가된 트리

**자가 균형 이진트리의 종류**

- AVL트리 : 자식의 depth를 이용
- Red Black Tree : 노드의 색을 이용

| <img src=".\img\binary_tree.png"> | <img src=".\img\binary_tree_2.png"> |
| --------------------------------- | ----------------------------------- |

당연히 트리를 압축해서 빈틈 없이 꽉꽉 채워 넣으면 탐색 횟수는 당연히 줄어들겠죠?

하지만 현실적으로 저장, 삭제 작업은 트리의 상태를 보며 하는 작업이 아니므로,, 아무 값이든 들어올 수 있고, 어떤 값이든 나갈 수 있어야 합니다.

---

# **📌 2. 정의**

## 🌳 2.1 모든 노드는 red / black 의 색을 갖는다.

아래는 해당 규칙을 어긴 케이스이다.

<img src=".\img\rbtree3.png">

## 🌳 2.2 모든 NIL 노드는 black이다. (null은 black으로 간주)

<img src =".\img\rbtree4.png">

### 💡 왜 필요할까?

RB트리 구현 시 부모의 형제나, 형제의 자식 노드를 확인해야 하는 경우가 있다. 이때 형제에게 자식이 없다던지 하는 예외를 매번 처리하게 되면 구현 양이 많아진다. 모든 색 체크 시 if null > black, else > check color ... ~~귀찮죠?~~

그래서 null을 의미하는 노드를 만들어두고 그 친구의 색을 black으로 만드는 방법 고안!

새로운 노드를 만들 때도 우선 새로운 노드의 부모 자식을 모두 NIL로 일단 채우고, 연결하는 방식 채택

RB 트리에서 leaf 노드는 nil 노드

관습적으로 NIL 노드는 그림으로 표현시 생략한다.

## 🌳 2.3모든 red는 black 자식을 갖는다. (red의 부모가 red 일수는 없다)

아래는 RB트리에서 가능한 모든 경우의 수이다.

<img src =".\img\rbtree1.png">

아래는 올바르지 않은 RB 트리의 예시이다.

<img src =".\img\rbtree2.png">

## 🌳 2.4 임의의 노드에서 자손 nil노드들까지 향하는 모든 경로는 모두 같은 수의 black 노드가 존재한다.(자기 자신은 count 제외)

<img src =".\img\rbtree5.png">

시작 점에서 이동 가능한 모든 경로를 고려했을 때, 만나는 black의 개수를 세보자. 이 때 모두 같은 값을 가져야한다는 성질. 해당 예시에서는 그 값이 1

<img src =".\img\rbtree6.png">

아래 예시는 그 값이 2

<img src =".\img\rbtree7.png">

### 💡 2.4.1 node x의 black height

노드 x에서 임의의 자손 nil 노드까지 내려가는 경로에서 black 수 (자기 자신은 카운트 제외) **2.4** 속성을 만족해야 성립하는 개념

### 💡 2.4.2 색을 바꾸면서도 2.4 속성 유지하기

RB tree가 **2.4** 속성을 만족하고, 두 자녀가 같은 색을 가질 때, 부모와 두 자녀의 색을 바꿔줘도 해당 속성을 여전히 만족한다.
<img src=".\img\rbtree9.png"> | <img src=".\img\rbtree8.png">
---|---|

# **📌3. 삽입**

## 🌳 3.0 삽입 전 RB 트리 속성 만족한 상태

## 🌳 3.1 삽입 방식은 일반 BST와 동일

## 🌳 3.2 삽입 후 RB 트리 위반 여부 확인

### 💡 3.2.1

### 💡 3.2.2 red 삽입 후 루트 노드 black 위반

루트 노드를 black으로 바꾼다.

## 🌳 3.3 RB 트리 속성을 위반했다면 재조정

## 🌳 3.4 RB 트리 속성을 다시 만족

# **📌4. 삭제**

출처 : https://dev-game-standalone.tistory.com/92, https://youtu.be/2MdsebfJOyM?si=PgO6FSy5IAHDNpd5


지금 추가한 내용

 출처 : https://dev-game-standalone.tistory.com/92, https://youtu.be/2MdsebfJOyM?si=PgO6FSy5IAHDNpd5 

