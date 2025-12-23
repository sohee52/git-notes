- 서브모듈이 새로 생겼을 때 pull하는 방법
    
    1️⃣ **상위 레포에서 먼저 pull**
    
    ```bash
    git pull
    ```
    
    이 단계에서 일어나는 일:
    
    - `.gitmodules`에 `algorithm-cpp-soma` 항목이 추가됨
    - 서브모듈 “존재 정보”만 내려받음
        
        👉 **폴더는 비어 있거나, 아예 안 보일 수 있음 (정상)**
        
    
    ---
    
    2️⃣ **서브모듈 초기화 + 다운로드**
    
    ```bash
    git submodule update --init
    
    또는
    
    git submodule update --init --recursive
    ```
    
    이 명령의 의미:
    
    - `--recursive` : 모든 서브모듈 한 번에 맞추기
    - `-init` : 새로 추가된 서브모듈 등록
    - `update` : `.gitmodules`에 적힌 커밋 기준으로 checkout
    
    ➡️ 이걸 실행하면
    
    `algorithm-cpp-soma/` 디렉토리가 생기고 실제 코드가 내려와야 함
    
    ---
    
    3️⃣ **확인 방법**
    
    ```bash
    git submodule status
    ```
    
    또는
    
    ```bash
    ls
    ```
    
    여기서 `algorithm-cpp-soma`가 다른 서브모듈들이랑 같이 보이면 정상.
    
    ---
    
    ⚠️ **절대 하면 안 되는 것**
    
    - ❌ `git pull`을 서브모듈 폴더 안에서 먼저 하는 것
    - ❌ 서브모듈 폴더를 직접 `git clone` 하는 것
        
        (서브모듈은 **상위 repo가 관리**함)
        
    
    ---
    
    **한 줄 요약 (가장 중요)**
    
    ```bash
    git pull
    git submodule update --init --recursive
    ```