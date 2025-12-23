# Git 서브모듈 이름(디렉터리) 변경 방법

## ✔️ 1. `.gitmodules` 파일 수정

`.gitmodules` 파일 안에는 보통 이런 구조가 있음:

```
[submodule "db-kjw-basic"]
    path = db-kjw-basic
    url = https://github.com/xxx/db-kjw-basic.git

```

여기서 `"db-kjw-basic"` 이 **서브모듈 명**,

`path = db-kjw-basic` 가 **디렉터리명**.

예를 들어 `db-kjw-basic` → `db-kjw-internals` 로 바꾸고 싶다면:

### 수정 전

```
[submodule "db-kjw-basic"]
    path = db-kjw-basic
    url = https://github.com/xxx/db-kjw-basic.git

```

### 수정 후

```
[submodule "db-kjw-internals"]
    path = db-kjw-internals
    url = https://github.com/xxx/db-kjw-basic.git

```

> ✔️ submodule 이름과 path 둘 다 원하는 이름으로 수정해야 함.
> 

---

## ✔️ 2. 서브모듈 디렉터리 이름 변경

터미널에서 실제 폴더 이름 변경:

```bash
git mv db-kjw-basic db-kjw-internals

```

또는 OS에서 폴더 이름 변경 후:

```bash
git add .

```

---

## ✔️ 3. Git에 새 path 반영

수정된 `.gitmodules` 내용을 Git에 반영:

```bash
git add .gitmodules
git add db-kjw-internals

```

---

## ✔️ 4. `.git/config`의 서브모듈 path 업데이트

`.git/config`에도 같은 항목이 하나 더 있어. 자동으로 고쳐지지 않으면 수동으로 고침.

`.git/config` 열어서:

```
[submodule "db-kjw-basic"]
    url = https://github.com/xxx/db-kjw-basic.git

```

→ 이름 바꿔서:

```
[submodule "db-kjw-internals"]
    url = https://github.com/xxx/db-kjw-basic.git

```

(여기는 path는 필요 없고 url만 있음)

---

## ✔️ 5. Git이 새로운 서브모듈 위치를 인식하도록 업데이트

```bash
git submodule sync
git submodule update --init --recursive

```

---

## ✔️ 6. 커밋

이제 마무리 커밋:

```bash
git commit -m "chore: rename submodule db-kjw-basic -> db-kjw-internals"

```

---

## 🔥 정리하면 딱 3단계

1. `.gitmodules` 수정
2. 실제 폴더 이름 변경
3. `git submodule sync && update`
