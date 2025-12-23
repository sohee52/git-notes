# Git reset --soft HEAD~1 되돌리기

## 상황 설명

```bash
git reset --soft HEAD~1
```

- 마지막 커밋을 **취소**
- 변경 내용은 **staging 영역(index)에 그대로 유지**
- 커밋만 사라진 상태

👉 이 상태에서 **reset 하기 전 상태로 완전히 되돌리고 싶을 때** 사용 방법 정리

---

## ✅reflog를 이용한 정확한 복구

### 1️⃣ reflog 확인

```bash
git reflog
```

예시 출력:

```
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
e4f5g6h HEAD@{1}: commit: 커밋 메시지
```

- `HEAD@{0}` : reset 직후 상태
- `HEAD@{1}` : **reset 실행 직전 상태**

---

### 2️⃣ reset 이전 상태로 되돌리기

```bash
git reset --hard HEAD@{1}
```

결과:

- 커밋 상태 → 복구됨
- staging 영역 → 복구됨
- working directory → 복구됨
    
    ➡️ **reset 하기 전과 완전히 동일한 상태**