## 🔍 예시

```
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<int> s;
    s.insert(5);
    s.insert(3);
    s.insert(8);
    s.insert(5);  // 중복 → 무시됨
```

## 🔍 특징

- **중복을 허용하지 않음**
    
- **자동 정렬됨 (기본: 오름차순)**
    
- 내부는 이진 탐색 트리(Red-Black Tree) 기반 → 시간 복잡도 O(log N)


## 🔍 지원하는 함수

| 함수               | 설명                      |
| ---------------- | ----------------------- |
| `insert(value)`  | 값 추가 (중복 시 무시됨)         |
| `erase(value)`   | 값 제거                    |
| `find(value)`    | 값 찾기 (없으면 `end()` 반환)   |
| `count(value)`   | 값의 개수 (set은 0 또는 1만 나옴) |
| `size()`         | 전체 원소 개수                |
| `clear()`        | 전부 삭제                   |
| `empty()`        | 비었는지 확인                 |
| `begin(), end()` | 반복자 (iterator)          |

## ✅ `unordered_set`에 **많은 데이터** 넣을 때
    
- **속도 안정화** (특히 find/insert 반복) 를 위한 **고급 최적화**
    


`unordered_set<string> s; s.reserve(1000000);             // 미리 충분한 공간 확보 s.max_load_factor(0.7);         // 충돌 줄여서 성능 향상`

> 특히 `백준` 같이 **시간 아슬아슬한 대형 입력 문제**에서는 체감 차이 꽤 나.