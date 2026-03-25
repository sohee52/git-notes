# Git 사용자 정보 설정하기

## 오류 상황
<p align="center"><img src="images/img-2026-03-25-09-58-29.png" width="100%"/></p>

Git에 사용자 정보(`user.name`, `user.email`)가 설정 안 돼 있어서 발생하는 오류이다.

## ✅ 해결 방법

터미널(또는 VSCode 터미널)에서 아래 실행:

### 1. 전역(global) 설정 (추천)

```bash
git config --global user.name "이름"
git config --global user.email "이메일"
```

예시:

```bash
git config --global user.name "홍길동"
git config --global user.email "test@example.com"
```

---

### 2. 잘 들어갔는지 확인

```bash
git config --global --list
```

→ `user.name`, `user.email` 나오면 정상

---

## ❗ 참고 (중요)

* 이 정보는 **commit 작성자 정보**로 들어감
* GitHub 쓸 거면 **GitHub 이메일이랑 동일하게 맞추는 게 좋음**

---

## 📌 특정 프로젝트에서만 설정하고 싶으면

(global 말고 해당 repo만 적용)

```bash
git config user.name "이름"
git config user.email "이메일"
```