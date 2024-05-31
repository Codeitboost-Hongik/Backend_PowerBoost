# Git

속성: 토픽
교과목: 버전 관리 및 협업하기
기한: 2024년 5월 14일
상태: 진행 중

1. git이란? - 버전관리와 동시 협업, 다른 컴퓨터에 작업물 보내기
- 코드 버전 관리 프로그램
버전관리 장점: 지난 과정 확인 가능, 이전 버전으로 돌아갈 수 있음
협업관리
2. git의 역사
- Git은 리누스 토발즈가 리눅스의 소스 코드를 관리하기 위해 만든 버전 관리 및 협업용 프로그램입니다.
3. 깃의 목표
    
    - 빠른 속도
    - 단순한 디자인
    - 비선형적 개발 지원(수천 개의 브랜치를 병행할 수 있음, 브랜치가 뭔지는 나중 챕터에서 배웁니다.)
    - 완전 분산형 시스템
    - 리눅스와 같은 거대한 프로젝트도 속도 저하의 문제없이 관리할 수 있는 시스템
     ⇒ 깃은 버전 관리(Version Control), 협업(Cooperation)에 필요한 여러 요소들이 고려됨
    
4. github이란?
git - 버전관리와 동시 협업, 다른 컴퓨터에 작업물 보내기
다른 컴퓨터에 작업물 보내기 = 외부 컴퓨터에 백업본 만들기
외부 컴퓨터=github=원격저장소
git은 코드 버전관리 프로그램, git으로 관리하는 프로젝트를 올려두는 곳이 github
-> 코드 협업 가능
5. git설치
6. sublime 설치->vs로
7. quiz
8. repository와 commit
- 레포지토리
프로젝트 디렉토리 안에 레포지토리(.git 디렉토리, 숨겨진 디렉토리)생성
버전별 프로젝트 모습과 버전별 변경 사항에 대한 설명
커밋이 저장되는 곳
ex) 사진저장소
- 커밋
프로젝트 디렉토리의 특정모습을 하나의 버전으로 남기는 행위&결과물
ex) 사진찍기
1. repository 만들기
git init - 비어있는 레포지토리 생성
2. 첫 커밋해보기
commit에 필요한 것: 이름 이메일 커밋 메세지
git config [user.name](http://user.name/) "@@"
git config user.email "@@"
git commit -m "Create [calculator.py](http://calculator.py/) and License this is the message"
->nothing added to commit but untracted files present
-> 깃에 의해 아직 추적x
-> 버전 관리의 대상x

git add [calculator.py](http://calculator.py/)
git add License
->커밋할 파일을 미리 지정해줘야 함
->수정된 파일의 모습이 커밋에 포함될 것이라 지정하는 것
Q.
*git add License
warning: LF will be replaced by CRLF the next time Git touches it
-> $ git config --global core.autocrlf true

📍 LF란?
LF는 Line-Feed의 약자이다.
단어가 타자기에서 비롯되었듯이, 커서는 그 자리에 둔 상태에서 종이만 한 줄을 올리는 동작을 말한다.

Mac, Linux(Unix)에서 사용되는 줄바꿈 문자열(\n)이다.

📍 CRLF란?
CRLF는 Carriage Return Line-Feed의 약자이다.
여기서 Carriage Return이란 문장이 끝에 다다르면 커서는 위아래 이동 없이 가장 앞으로 이동하는 동작을 말한다.
즉, CRLF는 커서를 다음 라인의 맨 앞으로 이동하는 동작이다.

Windows에서 사용되는 줄바꿈 문자열(\r\n)이다.

false : 파일에 있는 줄바꿈 문자를 그대로 반영
true: 파일 체크인할때 crlf가 있으면 lf로 변경
체크아웃할때 lf를 crlf로 변경
intput: 파일 체크인할 때 crlf가 있으면 lf로 변경
체크아웃할 때 저장소 텍스트를 그대로 가져옴

커밋관련 주의사항

1. 처음으로 커밋을 하기 전 이름과 이메일주소 설정
2. 커밋 메세지 남기기(옵션 -m)
3. 커밋할 파일을 git add로 지정
4. 파이썬 코드 설명
5. 깃의 3가지 작업 영역
6. 퀴즈
Git은 내부적으로 크게 3가지 종류의 작업 영역을 두고 동작합니다.
각 작업 영역의 이름은
1.working directory : mathtool dir
2.staging area : git add한 파일들이 존재하는 영역, 커밋하면 여기있는 파일들만 커밋에 반영됨
3.repository : 커밋들이 저장되는 곳

참고로 working directory는 working tree라고 하기도 하고, staging area는 index라고 할 때도 있습니다. 혹시 다른 곳에서 working tree, index 이런 단어를 쓰더라도 결국 다 우리가 배운 작업 영역들이니까 당황하지 마세요!

[07.gt](http://07.gt/) add 더 자세히 알아보기
git status //깃이 인식하고 있는 프로젝트 디렉토리의 현재 상태를 보여줌
git touch [파일이름] // 파일 만들기
git add. //현재 프로젝트 디렉토리 내에서 변경사항이 생긴 모든 파일들을 staging area에 추가
git commit -m "Add title comment and Create meeting-log"

08.git이 보는 파일의 4가지 상태
일단 Git에서 파일들은 크게 다음 2가지 상태를 가집니다.

1. Untracked 상태 : Untracked는 '추적되지 않고 있는'이라는 뜻입니다. 이 상태는 파일이 Git에 의해서 그 변동사항이 전혀 추적되고 있지 않는 상태를 뜻합니다. 예를 들어, 파일을 새로 생성하고 그 파일을 한 번도 git add 해주지 않았다면 이 상태입니다.
2. Tracked 상태
2-1. Staged 상태: 파일의 내용이 수정되고나서, staging area에 올라와있는 상태를 Staged(스테이징된, stage area에 올려진) 상태라고 합니다. 새로 생성한 파일에 내용을 쓰고 git add를 해주거나 한 번이라도 커밋에 포함됐었던 파일이라도 내용을 수정하고 git add를 해주면 이 상태입니다.
2-2. Unmodified 상태: 현재gi 파일의 내용이 최신 커밋의 모습과 비교했을 때 전혀 바뀐 게 없는 상태면 그 파일은 Unmodified(수정되지 않은, 변한 게 없는) 상태입니다. 커밋을 하고 난 직후에는 working directory 안의 모든 파일들이 이 상태가 됩니다.
2-3. Modified 상태: 최신 커밋의 모습과 비교했을 때 조금이라도 바뀐 내용이 있는 상태면 그 파일은 Modified(수정된) 상태입니다. 이렇게 Git에서 파일은 매 순간 4가지 상태 중 하나의 상태에 있게 됩니다. 이 내용을 그림으로 정리하면 아래와 같습니다.

Add the file : Untracked 상태의 파일을 처음으로 git add 해주면 Staged 상태가 됩니다.
Edit the file : 최신 커밋과 비교했을 때 차이가 없는 Unmodified 상태의 파일의 내용을 수정하면 Modified 상태가 됩니다.
Stage the file : Modified 상태의 파일을 git add 해주면 Staged 상태가 됩니다.
Remove the file : 파일을 삭제하면 당연히 Git에서 더이상 인식하지 않겠죠?
Commit : 커밋을 하면 staging area에 있던 파일들이 커밋에 반영되고, 이제 모든 파일들은 최신 커밋과 차이가 없게 되니까 Unmodified 상태가 됩니다.

1. git add 취소하기
git reset 파일명
-> staging area 에서 파일 제거, 변경된 새 모습은 그대로 working dir에 남아있음
working tree(dir) clean (=no change)
2. 특정 git 커맨드의 사용법 알아보기[윈도우]
git [command] -h //커맨드 창에 간단히 출력
git [command] --help 또는 git help add //매뉴얼 사이트 이동
3. 퀴즈
4. 깃써보기 정리노트
git init : 현재 디렉토리를 Git이 관리하는 프로젝트 디렉토리(=working directory)로 설정하고 그 안에 레포지토리(.git 디렉토리) 생성
git config [user.name](http://user.name/) 'codeit' : 현재 사용자의 아이디를 'codeit'으로 설정(커밋할 때 필요한 정보)
git config user.email 'teacher@codeit.kr' : 현재 사용자의 이메일 주소를 'teacher@codeit.kr'로 설정(커밋할 때 필요한 정보)
git add [파일 이름] : 수정사항이 있는 특정 파일을 staging area에 올리기
git add [디렉토리명] : 해당 디렉토리 내에서 수정사항이 있는 모든 파일들을 staging area에 올리기
git add . : working directory 내의 수정사항이 있는 모든 파일들을 staging area에 올리기
git reset [파일 이름] : staging area에 올렸던 파일 다시 내리기
git status : Git이 현재 인식하고 있는 프로젝트 관련 내용들 출력(문제 상황이 발생했을 때 현재 상태를 파악하기 위해 활용하면 좋음)
git commit -m "커밋 메시지" : 현재 staging area에 있는 것들 커밋으로 남기기
git help [커맨드 이름] : 사용법이 궁금한 Git 커맨드의 공식 메뉴얼 내용 출력
앞으로 각 챕터에서 새롭게 배운 커맨드들은 이렇게 정리하고 넘어가겠습니다.
5. github 계정과 remote repository 만들기
6. 로컬 레포지토리의 내용을 리모트 레포지토리로 보내기
로컬 레포지토리(내컴-MathTool) <-> 리모트 레포지토리(깃헙-Math_Box: MathTool의 복제본)

//cf, git bash 붙여넣기 shift + insert
// 복사 : ctrl + insert

1. 로컬 레포지토리에서 변경내용을 리모트 레포지토리에 반영하기
로컬 레포지토리에서 내용 변경할 경우
2. git add //staging area에 올리기
3. git commit //로컬레포지토리에 커밋하기
4. git push //로컬레포지토리에서 리모트 레포지토리로 반영하기
5. 리모트 레포지토리에서 변경내용을 로컬 레포지토리에 반영하기
6. git pull
리모트 레포지토리에서 pull하는 이유
7. 안전성 : 내 컴퓨터를 쓰지 못하게 된 경우
8. 협업가능
9. 퀴즈
10. git push 사용자 설정
사실 git push는 리모트 레포지토리의 주인, 그러니까 본인만 할 수 있습니다. 만약 본인이 아닌 다른 사용자도 git push를 할 수 있게 하려면 GitHub에서 추가 작업을 해줘야 합니다. -> manage access로 불러오기
11. 다른 프로젝트 가져오기
git clone [html]
12. 오픈 소스 프로젝트(open source project)
장점
무료로 사용할 수 있다.
여러 개발자들이 참여하기 때문에 폐쇄적으로 코드를 관리할 때보다 코드의 신뢰도가 더 높다.(이 부분은 사람마다 의견이 다를 수 있습니다)
오픈 소스 프로젝트에 참여 중인 다른 개발자들에게 질문을 할 수 있다.
어떤 프로그램을 개발할 때 특정 분야에서 사실상 표준처럼 사용되는 오픈 소스 프로그램을 많이 활용할수록 전체 개발 속도를 단축시킬 수 있다.

반면에 단점은
참여자 수가 많지 않거나, 참여자의 실력이 좋지 않으면 소스 코드의 신뢰성을 보장하기 어렵다.
해당 오픈 소스를 사용해서 문제가 생겼을 때 보상을 해주거나, 책임을 질 주체가 없다.

1. [README.md](http://readme.md/) 파일
이 프로젝트가 어떤 프로젝트인지 설명하거나
프로그램의 주요 사용법을 알려주거나
프로그램을 실행시키려면 어떤 사전 작업이 필요한지를 알려주는 내용
마크다운 문법: [https://www.codeit.kr/topics/getting-started-with-data-science/lessons/975](https://www.codeit.kr/topics/getting-started-with-data-science/lessons/975)
2. 퀴즈
3. 깃헙 시작하기 정리노트
git push -u origin master : 로컬 레포지토리의 내용을 처음으로 리모트 레포지토리에 올릴 때 사용합니다.(-u origin master가 무슨 뜻인지는 'Git에서 브랜치 사용하기' 챕터에서 배울 거니까 걱정마세요!)
git push : 로컬 레포지토리의 내용을 리모트 레포지토리에 보내기
git pull : 리모트 레포지토리의 내용을 로컬 레포지토리로 가져오기
git clone [프로젝트의 GitHub 상 주소] : GitHub에 있는 프로젝트를 내 컴퓨터로 가져오기
4. 커밋 히스토리
git log // commit [커밋 아이디/커밋 해시]
git log --pretty=oneline

git show [커밋아이디 4자리정도] // 해당 커밋과 그 다음 커밋이 어떻게 다른지 --(과거) 와 ++(현재)로 보여줌

1. m 옵션 없이도 커밋 메세지 남기기
->vim이 뜸, 복잡하고 긴 메세지 작성 편함
2. 최신 커밋 수정하기
git commit --amend
Q: 최신만 가능함?
3. 커밋 생성, 커밋 메세지 작성 가이드라인
4. 커밋 메시지 작성 가이드라인

(1) 커밋 메시지의 제목과 상세 설명 사이에는 한 줄을 비워두세요.
제목

상세설명
(2) 커밋 메시지의 제목 뒤에 온점(.)을 붙이지 마세요.
(3) 커밋 메시지의 제목의 첫 번째 알파벳은 대문자로 작성하세요.
(4) 커밋 메시지의 제목은 명령조로 작성하세요.(Fix it / Fixed it / Fixes it)
(5) 커밋의 상세 내용에는 이런 걸 적으면 좋습니다.
왜 커밋을 했는지
어떤 문제가 있었고
적용한 해결책이 어떤 효과를 가지는지
(6) 다른 사람들이 자신의 코드를 바로 이해할 수 있다고 가정하지 말고 최대한 친절하게 작성하세요.

1. 커밋할 때 알아야할 가이드라인
(1) 하나의 커밋에는 하나의 수정사항, 하나의 이슈(issue)를 해결한 내용만 남기도록 하세요. 다양하게 수정을 하고나서 하나의 커밋으로 남기는 것은 좋지 않습니다. 하나의 커밋이 하나의 사실만을 갖고 있어야 나중에 이해하기 쉽습니다.

(2) 현재 프로젝트 디렉토리의 상태가 그 내부의 전체 코드를 실행했을 때 에러가 발생하지 않는 상태인 경우에만 커밋을 하도록 하세요. 나중에 동료 개발자가 특정 커밋의 코드로 실행했을 때 에러가 발생한다면 혼란을 줄 수 있습니다.

커밋으로 보관된 특정 시점의 전체 코드는 항상 문제없이 실행되는 상태여야 합니다. 이미 과거의 커밋이 되어버렸다고 우리에게 쓸모없는 커밋이 되는 건 절대 아닙니다. 과거의 커밋이라도

과거 버전의 프로그램을 사용해야하거나
과거 커밋을 시작점으로 한 다른 방향의 별도 프로젝트를 시작하거나
아예 그 커밋으로 현재 프로젝트를 리셋할 수도 있습니다.

1. 긴 커맨드에 alias 설정
git config alias.history 'log --pretty=oneline'

git log --pretty=oneline 대신 git history 사용

1. 두 커밋 간의 차이 보기
git diff [이전 커밋 아이디] [이후 커밋 아이디]
2. 퀴즈
3. HEAD의 의미
보통 가장 최근에 한 커밋으로 매번 더 새로운 커밋을 가리킴
head에 따라 그 때 상태 working dir가 바뀜
4. 이전 커밋으로 git reset하기
git reset --hard [커밋 아이디]
git reset : 과거 커밋으로 돌아가기
5. git reset의 옵션을 배우기 전에 확실히 알아야 할 부분
커밋을 하고 나면 staging area에 있던 파일들은 어떻게 될까요? 사라지는 걸까요?
그건 아닙니다. 그냥 그 상태 그대로 남아있습니다. 그러니까 커밋을 했다고 staging area가 초기화되거나 하지는 않는 겁니다.
계속 git add를 할 때마다 staging area에서는 새로운 파일이 추가되거나 원래 있던 파일이 더 새로운 버전의 것으로 교체되거나 할 뿐입니다.
원래 있던 게 사라지는 게 아니라요. staging area에 있던 것들은 커밋을 하더라도 그것과 상관없이 계속 남아있다는 점, 잘 기억하세요!
6. git reset의 3가지 옵션
--soft
--mixed
--hard

11-1. error:failed to push some refs to
github에 내 Local 에 없는 파일이 있고, 내 파일을 push 할 면 발생하는 오류이다.

Pull is not possible because you have unmerged files 에러

git push -f origin [브랜치 이름]				git branch 를 사용하면 현재 브랜치 확인 가능.
commit history를 강제로 push하기 때문에 -f 또는 --force 명령어를 붙여줘야 한다.
원격 저장소에서 삭제되기 전에 다른 사람이 해당 브랜치의 커밋을 누군가 pull request했다면, pull한 사람의 로컬 저장소에는 적용이 안된다. 즉, 꼬일 수 있음.. 때문에 소통이 필요! 혹은 혼자 작업할 때 편한 방식.

1. head를 기준으로 git reset
git reset --hard HEAD^
HEAD^는 현재 HEAD가 가리키고 있는 커밋의 바로 이전 커밋을 나타냅니다. 즉, 이 상황에서는 5번 커밋을 나타내죠.

git reset --hard HEAD~2
여기서 HEAD~2는 현재 HEAD가 가리키는 커밋보다 2단계 전에 있는 커밋을 나타냅니다.

1. git tag
git tag [태그 이름] [커밋 아이디] //tag 달기
git tag //전체 tag 조회
git show [태그 이름] //특정 tag 조회
git tag -d [태그 이름] //특정 tag 지우기
2. 퀴즈
3. 커밋 다루기 정리노트
git log : 커밋 히스토리를 출력

git log --pretty=oneline : --pretty 옵션을 사용하면 커밋 히스토리를 다양한 방식으로 출력할 수 있습니다. --pretty 옵션에 oneline이라는 값을 주면 커밋 하나당 한 줄씩 출력해줍니다. --pretty 옵션에 대해 더 자세히 알고싶으면 이 링크를 참고하세요.

git show [커밋 아이디] : 특정 커밋에서 어떤 변경사항이 있었는지 확인

git commit --amend : 최신 커밋을 다시 수정해서 새로운 커밋으로 만듦

git config alias.[별명] [커맨드] : 길이가 긴 커맨드에 별명을 붙여서 이후로 별명으로 해당 커맨드를 실행할 수 있도록 설정

git diff [커밋 A의 아이디] [커밋 B의 아이디] : 두 커밋 간의 차이 비교

git reset [옵션] [커밋 아이디] : 옵션에 따라 하는 작업이 달라짐(옵션을 생략하면 --mixed 옵션이 적용됨)

(1) HEAD가 특정 커밋을 가리키도록 이동시킴(--soft는 여기까지 수행)

(2) staging area도 특정 커밋처럼 리셋(--mixed는 여기까지 수행)

(3) working directory도 특정 커밋처럼 리셋(--hard는 여기까지 수행)

그리고 이때 커밋 아이디 대신 HEAD의 위치를 기준으로 한 표기법(예 : HEAD^, HEAD~3)을 사용해도 됨

git tag [태그 이름] [커밋 아이디] : 특정 커밋에 태그를 붙임, 태그는 커밋을 가르키는 포인터

cf) git diff Ver1 Ver2 가능

2~3
5. 브랜치 사용하기

1. 브랜치란
깃은 root commit을 기반으로 갈라지는 branch (ex:유료 무료)
branch main : 처음 생성되는 브랜치
코드 관리 흐름: branch
2. 브랜치 다뤄보기
git branch : 모든 브랜치 찾기
git branch [name] : [name] 브랜치 생성하기
git branch -d [name] : delete, [name] 브랜치 삭제하기
3. 퀴즈
Q. branch의 범위 할당 가능?
4. 브랜치 merge하기
브랜치A에서 한 커밋을 B에도 반영할 수 있다
브랜치 B에서 git merge A
//merge commit이라는 커밋이 새로 생성
-> 다..?
5. merge할 때 conflict가 날 수 있어요
main과 premium중 뭐로 정할지 정하기
6. conflict가 났을 때 merge 자체를 취소해도 됩니다
머지를 시도하기 이전의 상태로 돌아가고 싶다면 그냥 머지 자체를 취소하는 방법도 있는데요.
git merge --abort
7. 여러 파일에서 conflict가 나면? git status 커맨드를 사용하여 conflict 발생한 파일 확인
8. 퀴즈
9. Remote repository의 브랜치는 이렇게 보입니다!
10. origin이란?
먼저 첫 번째 커맨드를 봅시다.
git remote add origin [https://github.com/kyuri-dev/Math_Box.git](https://github.com/kyuri-dev/Math_Box.git)
이 커맨드에서 remote는 리모트 레포지토리에 관한 작업을 할 때 쓰는 커맨드입니다.
그리고 그 뒤의 add는 새로운 리모트 레포지토리를 등록하겠다는 뜻입니다.
그 다음에는 origin [https://github.com/kyuri-dev/Math_Box.git이라고](https://github.com/kyuri-dev/Math_Box.git%EC%9D%B4%EB%9D%BC%EA%B3%A0) 써있죠?
이 표현은 [https://github.com/kyuri-dev/Math_Box.git](https://github.com/kyuri-dev/Math_Box.git) 리모트 레포지토리를 origin이라는 이름으로 등록하겠다는 뜻입니다.
그러니까 이 커맨드를 실행하고 나면 [https://github.com/kyuri-dev/Math_Box.git를](https://github.com/kyuri-dev/Math_Box.git%EB%A5%BC) origin으로 간단하게 나타낼 수 있게 되는 거죠.
그럼 왜 하필 origin이라고 하는 걸까요? origin이 아닌 여러분이 원하는 다른 단어를 입력해도 큰 상관은 없습니다. 하지만 Git에서는 리모트 레포지토리를 최초로 추가할 때 origin이라는 이름으로 가리키는 것이 관례화되어 있습니다.
origin은 ‘근원’, ‘기원’이라는 뜻을 가집니다. 아마도 다른 사람의 리모트 레포지토리를 자신의 컴퓨터로 가져와서 작업을 하는 사람의 입장에서는 리모트 레포지토리가 프로젝트의 근원이 되는 존재이기 때문에 그런 관습이 생긴 것으로 추측됩니다.
사실
git remote add hello [https://github.com/kyuri-dev/Math_Box.git](https://github.com/kyuri-dev/Math_Box.git)
처럼 origin 대신 우리가 원하는 단어(hello)를 써도 상관은 없지만, 되도록 관례에 따라 origin을 써주는 게 좋겠죠?
11. Remote Repositoy에 있는 브랜치
이제 두 번째 커맨드를 설명해드릴게요.

git push -u origin master

이 커맨드의 뜻은

현재 로컬 레포지토리에 있는 master 브랜치의 내용(=master 브랜치와 관계된 모든 커밋들)을
origin이라는 리모트 레포지토리로 보낸다는 뜻입니다.
이때 같은 이름의 브랜치로 전송하게 되는데 만약 origin이라는 리모트 레포지토리에 master 브랜치가 없으면 master 브랜치를 새로 생성하고 푸시합니다.
그런데 여기서 옵션 -u는 무슨 뜻일까요? -u는 --set-upstream이라는 옵션의 약자입니다.

이렇게 --set-upstream(-u) 옵션을 주면

로컬 레포지토리에 있는 master 브랜치가
origin에 있는 master 브랜치를 tracking(추적)하는 걸로 설정됩니다.
tracking이라는 건 로컬 레포지토리의 한 브랜치가 리모트 레포지토리의 한 브랜치와 연결되어 그것을 계속 바라보는 상태가 되는 것이라고 생각하시면 됩니다. 이렇게 맺어진 연결 상태를 tracking connection이라고 합니다.

만약

로컬 레포지토리에 A라는 브랜치가 있고,
리모트 레포지토리에 B라는 브랜치가 있을 때
이런 tracking connection이 서로 맺어진 경우,
B 브랜치를 A 브랜치의 upstream branch라고 합니다.
지금은 구별하기 위해서 A와 B라고 표현했지만 보통은 같은 이름인 경우가 대부분입니다.
이렇게 tracking connection이 한번 설정되고 나면,
사용자가 현재 master 브랜치에 위치해있을 때, git push
라고만 써도 자동으로 리모트 레포지토리의 master 브랜치를 대상으로 git push가 동작하고,

git pull
라고만 써도 리모트 레포지토리의 master 브랜치를 대상으로 git pull이 동작합니다.

사실 --set-upstream(-u) 옵션을 주지 않아도 그 후에 git push와 git pull을 할 수 있기는 합니다. 하지만 맨 처음에 이 옵션을 주지 않으면 tracking connection이 없기 때문에 나중에 git push를 하고 싶을 때

git push origin master:master
이런 식으로 적어줘야 합니다. 여기서

origin은 리모트 레포지토리를 나타내고,
master:master에서 더 먼저 나오는 master는 로컬 레포지토리의 master 브랜치(~에서)/더 뒤에 나오는 master는 리모트 레포지토리의 master 브랜치(~으로)를 나타냅니다.
그러니까 tracking connection이 없으면 매번 이런 식으로 git push를 해줘야 합니다. git pull도 마찬가지로 이런 식의 복잡한 표현이 필요하게 됩니다.

그러니까 그냥 처음부터 tracking connection을 설정하고 그 이후부터는 git push, git pull이라고만 써서 편하게 푸시와 풀을 하는 게 좋겠죠? 이게 바로 제가 맨 처음에 로컬 레포지토리의 내용을 리모트 레포지토리로 보낼 때 -u라는 옵션을 썼던 이유입니다.

1. origin/master의 의미
자, 이제

로컬 레포지토리의 master 브랜치
리모트 레포지토리의 master 브랜치
이렇게 같은 이름이지만, 서로 다른 2개의 브랜치가 있다는 걸 알겠죠?

그럼 리모트 레포지토리에 있는 master 브랜치는 어떻게 볼 수 있을까요? GitHub 페이지에서 보면 될 겁니다.
master가 로컬 레포지토리의 master 브랜치를 나타내고
origin/master가 리모트 레포지토리의 master 브랜치를 나타냅니다.
이때까지 로컬 레포지토리의 master 브랜치에서 여러 커밋을 했지만 그러고나서 git push를 해준 적은 없었습니다. 그래서 위 그림처럼 origin/master가 master보다 이전의 커밋을 가리키고 있는 겁니다.

다음 영상에서는 master, premium 브랜치 둘 다에서 리모트 레포지토리로 git push 하겠습니다. 그러고 나면 이제 origin/master도 master와 같은 커밋을 가리키게 될 것입니다.

1. master 브랜치와 preminum 브랜치 둘 다 push하기
Q push와 commit의 차이?
2. HEAD와 브랜치의 관계(사진)
브랜치 : 코드를 관리하는 하나의 흐름 -> 어떤 커밋을 가리키는 존재 -> 포인터
헤드는 브랜치를 가르킴
HEAD는 보통 본인이 직접 커밋을 가리키는 게 아니라 브랜치를 통해서 간접적으로 커밋을 가리킵니다.
3. git reset의 비밀
과거의 커밋으로 git reset을 한다고 그 이후의 커밋들이 삭제되는 게 절대 아닙니다. 계속 남아있습니다.
git reset은 과거의 커밋뿐만 아니라 현재 HEAD가 가리키는 커밋 이후의 커밋으로도 할 수 있습니
4. git reset과 git checkout의 차이
Detached HEAD입니다. Detached는 우리말로 ‘~로부터 떨어진, 분리된’이라는 뜻을 갖는데요. 브랜치로부터 떨어진 상태이기 때문에 이렇게 부르는 겁니다.
이렇게 HEAD가 특정 커밋을 직접 가리키게 하는 이유는 여러가지가 있을 수 있는데요.
그 중에서 주된 이유 한 가지는 바로 과거의 특정 커밋에서 새로운 브랜치를 만들고 싶을 때입니다.

git checkout master

이 커맨드의 뜻은 다음과 같이 해석됩니다.

= master 브랜치로 이동하라
= HEAD가 master 브랜치를 가리키도록 하라
= HEAD가 master 브랜치가 가리키던 커밋을 간접적으로 가리키게 됨으로써
= working directory의 내부도 그 커밋에 맞게 변함으로써
= master 브랜치로 이동한 것을 사용자는 실감하게 됨

이렇게 되는 거죠.

1. 새로운 커밋을 만들지 않는 merge도 있다
새로운 커밋이 생기는 게 아니라 단지 브랜치가 이동하게 되는 머지를 Fast-forward 머지
커밋 히스토리에서 같은 선(line) 상에 있는 브랜치를 머지할 때 Fast-forward 머지가 이루어집니다. 방금 전에는 master 브랜치와 premium 브랜치가 둘다 같은 선 상에 있었죠? 바로 이런 경우입니다.
두 브랜치가, 커밋 히스토리 상에서 분리된 2개의 선에 각각 존재할 때 머지를 하면 머지 커밋이 새롭게 생기는 거구요. 그리고 이런 머지는 3-way merge라고 합니다. 이름이 3-way인 이유는 지금 1, 2, 3 표시한 3가지 커밋을 고려해서 머지를 하기 때문입니다. 3-way merge는 base에서 변화가 발생한 것을 우선 채택
[https://www.codeit.kr/topics/git/lessons/2931](https://www.codeit.kr/topics/git/lessons/2931)
2. 퀴즈
3. 정리노트
git branch [새 브랜치 이름]: 새로운 브랜치를 생성
git checkout -b [새 브랜치 이름]: 새로운 브랜치를 생성하고 그 브랜치로 바로 이동
git branch -d [기존 브랜치 이름]: 브랜치 삭제
git checkout [기존 브랜치 이름]: 그 브랜치로 이동
git merge [기존 브랜치 이름]: 현재 브랜치에 다른 브랜치를 머지
git merge --abort: 머지를 하다가 conflict가 발생했을 때, 일단은 머지 작업을 취소하고 이전 상태로 돌아감

3~4
6. 깃 협업하기

1. 지금부터 배울 git 실무지식
2. git push 전에 git pull해야하는 경우가 많을 걸
로컬 레포지토리(수정) <- 리모트 레포지토리(수정)
git pull: 리모트 레포지토리의 브랜치를 가져와서 현재 브랜치에 "merge"하는 동작
누군가 깃푸시를 했다
-> 나는 먼저 깃pull을 해서 merge conflict 해결
-> git push
3. git pull말고 git fetch도 있오
merge는 안하고 가져오기만 하는 git fetch
리모트 레포지토리에 있는 브랜치의 내용을 일단 가져와서 살펴본 후에 머지 하고 싶을 때 사용
(git pull하기 의심스러울 때)
git fetch -> git diff [리모트 레포지토리] [로컬 레포지토리:origin/[name]]

리모트 레포지토리에 있는 브랜치 내용과 내가 작성한 코드를 비교해서 잘못된 부분이 없는지 검토해야 할 때

1. 이 코드는 누가 작성했을까?
git blame [파일 명] or git show
2. 이미 remote repository에 올라간 커밋을 취소해야한다면?
커밋을 취소하는 커밋
git revert [commitID] -> git push 해줘야 함
리셋하면 안됨?? - 로컬만 가능, 리모트 있으면 안됨
b/c 리모트가 더 최신이라 push가 안되고 pull해야 됨
3. 여러 커밋 취소하기
Q: 한꺼번에만 가능?
4. 퀴즈
5. 깃 협업하기 정리노트
git fetch: 로컬 레포지토리에서 현재 HEAD가 가리키는 브랜치의 업스트림(upstream) 브랜치로부터 최신 커밋들을 가져옴(가져오기만 한다는 점에서, 가져와서 머지까지 하는 git pull과는 차이가 있음)
git blame: 특정 파일의 내용 한줄한줄이 어떤 커밋에 의해 생긴 것인지 출력
git revert: 특정 커밋에서 이루어진 작업을 되돌리는(취소하는) 커밋을 새로 생성
6. 깃 자유자재로 활용하기
7. git reset을 하고 나서 돌아오려면?
최신커밋을 알아야되는데??
git reflog : 헤드가 가르켜온 커밋들을 알려줌
8. 커밋 히스토리를 보는 다양한 방법
현재 브랜치와 다른 브랜치까지 커밋 히스토리 보기
git log --pretty=oneline --all --graph
//철자조심
9. 깃을 gui환경에서 사용할 수 있게 해주는 프로그램 Sourcetree
[https://support.atlassian.com/bitbucket-cloud/docs/tutorial-learn-bitbucket-with-sourcetree/](https://support.atlassian.com/bitbucket-cloud/docs/tutorial-learn-bitbucket-with-sourcetree/)
10. 퀴즈
11. 깔끔한 커밋 히스토리를 원할 땐 git merge 대신 git rebase
git rebase --continue // 커밋재배치한다. 프리미엄 브랜치의 베이스를 테스트 브랜치로 재지정
//충돌 때문에 제대로 진행안된 리베이스 계속 진행
새로운 커밋X
합쳤다는 정보가 필요한경우 - merge
좀 더 깔끔하게 사용하려면 - rebase
12. 작업 내용 임시 저장하기
다른 브랜치로 가면 working directory가 재설정되니까 문제가 됨
git stash: 안전한 곳에 보관하다, 넣어두다 => stack에 저장
git stash list // 스택에 저장된 stash들 보여주기
git stash apply //다시 가져오기(가장 최신 것)
13. 잘못된 브랜치에서 작업하고 있었다면?
git stash로 받아와서 apply //브랜치 상관 없음
14. 적용한 작업내용은 스택에서 없애기
git stash drop stash@{[num]}
git stash pop [작업 내용의 아이디] // 작업 내용을 적용하면서 동시에 스택에서 제거
15. 퀴즈
16. 필요한 커밋만 가져오는 git cherry-pick
git cherry-pick [커밋아이디]
//merge의 축소화
17. 여러 커밋을 하나의 커밋으로 만들기
git reset으로!
18. 깃이 무시하는 파일들
.gitignore 파일은
working directory 내에 존재하는 파일들 중에서
마치 존재하지 않는 것처럼
Git이 인식해야할 파일들의 목록이 적힌 파일입니다.
만약 여러분이 working directory에서 버전 관리를 할 필요가 없는 것들이 있다면 이렇게 .gitignore 파일에 그 이름을 추가하고 버전 관리를 시작하세요. 그럼 좀더 깔끔하게 버전 관리를 할 수 있습니다.
*.py[cod]
*$py.class
*.so
19. 퀴즈
20. 내용 총정리
21. Git 써보기
git init : 현재 디렉토리를 Git이 관리하는 프로젝트 디렉토리(=working directory)로 설정하고 그 안에 레포지토리(.git 디렉토리) 생성
git config [user.name](http://user.name/) 'codeit' : 현재 사용자의 아이디를 'codeit'으로 설정(커밋할 때 필요한 정보)
git config user.email 'teacher@codeit.kr' : 현재 사용자의 이메일 주소를 'teacher@codeit.kr'로 설정(커밋할 때 필요한 정보)
git add [파일 이름] : 수정사항이 있는 특정 파일을 staging area에 올리기
git add [디렉토리명] : 해당 디렉토리 내에서 수정사항이 있는 모든 파일들을 staging area에 올리기
git add . : working directory 내의 수정사항이 있는 모든 파일들을 staging area에 올리기
git reset [파일 이름] : staging area에 올렸던 파일 다시 내리기
git status : Git이 현재 인식하고 있는 프로젝트 관련 내용들 출력(문제 상황이 발생했을 때 현재 상태를 파악하기 위해 활용하면 좋음)
git commit -m "커밋 메시지" : 현재 staging area에 있는 것들 커밋으로 남기기
git help [커맨드 이름] : 사용법이 궁금한 Git 커맨드의 공식 메뉴얼 내용 출력
22. GitHub 시작하기
git push -u(또는 --set-upstream) origin master : 로컬 레포지토리의 내용을 처음으로 리모트 레포지토리에 올릴 때 사용합니다.
git push : 위의 커맨드를 한번 실행하고 난 후에는 git push라고만 쳐도 로컬 레포지토리의 내용을 리모트 레포지토리에 올릴 수 있습니다.
git pull : 바로 위의 위에 있는 커맨드를 한번 실행하고 난 후에는 git pull이라고만 쳐도 리모트 레포지토리의 내용을 로컬 레포지토리로 가져옵니다.
git clone [프로젝트의 GitHub 상 주소] : GitHub에 있는 프로젝트를 내 컴퓨터로 가져오기
23. Git에서 커밋 다루기
git log : 커밋 히스토리를 출력

git log --pretty=oneline : --pretty 옵션을 사용하면 커밋 히스토리를 다양한 방식으로 출력할 수 있습니다. --pretty 옵션에 oneline이라는 값을 주면 커밋 하나당 한 줄씩 출력해줍니다. --pretty 옵션에 대해 더 자세히 알고싶으면 이 링크를 참고하세요.

git show [커밋 아이디] : 특정 커밋에서 어떤 변경사항이 있었는지 확인

git commit --amend : 최신 커밋을 다시 수정해서 새로운 커밋으로 만듦

git config alias.[별명] [커맨드] : 길이가 긴 커맨드에 별명을 붙여서 이후로는 별명으로도 해당 커맨드를 실행할 수 있게 설정

git diff [커밋 A의 아이디] [커밋 B의 아이디] : 두 커밋 간의 차이 비교

git reset [옵션] [커밋 아이디] : 옵션에 따라 하는 작업이 달라짐(옵션을 생략하면 --mixed 옵션이 적용됨)

(1) HEAD가 특정 커밋을 가리키도록 이동시킴(--soft는 여기까지 수행)

(2) staging area도 특정 커밋처럼 리셋(--mixed는 여기까지 수행)

(3) working directory도 특정 커밋처럼 리셋(--hard는 여기까지 수행)

그리고 이때 커밋 아이디 대신 HEAD의 위치를 기준으로 한 표기법(예 : HEAD^, HEAD~3)을 사용해도 됨

git tag [태그 이름] [커밋 아이디] : 특정 커밋에 태그를 붙임

1. Git에서 브랜치 사용하기
git branch [새 브랜치 이름] : 새로운 브랜치를 생성
git checkout -b [새 브랜치 이름] : 새로운 브랜치를 생성하고 그 브랜치로 바로 이동
git branch -d [기존 브랜치 이름] : 브랜치 삭제
git checkout [기존 브랜치 이름] : 그 브랜치로 이동
git merge [기존 브랜치 이름] : 현재 브랜치에 다른 브랜치를 머지
git merge --abort : 머지를 하다가 conflict가 발생했을 때, 일단은 머지 작업을 취소하고 이전 상태로 돌아감
2. Git 실전 I
git fetch : 로컬 레포지토리에서 현재 HEAD가 가리키는 브랜치의 업스트림(upstream) 브랜치로부터 최신 커밋들을 가져옴(가져오기만 한다는 점에서, 가져와서 머지까지 하는 git pull과는 차이가 있음)
git blame : 특정 파일의 내용 한줄한줄이 어떤 커밋에 의해 생긴 것인지 출력
git revert : 특정 커밋에서 이루어진 작업을 되돌리는(취소하는) 커밋을 새로 생성
3. Git 실전 Ⅱ
git reflog : HEAD가 그동안 가리켜왔던 커밋들의 기록을 출력
git log --all --graph : 모든 브랜치의 커밋 히스토리를, 커밋 간의 관계가 잘 드러나도록 그래프 형식으로 출력
git rebase [브랜치 이름] : A, B 브랜치가 있는 상태에서 지금 HEAD가 A 브랜치를 가리킬 때, git rebase B를 실행하면 A, B 브랜치가 분기하는 시작점이 된 공통 커밋 이후로부터 존재하는 A 브랜치 상의 커밋들이 그대로 B 브랜치의 최신 커밋 이후로 이어붙여짐(git merge와 같은 효과를 가지지만 커밋 히스토리가 한 줄로 깔끔하게 된다는 차이점이 있음)
git stash : 현재 작업 내용을 스택 영역에 저장
git stash apply [커밋 아이디] : 스택 영역에 저장된 가장 최근의(혹은 특정) 작업 내용을 working directory에 적용
git stash drop [커밋 아이디] : 스택 영역에 저장된 가장 최근의(혹은 특정) 작업 내용을 스택에서 삭제
git stash pop [커밋 아이디] : 스택 영역에 저장된 가장 최근의(혹은 특정) 작업 내용을 working directory에 적용하면서 스택에서 삭제
git cherry-pick [커밋 아이디] : 특정 커밋의 내용을 현재 커밋에 반영
! 그 밖에 알아야할 사실

(1) git commit이라고만 쓰고 실행하면 커밋 메시지를 입력할 수 있는 텍스트 에디터 창이 뜹니다. 거기서 커밋 메시지를 입력하고 저장하고 나면 커밋이 이루어집니다.

(2) git push와 git pull은 그 작업 단위가 브랜치입니다. 예를 들어, master 브랜치에서 git push를 하면 master 브랜치의 내용만 리모트 레포지토리의 master 브랜치로 전송되지, premium 브랜치의 내용이 전송되는 것은 아닙니다.(git push에 --all이라는 옵션을 주면 모든 브랜치의 내용을 전송할 수 있기는 합니다.)

자, Git 토픽에서 배운 커맨드들을 쭉 정리해봤는데요. 기억이 다 잘 나시나요? 이 커맨드들만 제대로 이해하고 사용해도 여러분이 어디에서 어떤 일을 하든 Git을 사용할 때 불편함이 없을 겁니다. 혹시라도 Git으로 아주 세밀한 작업 또는 여기서 배우지 않은 새로운 커맨드를 써야한다고 할지라도 겁낼 필요가 없습니다. 이 토픽에서는 커맨드 뿐만 아니라 Git의 내부 동작 원리도 제대로 배웠기 때문에 여러분이 조금만 노력하면 그런 것들도 금방 쉽게 할 수 있을 겁니다.

이제 어디를 가도 '나 Git 쓸 줄 알아!' 라고 자신있게 말할 수 있게 되신 여러분, 축하합니다!