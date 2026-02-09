## 커밋 내용 수정하는 방법

### push하기 전

```bash
git commit --amend -m "새로운 커밋 메시지"
git push
```

### push한 후

```bash
git commit --amend
git push -f origin 브랜치명
```
