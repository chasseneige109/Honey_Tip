`set`은 자주 쓰이는 자료구조인데,  
C++에서의 `set`은 **자동 정렬 + 중복 제거** 기능을 가진 컨테이너야.  
내부 구조는 **이진 탐색 트리(BST)**를 기반으로 동작해.

---

## ✅ C++ `set`의 내부 구조

### 📦 C++ STL `set`은 내부적으로 **Red-Black Tree (레드-블랙 트리)**로 구현돼 있어.

|특징|설명|
|---|---|
|이진 탐색 트리|왼쪽 < 부모 < 오른쪽|
|레드-블랙 트리|**균형 잡힌 BST** → 최악의 경우에도 O(log n) 보장|
|자동 정렬|삽입할 때마다 정렬된 순서 유지|
|중복 허용 안 함|`insert(3)` 두 번 해도 한 번만 저장됨|

---

✅ 예시

#include <iostream>
#include <set>
using namespace std;

int main() {
    set<int> s;
    s.insert(3);
    s.insert(1);
    s.insert(5);
    s.insert(3); // 중복 → 무시됨

    for (int x : s) {
        cout << x << " ";  // 1 3 5 (자동 정렬됨)
    }
}
