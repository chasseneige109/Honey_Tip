
## 1️⃣ What is BLAS?
**BLAS (Basic Linear Algebra Subprograms)**  
: 1960년대부터 정의된 선형대수 기본 연산 표준 인터페이스.  
모든 수치계산 라이브러리(Numpy, PyTorch, MATLAB 등)의 기반.

---

## 2️⃣ BLAS Levels

| Level | 연산 유형 | 예시 | 복잡도 | 특징 |
|-------|------------|------|---------|------|
| **BLAS 1** | 벡터–벡터 | inner product, axpy | `O(n)` | 메모리 접근 의존도 높음 |
| **BLAS 2** | 행렬–벡터 | y = A·x | `O(n²)` | 중간 효율 |
| **BLAS 3** | 행렬–행렬 | C = A·B | `O(n³)` | 연산 밀도 높음, GPU/TPU 최적화 |

> 💡 BLAS level이 높을수록 **캐시 효율·병렬화 성능**이 좋아짐.

---

## 3️⃣ Sparse Structure

**희소 행렬(sparse matrix)**  
→ 대부분의 원소가 0인 행렬.  
실제 연산은 **non-zero 항만 계산**.

- **Inner product**: `O(min(nnz(x), nnz(y)))`
- **Matrix-vector multiply**: `O(nnz(A))`

> 예: 1억 차원 벡터라도 비제로 항이 10만 개면 → 약 10⁵ flops.

---

## 4️⃣ Low-rank Structure

**저랭크 행렬 (Low-rank matrix)**  
\[
A = U V^T, \quad U ∈ ℝ^{n×r}, V ∈ ℝ^{n×r}, \, r ≪ n
\]

- 올바른 계산:  
  `A·x = U·(Vᵀ·x)` → `O(n·r)`
- 잘못된 계산:  
  `A = U·Vᵀ`를 먼저 생성 → `O(n²)` 메모리 폭발 💥

> ✅ low-rank 구조를 활용하면 저장공간·연산량 모두 절약 가능.

---

## 5️⃣ 연산별 시간 복잡도 비교

| 연산 | 복잡도 | 예시 |
|------|----------|------|
| Inner product | `O(n)` | BLAS 1 |
| Matrix–vector | `O(n²)` | BLAS 2 |
| Matrix–matrix | `O(n³)` | BLAS 3 |
| Sparse multiply | `O(nnz(A))` | 희소행렬 |
| Low-rank multiply | `O(n·r)` | r ≪ n |

---

## 6️⃣ Key Takeaways

- **BLAS Level 3**: GPU/TPU에서 가장 효율적  
- **Sparse**: 비제로 항만 계산 → 속도 수천 배 향상  
- **Low-rank**: 큰 행렬을 작은 구성요소로 표현  
- **실무 최적화 핵심**: flops 개수보다 **데이터 구조와 메모리 패턴**

---

📘 *Ref: S. Boyd — Numerical Linear Algebra Lecture (Matrix Structure & BLAS Levels)*
