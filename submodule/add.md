## 0️⃣ 전제 조건

- 메인 repository가 이미 존재
- 서브모듈로 추가할 repository가 이미 존재
- 두 repo 모두 접근 권한 있음
- 메인 repo의 브랜치 예시: `main`
- 서브모듈 브랜치 예시: `main`

---

## 1️⃣ 메인 repo로 이동

```bash
cd <메인-repo-경로>

```

현재 위치 확인:

```bash
git status

```

---

## 2️⃣ 서브모듈 추가

```bash
git submodule add -b main https://github.com/sohee52/db-pjs-design.git db-pjs-design

```

### 옵션 설명

- `b main` : 서브모듈에서 사용할 기본 브랜치
- 마지막 인자 `db-pjs-design` : 메인 repo 내에 생성될 디렉터리 이름

---

## 3️⃣ 서브모듈 추가 결과 확인

```bash
git status

```

변경 사항:

- `.gitmodules` 파일 생성
- `db-pjs-design/` 디렉터리 추가 (서브모듈 포인터)

---

## 4️⃣ `.gitmodules` 파일 확인 (중요)

```bash
cat .gitmodules

```

정상 예시:

```
[submodule "db-pjs-design"]
    path = db-pjs-design
    url = https://github.com/sohee52/db-pjs-design.git
    branch = main

```

> branch = main이 있어야 git submodule update --remote 사용 가능
> 

---

## 5️⃣ 서브모듈 초기화 및 실제 코드 다운로드

```bash
git submodule update --init --recursive

```

> 이미 clone되어 있어도 한 번 실행하는 것이 안전
> 

---

## 6️⃣ 메인 repo에 변경 사항 커밋

⚠️ **이 단계가 없으면 서브모듈 추가가 완료되지 않음**

```bash
git add .gitmodules db-pjs-design
git commit -m "chore: add db-pjs-design submodule"

```

---

## 7️⃣ 메인 repo 원격 저장소에 push

```bash
git push origin main

```

---

## 8️⃣ 다른 사람이 메인 repo를 clone할 때

### 8️⃣-1️⃣ 처음부터 받을 때 (권장)

```bash
git clone --recurse-submodules <메인-repo-URL>

```

### 8️⃣-2️⃣ 이미 clone한 상태라면

```bash
git submodule update --init --recursive

```

---

## 9️⃣ 서브모듈 최신 커밋으로 업데이트하기

서브모듈의 `main` 브랜치 기준으로 최신화:

```bash
git submodule update --remote db-pjs-design

```

이후 **메인 repo에서 커밋 필요**:

```bash
git add db-pjs-design
git commit -m "chore: update db-pjs-design submodule"
git push origin main

```

---

## 1️⃣0️⃣ 서브모듈에서 작업할 때 기본 흐름

```bash
cd db-pjs-design
git checkout main
git pull
# 작업
git add .
git commit -m "feat: ..."
git push

```

다시 메인 repo로 돌아와서:

```bash
cd ..
git add db-pjs-design
git commit -m "chore: bump db-pjs-design submodule"
git push

```