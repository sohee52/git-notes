# 서브 모듈 삭제하는 방법

```bash
git submodule deinit -f git-yalco-submodule
git rm -f git-yalco-submodule
rm -rf .git/modules/git-yalco-submodule
git commit -m "Remove submodule git-yalco-submodule"
```