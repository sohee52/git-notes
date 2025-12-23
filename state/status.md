
## `git status`

### 역할

* 현재 Git 저장소의 **상태를 한눈에 보여준다.**

### 확인 가능한 정보

* 현재 브랜치
* 원격 브랜치와의 관계 (ahead / behind 여부)
* 변경된 파일 상태

  * staged
  * modified
  * untracked

### 상태 분류 예시

* `Changes to be committed` → 스테이징된 파일
* `Changes not staged for commit` → 수정됐지만 add 안 된 파일
* `Untracked files` → Git이 아직 관리하지 않는 파일

### 영향 받는 영역

* ❌ 작업 디렉토리 변경 없음
* ❌ 스테이징 영역 변경 없음
* ❌ 커밋 변경 없음

### 사용 상황

* 커밋 전에 상태 점검
* 작업 중 실수 방지
* 현재 어떤 파일이 어디까지 처리됐는지 확인할 때

### 요약

> **현재 작업 상태를 확인만 하는 명령**