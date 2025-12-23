# 서브 모듈 만드는 법

> 여러 독립 알고리즘 저장소를
> 
> 
> 하나의 메인 저장소에서 함께 관리하고 싶을 때 사용하는 방식
> 
> (메인 Public + 서브 Private 가능)
> 

---

## 1️⃣ 메인 Repository 생성

### (1) GitHub에서 새 Repo 생성

---

### (2) 로컬에 Clone

```bash
cd C:/Users/PC/Desktop
git clone https://github.com/sohee52/algorithm.git
cd algorithm
```

---

## 2️⃣ 서브 Repo 준비

서브 Repo는 **이미 존재한다고 가정**

예)

```
https://github.com/sohee52/algorithm-cpp-samsung (Private)
https://github.com/sohee52/algorithm-cpp-boj
...
```

서브 Repo는 **각각 독립 개발용**으로 유지됨

---

## 3️⃣ 메인 Repo에 서브모듈 추가

메인 repo 폴더(algorithm) 안에서 실행

```bash
git submodule add -b main https://github.com/sohee52/git-yalco
```

다른 서브 Repo도 같은 방식

```bash
git submodule add -b main https://github.com/sohee52/git-notes
...
```

---

## 4️⃣ 처음 Submodule 추가 후 Commit & Push

```bash
git add .gitmodules
git commit -m "Add submodules"
git push origin main
```

> 이 시점에 GitHub 메인 repo에
> 
> 
> **서브 폴더 + .gitmodules 파일**이 생김
> 

---

## 5️⃣ Submodule에서 개발하는 방법

직접 서브모듈 폴더로 들어가서 작업

```bash
cd algorithm-cpp-samsung
git add .
git commit -m "solve: new problem"
git push origin main
```

---

## 6️⃣ 메인 Repo에 반영(pointer commit)

서브모듈에서 push 후, 메인 repo에 돌아와서:

```bash
cd ..
git add algorithm-cpp-samsung
git commit -m "Update submodule: samsung"
git push

```

> 메인 repo가 “서브모듈 최신 커밋을 가리키도록” 업데이트됨
> 

---

## 7️⃣ 처음 Clone 한 PC에서 Submodule 포함 가져오기

```bash
git clone https://github.com/sohee52/algorithm.git
cd algorithm
git submodule update --init --recursive
```

---

## 8️⃣ Submodule 최신 반영 가져오기

메인 repo에서 실행:

```bash
git submodule update --remote --merge
```

---

# ⭐ 핵심 요약

```
코드는 서브 repo에서 개발 → push
메인 repo는 pointer commit → push
clone 시 submodule update 필요
```

---

# ✨ 선택 자동화 옵션 (원하면 추가)

| 기능 | 지원 여부 | 설명 |
| --- | --- | --- |
| 한 줄로 pointer commit | ✔ | alias 또는 스크립트 제공 |
| 풀 자동화 (서브에서 push → 메인 자동 반영) | ✔ | GitHub Actions + PAT 설정 필요 |
| VS Code workspace 자동 구성 | ✔ | 편한 관리 가능 |

---