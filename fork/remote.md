### 1️⃣ 왜 `remote`가 필요한가

* **fork한 repo**에는 기본적으로

  * `origin` → **내 fork 저장소**
* **원래(repo 주인) 저장소**는 기본 remote로 등록돼 있지 않음
  → 그래서 **PR 대상 저장소(upstream)** 를 `remote`로 추가해야 함

---

### 2️⃣ 핵심 명령어

#### 🔹 원본 저장소를 upstream으로 추가

```bash
git remote add upstream https://github.com/원래주인/원래repo.git
```

#### 🔹 등록 확인

```bash
git remote -v
```

결과 예시:

```text
origin    https://github.com/내계정/repo.git (fetch)
upstream  https://github.com/원래주인/repo.git (fetch)
```

---

### 3️⃣ PR 올리는 실제 흐름

```bash
# 1. upstream 최신 내용 가져오기
git fetch upstream

# 2. upstream main 기준으로 브랜치 생성
git checkout -b feature/foo upstream/main

# 3. 작업 후
git push origin feature/foo
```

→ **GitHub에서**

* base: `원래주인/repo (main)`
* compare: `내계정/repo (feature/foo)`
* PR 생성

---

### 요약

> `origin`은 내 fork, `upstream`은 원본 repo이며
> PR을 제대로 관리하려면 원본 repo를 `upstream`으로 등록해야 한다.
