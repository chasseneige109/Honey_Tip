간선의 가중치가 존재하며, 한 노드에서 시작하여, 모든 노드를 탐색하는 최소 비용

### 기본 구현 방법
- 간선 가중치를 오름차순으로 정렬 후 작은 순으로 선택.
- 이때 [[Union Find]]를 활용하여 사이클이 형성될 시 미포함.