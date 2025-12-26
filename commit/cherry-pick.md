- 다른 브랜치에서 만든 “특정 커밋만” 가져오고 싶으면 (cherry-pick)
    
    ```bash
    git cherry-pick <해시값>
    
    혹은
    
    git cherry-pick <시작해시>^..<끝해시>
    git cherry-pick ea2f9f7^..01a8512
    ```