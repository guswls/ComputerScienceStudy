## 자료구조 - Heap
## 힙(Heap)

힙 자료구조는 완전 이진 트리를 기초로 하는 자료구조이다.

완전 이진트리는 마지막을 제외한 모든 노드에서 자식들이 꽉 채워진 이진트리를 말한다.

<img width="482" alt="스크린샷 2021-12-19 오후 7 06 51" src="https://user-images.githubusercontent.com/54795404/146671230-e500fb5c-cb74-472b-a752-08bfe3eee806.png">


위와 같은 형태를 띄고 있으며, 몇가지 특징들을 가지고 있다.

1. 힙은 최대힙(Max heap)과 최소힙(Min Heap)으로 나눠진다. 최대힙은 부모노드의 값이 자식노드들의 값보다 항상 크고, 최소힙은 부모노드의 값이 자식 노드의 값보다 항상 작다.(위 그림은 최대힙의 예시)
2. 힙은 중복값을 허용한다. 힙은 최댓값 또는 최솟값을 쉽게 뽑기 위한 자료구조 임으로 중복을 허용한다.

### **1-2. 힙의 종류**

- **최대 힙(Max Heap):** (완전 이진 트리) + (부모 노드 > 자식 노드)
- **최소 힙(Min Heap):** (완전 이진 트리) + (부모 노드 < 자식 노드)

힙은 위처럼 두 종류로 나뉜다.

다시 풀어서 설명하자면

최대 힙은 완전 이진 트리이면서 부모 노드가 자식 노드보다 큰 트리

최소 힙은 완전 이진 트리이면서 부모 노드가 자식 노드보다 작은 트리이다.

보통 힙이라고 하면 일반적으로 최대 힙을 의미한다.

### **1-3. 힙의 활용**

힙은 **최댓값 혹은 최솟값을 빠르게 찾아내기에 유리**한 자료구조이다.

그래서 우선순위 큐를 구현할 때 쓰이기도 하고

허프만 코드를 구현할 때도 쓰이고

힙 정렬을 구현할 때도 쓰인다.

### 힙을 배열로 구현하기

힙은 대체적으로 배열로 구현된다. 완전이진트리를 기본으로 하기 때문에 비어있는 공간이 없어 배열로 구현하기에 용이하다.

아래 그림과 같이 루트노드를 배열의 0번 index에 저장하고, 각 노드를 기점으로 **왼쪽 자식노드는 *a*[*i*∗2+1], 오른쪽 자식노드는 *a*[*i*∗2+2]** 의 index에 저장된다. 
또한 특정 index의 노드에서 **부모노드는 *a*[(*i*−1)//2]**로 찾을 수 있다.


<img width="513" alt="스크린샷 2021-12-19 오후 7 07 25" src="https://user-images.githubusercontent.com/54795404/146671241-498d6230-058b-4b2f-a40d-ce2a46f16054.png">


## 삽입과 삭제로 깨진 힙을 재구조화하기(heapify)

최대힙의 부모노드는 항상 자식노드의 값보다 크다는 조건을 가지고 있다.

하지만 힙에서 삽입 또는 삭제가 일어나게 되면 경우에 따라 최대힙의 조건이 깨질 수 있다. —> 재구조화하여 노드들의 위치를 바꾸자

삽입과 삭제의 경우 모두 **연산 자체는 *O*(1)**로 작동하지만 heapify의 과정을 거치기 때문에 ***O*(*logn*)의 시간복잡도**를 가지게 된다.

### 삽입 과정 구현과정

먼저 삽입과정을 보면 새로운노드 [11]이 삽입되었을 경우이다.

새로운 노드는 리프토드가 아니면서 가장 말단에 있는 노드의 자식 노드로 추가된다. 이후, 부모노드와 비교하면서 재구조화 과정을 수행한다.

<img width="514" alt="스크린샷 2021-12-19 오후 7 07 55" src="https://user-images.githubusercontent.com/54795404/146671258-df4e0ecb-d4e4-4223-9dba-6fe42bc3d0c0.png">


### 삭제과정 구현과정

아래 그림은 루트 노드가 삭제되었을 경우인다. 루트 노드가 삭제되면 가장 말단노드를 루트노드자리에 대체한 후 재구조화 과정을 수행한다.

(힙으로 구현된 우선순위 큐에서도 가장 우선순위가 큰 루트노드를 주로 삭제한다. )

<img width="512" alt="스크린샷 2021-12-19 오후 7 08 19" src="https://user-images.githubusercontent.com/54795404/146671268-c2b018a2-576d-4fd5-abdb-b21e91d4f524.png">
