# Git & Github

## Git이란?

### Git : 버전 관리 프로그램으로서, 동시 협업을 가능하게 해줌.

1. 지난 과정 확인 가능
2. 이전 버전으로 돌아갈 수 있음.
3. 다른 컴퓨터, 즉 원격 저장소 github에 작업물을 보내 백업 가능

- .**gitignore 파일** : working directory 내에 존재하는 파일들 중에서 마치 존재하지 않는 것처럼 git이 인식해야 할 파일들의 목록이 적힌 파일
    - .gitignore 파일에 버전 관리할 필요가 없는 것들을 추가하면서 진행하면 더 깔끔하게 버전 관리 가능

### 운영 체제(Operation System, OS) : 입력과 출력을 연결

- 컴퓨터는 입력과 출력의 기능만 하는데, 이를 연결해주는 역할을 해줌.
- 여러 제조사의 하드웨어를 고려하여 애플리케이션에 신호를 연결해줌.
- 운영 체제의 도움으로, 여러 애플리케이션이 작동 가능

<aside>
💡 **Git Bash** : Windows에서도 유닉스 커맨드를 사용할 수 있도록 하는 프로그램

</aside>

### 레포지토리와 커밋

- **레포지토리(repository)** : 커밋이 저장되는 장소
    - 프로젝트 디렉토리에 버전 별로 프로젝트 모습, 변경 사항에 대한 설명이 있음.
    - .git 디렉토리가 레포지토리이며, 숨겨져 있음.
        
        ```bash
        # 비어있는 레포지토리(.git 레포지토리) 생성
        $ git init
        ```
        
        - 터미널에서 숨긴 파일을 확인하는 방법
            
            1) Mac : $ ls -al
            
            2) Windows cmd : $ dir /a
            
            3) Powershell : $ Get-ChildItem-Force
            
        - $ cd .. : 상위 폴더로 나가는 커맨드
        - $ touch [파일 이름] : 현재 위치에서 파일 생성

- **커밋(commit)** : 프로젝트 디렉토리의 특정 모습을 하나의 버전으로 남기는 행위 및 결과물
    - 프로젝트 디렉토리의 버전을 하나로 남김.
        
        ex) 커밋1 — 커밋2 — 커밋3 — 커밋4 — …
        

- **커밋 커맨드**
    - 커밋하기 전에 git에게 커밋하는 사람 알려주기
        
        ```bash
        $ git config user.name "Yeobi"
        $ git config user.email "kimhyjjang@gmail.com"
        ```
        
    
    - 커밋할 파일을 미리 지정해주기
        
        ```bash
        # staging area에 파일 추가
        $ git add [파일 이름]
        
        # 현재 프로젝트 디렉토리 내에서 변경사항이 생긴 모든 파일을 staging area에 추가
        $ git add .
        ```
        
    
    - staging area에서 파일 제거하기
        
        ```bash
        $ git reset [파일 이름]
        ```
        
        # nothing to commit, working tree clean : 이전 커밋 이후로 변경사항 없음.
        
    
    - git이 인식하고 있는 프로젝트 디렉토리의 현재 상태 보여주기
        
        ```bash
        $ git status
        ```
        
    
    - git 커맨드의 의미와 사용법을 자세히 알아보기
        
        ```bash
        $ git help [커맨드]
        # 또는
        $ man git- [커맨드]
        ```
        

### Git으로 관리되는 파일이 가지는 일종의 ‘상태(status)’

1. **Untracked 상태** : 한 번도 git add 해주지 않아 파일이 git에 의해 변동사항이 전혀 추적되고 있지 않은 상태
2. **Tracked 상태** : 파일이 git에 의해 그 변동사항이 추적되고 있는 상태
    
    1) **Staged 상태** : 파일의 내용이 수정된 후, staging area에 올라와 있는 상태
    
    - 새로 생성한 파일에 내용을 쓰고 git add 해준 상태
    - 한 번이라도 커밋에 포함됐었던 내용이 최신 커밋의 모습과 비교했을 때 전혀 바뀐 게 없는 상태
    
    2) **Unmodified 상태** : 현재 파일의 내용이 최신 커밋의 모습과 비교했을 때 전혀 바뀐 게 없는 상
    
    - 커밋을 하고 난 직후, working directory 안의 모든 파일들이 이 상태가 됨.
    
    3) **Modified 상태** : 최신 커밋 모습과 비교했을 때 조금이라도 바뀐 내용이 있는 상태
    

---

## Github란?

- 깃허브의 레포지토리 : **리모트 레포지토리**  vs  내 컴퓨터의 레포지토리 : **로컬 레포지토리**
- 목적 : 1) 안전성  2) 협업 가능
- **git push** 커맨드를 통해 로컬 레포지토리의 내용 → 리모트 레포지토리에 반영
- **git push** 는 리모트 레포지토리의 주인인 본인만 가능, 타인도 할 수 있게 해주려면 collaborator로 지정
- 로컬 레포지토리를 수정하는 동안 깃허브에 변화가 생기면 git push 불가능
    
    → git pull 먼저 한 다음, merge 완료하고, git push 진행
    
- 파일 이름이 README일 경우, 내용을 바로 보여줌.
    - README.md
        1. 어떤 프로젝트인지 설명하거나
        2. 프로그램의 주요 사용법을 알려주거나
        3. 프로그램을 실행시키려면 어떤 사전 작업이 필요한지 알려주는 내용을 적음.
        - .md 확장자 : markdown의 준말로, 특정 규칙에 맞게 간단한 텍스트만으로 어떤 표시를 해두면 자동으로 HTML 태그로 전환되도록 약속한 문법
            
            → 단지 텍스트만으로도 내용의 디자인을 예쁘게 만들 수 있음.
            
        - 일반적으로 프로젝트의 관한 설명을 담고 있기 때문에 내용을 바로 보여줌.
        

- **협업하기**
    - **git fetch** 커맨드 사용
        - Github에서 가져온 브랜치의 내용을 merge하기 전에 점검해야 할 필요가 있을 때
        - Github에 있는 브랜치의 내용과 내가 작성한 코드를 비교하며 검토하고자 할 때
        
        |                          git pull |                         git fetch |
        | --- | --- |
        |   로컬 레포지토리에 merge까지 진행 |     로컬 레포지토리에 merge는 진행 x |
    - 책임 소재 묻기
        
        ```python
        # 해당 파일의 특정 코드를 누가 작성했는지 찾아내기
        $ git blame [파일 이름]
        
        # 커밋 author 찾아내기
        $ git show [커밋 id]
        ```
        

- **관련 코드**
    
    ```bash
    # 로컬 레포지토리의 내용을 처음으로 리모트 레포지토리에 올릴 때
    $ git push -u origin main
    
    # 로컬 레포지토리의 내용을 리모트 레포지토리에 보내기
    $ git push
    
    # 리모트 레포지토리의 내용을 로컬 레포지토리로 가져오기
    $ git pull
    
    # Github에 있는 프로젝트를 내 컴퓨터로 가져오기
    $ git clone [프로젝트의 Github 상 주소]
    
    # Github에 있는 브랜치의 내용을 일단 가져와서 살펴본 후, merge하길 원할 때 사용
    $ git fetch
    ```
    

---

## Commit 다루기

### **커밋 가이드라인**

- **커밋 해시** : 커밋 관리를 위해 커밋 각각에 대해 id를 부여함.
- **커밋 메시지**
    1. 커밋 메시지 제목과 상세 설명 사이에 한 줄 비워두기
    2. 커밋 메시지 제목 뒤에 온점 붙이지 않기
    3. 커밋 메시지 제목의 첫 번째 알파벳은 대문자로 작성
    4. 커밋 메시지 제목은 명령조로 작성
    5. 커밋의 상세 내용에 커밋 이유, 어떤 문제가 있었는지, 적용한 해결책이 어떤 효과를 가지는지 적으면 좋음.
- 하나의 커밋에는 하나의 수정사항만 남기기
- 현재 프로젝트 디렉토리의 상태가 그 내부의 전체 코드를 실행했을 때 에러가 발생하지 않는 경우에만 커밋하기

### HEAD와 커밋

- **HEAD** : 브랜치를 통해 커밋을 간접적으로 가리키는 포인터
    - **Detached HEAD** : HEAD가 main 브랜치를 가리키는 게 아니라 직접 커밋을 가리키고 있는 상태의 HEAD
        - 과거의 특정 커밋에서 새로운 브랜치를 만들고 싶을 때 **git checkout** 커맨드를 통해 커밋을 이동함.
        - **git checkout** : HEAD가 직접적으로 가리키는 것을 바꿀 수 있고, 커맨드 뒤에 커밋 id나 브랜치 이름을 줘서 직접 커밋 또는 브랜치를 가리키도록 할 수 있음.
    - Working Directory는 HEAD가 가리키는 커밋에 따라 구성
- **git reset** : HEAD가 과거의 커밋을 가리키게 할 수 있고, working directory의 내용도 과거 커밋의 모습으로 돌아가게 할 수 있음.
    
    → 과거의 커밋으로 아예 돌아가고 싶을 때 사용
    
    - 과거의 커밋으로 git reset을 하더라도 그 이후의 커밋들이 삭제되는 게 아니라 계속 남아있음.
    - 과거뿐만 아니라 현재 HEAD가 가리키는 커밋 이후의 커밋으로도 돌아갈 수 있음.
    
    ```bash
    # HEAD가 해당 커밋을 가리키게 해 과거로 돌아가기
    $ git reset —hard [커밋 id]
    
    # HEAD가 가리키는 커밋의 바로 이전 커밋으로 돌아가기
    $ git reset —hard HEAD^
    
    # HEAD가 가리키는 커밋보다 n단계 전의 커밋으로 돌아가기
    $ git reset —hard HEAD~(n)
    ```
    
    - **—soft** : HEAD가 과거의 특정 커밋을 가리키도록 함.
    - **—mixed** : staging area를 과거 특정 커밋의 내용과 똑같게 만듦.
    - **—hard** : working directory를 과거 특정 커밋의 내용과 똑같게 만듦.
    
    <aside>
    💡 **커밋 이후엔 working directory에서 했던 내용들이 날아가므로 조심하자!**
    
    **→ $ git pull 커맨드 사용하여 github에서 다시 가져오기**
    
    </aside>
    
- **git revert** : 과거의 커밋으로 돌아가고, 기록을 남김
    
    ```python
    # 과거 커밋으로 돌아가기
    $ git revert [커밋 id]
    
    # id1 다음 커밋부터 id2까지 커밋을 id1 커밋으로 되돌리기
    $ git revert [커밋 id1]..[커밋 id2]
    ```
    
- **git reflog** : reference log의 약자로, HEAD가 이때까지 가리켜왔던 커밋들을 보여줌.
    - HEAD가 가리켰던 커밋들의 id를 확인할 수 있음.
    - $ git reflog한 뒤, $ git reset —hard [커밋 id] 커맨드 활용
- **git log** : 커밋 히스토리 확인
    
    ```python
    # 한 줄로 모든 브랜치의 커밋을 보여주기
    $ git log --pretty=oneline --all
    
    # 모든 브랜치의 커밋을 그림과 함께 입체적으로 보여주기
    $ git log --pretty=oneline --all --graph
    ```
    

---

## Branch에 대해..

### Branch : 하나의 코드 관리 흐름을 뜻하며, 어떤 커밋을 가리키는 포인터

 **# On branch main** : main 브랜치 위에 있다는 의미

- **Remote Repository의 브랜치**
    - **$ git remote add origin [깃허브 주소]** 에서
        - **remote** : 리모트 레포지토리에 관한 작업을 할 때 쓰는 커맨드
        - **add** : 새로운 리모트 레포지토리 등록
        - **origin [깃허브 주소]** : 깃허브 주소를 origin 이라는 이름으로 등록
            
            → origin 대신 다른 단어를 입력해도 상관 없지만, origin 사용이 관례!
            
    - **$ git push -u origin main** : 현재 로컬 레포지토리에 있는 main 브랜치의 내용을 origin이라는 리모트 레포지토리로 보낸다는 의미임.
        - **-u (—set-upstream)** : 로컬 레포지토리의 main 브랜치가 origin의 main 브랜치를 tracking 한다는 의미임.
            - **tracking** : 로컬 레포지토리의 한 브랜치가 리모트 레포지토리의 한 브랜치와 연결되어 그것을 계속 바라보는 상태가 되는 것
        - **main** : 로컬 레포지토리의 main 브랜치
        - **origin/main** : 리모트 레포지토리의 main 브랜치
    - 새로 만든 브랜치에서 github로 보내려 하는데, 오류 발생 예시
        
        # fatal: The current branch premium has no upstream branch.
        
        # To push the current branch and set the remote as upstream, use
        
        #        git push --set-upstream origin premium
        
        → **$ git push —set-upstream origin premium** 커맨드 입력하면 github와 브랜치를 연결하여 해결 가능!
        
    - 리모트 레포지토리의 브랜치에 문제 발생 시, 해결 방법
        - 잘못된 코드를 추가한 개발자에게 함수를 지우고 다시 리모트 레포지토리에 올려달라고 하기
        - 잘못된 부분을 알아서 해결하고 다시 git push 하기
- Branch 관련 **git 커맨드**
    
    ```bash
    # 브랜치 생성
    $ git branch [브랜치 이름]
    
    # 해당 브랜치로 이동
    $ git checkout [브랜치 이름]
    
    # 브랜치 조회
    $ git branch
    
    # 해당 브랜치 삭제
    $ git branch -d [브랜치 이름]
    
    # 브랜치를 생성한 뒤, 그 브랜치로 이동
    $ git checkout -b [브랜치 이름]
    ```
    

### Merge와 Conflict

- **merge** : 브랜치를 병합하는 것으로, HEAD가 가리키던 커밋에 다른 브랜치가 가리키던 커밋을 합쳐서 새로운 커밋을 만드는 작업
- **merge 커밋** : merge를 통해서 생겨난 커밋
- **Fast-forward merge** : 새로운 커밋이 생기는 것이 아니라 단지 브랜치가 이동하게 되는 merge
- **3-way merge** : 3가지 커밋을 고려하여 merge를 함.
    - base 때의 내용과 비교했을 때 달라진 부분이 있는 것이 우선시됨.
    - 두 브랜치에서 둘 다 변화가 일어났을 때에는 Conflict를 발생시켜서 사용자가 스스로 선택하게끔 함.
- merge 관련 **git 커맨드**
    
    ```bash
    # 현재 위치 브랜치에 해당 브랜치를 merge하기
    $ git merge [브랜치 이름]
    
    # merge 취소하기
    $ git merge --abort
    ```
    
- Merge 도중 conflict 발생 가능
    
    # CONFLICT (content): Merge conflict in [calculator.py](http://calculator.py/) → merge 도중 충돌 발생
    
    - **Conflict 해결 방법**
        - 하나의 파일에서 conflict 발생 시
            1. 충돌이 발생한 파일 열기
            2. merge의 결과가 되었으면 하는 모습대로 코드 수정하기
        - 여러 개의 파일에서 conflict 발생 시
            
            1) 각각의 파일의 conflict를 하나씩 해결하고 $ git add [파일 이름] 커맨드 입력
            
            2) 모든 파일들의 conflict를 다 해결하고 한 번에 $ git add . 커맨드 입력
            
    - **Merge 취소 방법**
        - $ git merge —abort 커맨드 입력하여 merge 취소
        - merge 취소보다는 충돌 해결한 뒤 커밋하는 것이 정석임!
        
- **rebase** : 두 커밋을 하나의 커밋으로 깔끔하게 이어붙임.
    - rebase와 merge의 차이점
        - rebase는 새로운 커밋을 만들지 않음.
        - rebase로 만들어진 커밋 히스토리가 merge로 만들어진 커밋 히스토리보다 더 깔끔함.
        
        |                    rebase |                    merge |
        | --- | --- |
        | 커밋 히스토리를 깔끔하게 유지해야 할 때 | 두 브랜치를 합쳤다는 정보가 히스토리에 남아야 할 때 |

### Git stash

- working directory에서 작업하던 내용을 git이 스택에 따로 보관해줌.
- 최근 커밋 이후로 작업했던 내용은 모두 스택에 옮겨지고, working directory 내부는 다시 최근 커밋 상태로 초기화됨.

- 한 브랜치에서 하던 작업을 아직 커밋하지 않았는데, 다른 브랜치로 가야 하는 상황에서 작업 중이던 내용을 잠깐 저장하고 싶을 때 사용
- 잘못된 브랜치에서 작업했을 때에도 사용
    1. git stash로 stack에 작업 내용 저장
    2. 올바른 브랜치로 가서 다시 git stash apply 커맨드 입력

<aside>
💡 스택에 작업 내용이 너무 많이 쌓이면 가독성이 좋지 않으므로 이미 적용한 작업 내용은 지워주자!

</aside>

- 관련 코드
    
    ```bash
    # git 스택에 잘 저장되었는지 확인하기
    $ git stash list
    
    # git 스택에 저장해둔 내용 불러오기
    $ git stash apply [작업 내용 id]
    
    # 해당 작업 내용 삭제하기
    $ git stash drop [작업 내용 id]
    
    # 특정 작업 내용을 적용함과 동시에 스택에서 제거하기
    $ git stash pop [작업 내용 id]
    
    # 자신이 원하는 작업이 들어있는 커밋들만 가져와서 현재 브랜치에 추가하기
    $ git cherry-pick [커밋 id]
    
    # 불필요한 커밋들 없애주기
    $ git reset (--soft / --mixed) [커밋 id]
    ```
    

---

## Git 커맨드

$ git push -u origin main : 처음으로 로컬 레포지토리의 내용 → 리모트 레포지토리

$ git push : 로컬 레포지토리 내용 → 리모트 레포지토리

$ git pull : 리모트 레포지토리 내용 → 로컬 레포지토리

$ git clone (github 주소) : 깃허브 프로젝트의 레포지토리를 그대로 복제

$ git log : 커밋 히스토리 보기

$ git log —pretty=oneline : 커밋 히스토리를 한 줄로 깔끔하게 보기

$ git config alias.(수정할 커맨드) ‘(원래 있던 커맨드)’ : 커맨드 전체에 별명을 붙여 그 별명으로 사용 가능 (aliasing)

$ git history : git —pretty=oneline 커맨드 별명으로, 한 줄의 커밋 히스토리 보기

$ git show (커밋 id) : 해당 커밋 내용 보여주기

- --- : 해당 커밋 이전의 모습
- +++ : 해당 커밋에서의 모습

$ git diff (이전 커밋 id) (이후 커밋 id) : 두 커밋 사이의 변화 알아보기

$ git commit —amend : 최신 커밋을 수정해서 다시 새로운 커밋으로 만들기

$ git reset : HEAD가 과거의 커밋을 가리키게 할 수 있고, working directory의 내용도 과거 커밋의 모습으로 돌아가게 함. 

- 과거 커밋으로 아예 돌아가고 싶을 때 사용

$ git reset —hard (커밋 id) : HEAD가 해당 커밋을 가리키게 해 과거로 돌아감.

$ git reset --hard HEAD^ : HEAD가 가리키고 있는 커밋의 바로 이전 커밋으로 돌아감.

$ git reset --hard HEAD~(n) : HEAD가 가리키는 커밋보다 n단계 전에 있는 커밋으로 돌아감.

$ git tag : 프로젝트 디렉토리에 있는 모든 태그 조회

$ git tag (태그 이름) (커밋 id) : 커밋에 태그 달기

$ git show (태그 이름) : 태그와 연결된 커밋 살펴보기 

$ cat (파일 이름) : 파일 내용 터미널에 출력