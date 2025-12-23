## 커밋 내용 수정하는 방법

### push하기 전

```bash
git commit --amend -m "새로운 커밋 메시지"
git push
```

### push한 후

```bash
git commit --amend -m "새로운 커밋 메시지"
git push --force-with-lease
```

#### `--force-with-lease`
- "내가 마지막으로 봤던 원격 상태 그대로일 때만" 강제 push
- 강제 푸시 시 다른 사람의 작업을 덮어쓰지 않도록 보호해줍니다.