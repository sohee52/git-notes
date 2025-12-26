# 🔁 Git reflog 정리

## 1️⃣ reflog가 뭔가?

**`reflog` = HEAD(또는 브랜치)가 “어디를 가리켰는지”에 대한 기록**

* `commit`, `checkout`, `reset`, `rebase`, `merge` 등으로
  **HEAD가 이동한 모든 이력**을 로컬에 저장함
* 즉,
  👉 **“과거에 있었던 커밋으로 되돌아갈 수 있는 타임머신”**

---

## 2️⃣ 왜 log에는 안 보이는데 reflog에는 보일까?

### `git log`

* **브랜치가 현재 가리키는 커밋들만** 보여줌
* `reset --hard` 하면 **끊긴 커밋은 안 보임**

### `git reflog`

* **브랜치 이동 기록 자체를 저장**
* reset, force push로 **사라진 커밋도 추적 가능**

👉 그래서 **“커밋이 날아갔다” 싶을 때 마지막 희망이 reflog**

---

## 3️⃣ reflog 확인 방법

```bash
git reflog
```

출력 예시:

```
abc1234 HEAD@{0}: commit: fix typo
def5678 HEAD@{1}: reset: moving to HEAD~3
ghi9012 HEAD@{2}: commit: add feature
```

의미 해석:

* `HEAD@{0}` : 현재 위치
* `HEAD@{1}` : 바로 이전 HEAD
* `HEAD@{2}` : 그 이전 HEAD

---

## 4️⃣ reflog로 할 수 있는 대표적인 복구

### ✅ 1. reset으로 지운 커밋 복구

```bash
git reset --hard <커밋해시>
```

또는

```bash
git reset --hard HEAD@{2}
```

---

### ✅ 2. 다른 브랜치로 커밋 옮기기 (cherry-pick)

```bash
git cherry-pick <커밋해시>
```

여러 개면:

```bash
git cherry-pick A..B
```

---

### ✅ 3. “아까 상태로 돌아가기”

```bash
git reset --hard HEAD@{1}
```

→ 방금 전 상태로 정확히 복귀

---

## 5️⃣ reflog의 중요한 특징 (핵심)

### 🔹 로컬 전용

* **원격 저장소에는 reflog 없음**
* 내 컴퓨터에서만 복구 가능

### 🔹 영구 보존 아님

* 기본적으로 **약 90일** 유지
* Git GC(가비지 컬렉션) 돌면 사라질 수 있음

### 🔹 브랜치별로 존재

```bash
git reflog          # HEAD 기준
git reflog week2-1/sohee
```

---

## 6️⃣ 실무에서 reflog를 쓰는 순간들

* ❌ 잘못된 브랜치에 커밋함
* ❌ `reset --hard`로 커밋 삭제
* ❌ rebase 중 꼬임
* ❌ force push 전에 되돌리고 싶을 때
* ❌ “어제까지 있던 코드가 사라짐”

👉 **이 모든 경우의 마지막 안전망**

---

## 7️⃣ 한 줄 요약 (진짜 중요)

> **reflog는 “커밋 기록”이 아니라 “HEAD 이동 기록”이다.**
> 그래서 log에 안 보이는 커밋도 복구할 수 있다.