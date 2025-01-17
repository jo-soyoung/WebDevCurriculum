# Quest 00. 형상관리 시스템

## Introduction
* git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics
* git
  * `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  * `.git` 폴더
* GitHub

## Resources
* [Resources to learn Git](https://try.github.io)
* [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
* [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist
### * 형상관리 시스템은 왜 나오게 되었을까요?
  - 형상 관리 = 구성 관리 (Configuration Management)
  - 정의? <br/>
  원하는 상태로 일관되게 유지하는 프로세스. 다양한 변경 사항이 적용되더라도 시스템이 정상 작동할 수 있도록 함.
  - 그래서 왜 필요하냐면? <br/> 1) 모든 변경 사항들을 트래킹할 수 있음 <br/> 2) 모든 사람들이 technology assets이 어떻게 이뤄져 있는지 파악할 수 있음 <br/> 3) 그래서 효율적으로 여러 사람이 하나의 프로젝트에서 일할 수 있게 됨
  - cf. 버전 관리 시스템(VCS, Version Control System)

  | Configutaion Management | Version Contol System |
  |  :--:  |  :--:  |
  | 상품/제품(software)의 consistency를<br/>유지하기 위한 것에 초점 | 말 그대로 상품/제품(software)의 버전을 관리하는 시스템 |

<br/><br/>

### * git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?
  - git은 어떤 형상 관리 시스템?
    - 분산형 형상 관리 시스템 (Distributed VCS)
  - 분산형 형상 관리 시스템이 뭐냐면..
    - 중앙 집중식 형상 관리 시스템(Centralized VCS, Client-server VCS)과 비교해서 보면 이해하기 쉬움 <br/>

  | Centralized VCS | Distributed VCS |
  |  :--:  |  :--:  |
  | 중앙 서버가 존재 | 중앙 서버가 존재 |
  | 로컬 저장소 없음<br/> (중앙 서버만 모든 변경 사항들을 가지고 있음) | 로컬 저장소 있음<br/> (중앙 서버 외에 각각의 로컬 컴퓨터에서도<br/>모든 변경 사항을 가지고 있을 수 있음) |
  | 항상 중앙 서버와 연결되어 있어야 하기 때문에<br/>인터넷 연결이 필수 | 로컬 저장소가 있기 때문에<br/>인터넷 연결 없이도 개발 가능 |
  | synchronizing, tracking, backing up files에 초점 | 변경 사항들을 공유하는 것에 초점 |
  | *중앙 서버의 파일을 날리면 모든 버전이 날아감 | 중앙 서버가 날아가도<br/>로컬 저장소의 기록을 이용해 복구 가능 |
  | <img src="https://t1.daumcdn.net/cfile/tistory/184C803F514047D41D" width="300"/> | <img src="https://t1.daumcdn.net/cfile/tistory/2511743F514047D442" width="300"/> |
  
<br/><br/>
### * git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
  - git이 어떻게 개발 되었냐면..
    - [History of Git](https://www.welcometothejungle.com/en/articles/btc-history-git)
    - git을 개발한 Linus Torvalds와 그의 팀은 Linux Kernel을 개발하면서 BK(BitKeeper)라는 VCS툴을 사용 중이었음. 당시 BK는 유료 툴이었지만 Linux 팀에게는 무료로 제공되고 있었고, 추후 BK측과 Linux 팀원 개발자와 갈등이 생기면서 더이상 무료로 사용하기 힘들어짐. 그래서 새로운 VCS 툴을 찾던 중 Linus는 git을 개발함.
  - git이 분산형 시스템을 채택한 이유는 뭐냐면..
    - Centralized VCS(aka Client-server VCS)는 개발 과정이 컨트롤 되고 서로 활발한 네트워킹이 있는 사내 개발팀에게는 좋을 수 있음. 하지만 당시 Linux 팀은 자발적으로 프로젝트에 참여한 수많은 개발자들과 협업해서 일하고 있었고 그들은 독립적이고 재택 근무 형태로 일을 하고 있었음.
    - Distributed VCS은 각각의 로컬에 저장된 파일들 중 가장 최신 상태를 복사해오는 형태로 운영되기 때문에 개발자들이 독립적으로 일하기 훨씬 편함. 
    - _“BK was the big conceptual influence for the usage model, and really should get all the credit. For various reasons, I wanted to make the Git implementation and logic completely different from BK, but the conceptual notion of ‘distributed VCS’ really was the number one goal, and BK taught me the importance of that,” says Torvalds. “Being truly distributed means forks are non-issues, and anybody can fork a project and do their own development, and then come back a month or a year later and say, ‘Look at this great thing I’ve done.’”_

  <br/><br/>

### * git과 GitHub은 어떻게 다를까요?
  | Git | GitHub |
  |  :--:  |  :--:  |
  | 개발자들이 소스코드를 관리하기 위해<br/> 설치하고 사용하는 오픈 소스 툴 | Git을 사용하는 개발자들이 모여<br/>리소스를 올리고 다운로드받는 곳 |

  <img src="https://cdn.ttgtmedia.com/rms/onlineimages/serverside-git_vs_github.png" width="600"/>
<br/><br/>

### * git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?
1. `git clone <repository명> <directory명>` <br/>
기존의 repository를 새로운 로컬 directory로 복사해오기 위한 명령어
2. `git add <변경된 파일명>` 혹은 `git add *`<br/>
코드 변경 사항을 working directory에서 staging area에 추가하기 위한 명령어 <br/>
(참고로, staging area에 들어간 순간부터 git이 해당 코드를 인식하고 추적할 수 있음)

3. `git commit -m <커밋메시지>`<br/>
변경사항들을 commit message라는 제목을 달아 저장소에 저장하는 명령어
commit까지 끝낸 다음에서야 GitHub에 push 할 수 있음
  <img src="https://www.w3docs.com/uploads/media/default/0001/03/ad19114d2f18ae7f7e8b99a5110d1a2f339282c6.png" width="400"/>

4. `git push origin <로컬 브랜치명>`<br/>
GitHub와 같은 원격 저장소(aka. origin)에 로컬 브랜치에 있는 커밋들을 올리는 명령어
 
5. `git pull`<br/>
GitHub와 같은 원격 저장소(aka.origin)로부터 최신 정보를 받아 로컬 브랜치에 합치는(aka. merge하는) 명령어<br/>
cf. `git pull --rebase` = `git rebase`<br/>merge하는 대신에 rebase 방식으로 로컬 브랜치를 업데이트하는 명령어 [git rebase](https://readystory.tistory.com/151)

6. `git branch <브랜치명>`<br/>
브랜치를 만드는 명령어

7. `git stash`<br/>
작업한 변경 사항들을 임시 저장하는 명령어 [git stash](https://blog.naver.com/cookr3/222547054926)

<br/><br/>

### * git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?

- Object
  - 기존 오리지널 파일들과 log 메시지, author 정보, 날짜 정보와 같이 수정 사항들을 새로 build하기 위한 모든 정보들을 갖고 있는 곳
  - _It contains your original data files and all the log messages, author information, dates, and other information required to rebuild any revision or branch of the project._
- Commit
  - author, committer, commit-data, log-messages와 같은 정보들이 수정되면 저장소(repository)에 정보를 저장하는 object
  - _A “commit” object holds metadata for each change introduced in the repository, including the author, committer, commit-data, and log- messages._
- Head
  - 현재 위치하고 있는 브랜치라고 생각하면 됨. `checkout` 명령어로 다른 브랜치로 이동하면 HEAD는 그 새로운 브랜치로 옮겨 감.
  - _The HEAD points out the last commit in the current checkout branch. It is like a pointer to any reference. The HEAD can be understood as the "current branch." When you switch branches with 'checkout,' the HEAD is transferred to the new branch._
- Branch
  - 저장소같은 개념. 각각의 저장소는 여러 다른 파일과 폴더 버전들을 참조함.
    - tree object와 같은 개념인듯?
  - _A “tree” is basically like a directory- it references a bunch of other trees and blobs (i.e. files and sub-directories)._
- Tag
  - 보통 commit과 같은 특정 object에 사람이 읽을 수 있는 이름으로 임의의 이름을 지정하는 object
  - _A “tag” object assigns an arbitrary human-readable name to a specific object usually a commit._
- 참고: [What is git object model](https://medium.com/mindorks/what-is-git-object-model-6009c271ca66), [What is git branch](https://www.atlassian.com/git/tutorials/using-branches)

<br/><br/>

### * 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
- 간단하게 요약하면, 로컬에서 되돌린 다음 되돌려진 결과를 remote repository에 push하면 됨
- 로컬에서 되돌리는 방법
  1) `git reset` <br/> git reset은 되돌렸다는 사실도 남지 않게 되돌리는 방법. 그래서 내가 되돌렸다고 하더라도 이 사실을 모르고 이전 커밋들을 pull 받아둔 동료가 다시 push하면 말짱 도루묵.
  2) `git revert` **추천!** <br/>
  되돌렸다는 것 자체도 커밋으로 기록됨. 완전히 뒤로 돌아간다기보단, 이전 상태의 파일들을 새롭게 커밋하는 명령어라고 생각하면 좋음.  <br/>
    - 

- [git reset과 revert](https://kyounghwan01.github.io/blog/etc/git/git-reset-revert/#%E1%84%8B%E1%85%B5-%E1%84%8C%E1%85%A1%E1%86%A8%E1%84%8B%E1%85%A5%E1%86%B8%E1%84%8B%E1%85%B3%E1%86%AF-%E1%84%92%E1%85%A1%E1%84%82%E1%85%B3%E1%86%AB-%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%B2)
- [원격 저장소에 올라간 커밋 되돌리기](https://jupiny.com/2019/03/19/revert-commits-in-remote-repository/)
- <img src="https://miro.medium.com/max/1400/1*8GsjZXPaKv-C_1eFK0D1XQ.png" width="600"/>
<br/><br/>


## Quest
* ✅ GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다.
* ✅ Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다.
  * ✅ 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다.
* ✅ 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다.
* ✅ `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다.
  - `git stash push -m "stash-test"` 타이틀 붙여서 임시 저장
  - `git stash list` 임시 저장한 리스트 보기
  - `git stash pop` 임시 저장한 제일 최신 애 꺼내면서 임시 저장소에선 지우기

## Advanced
* Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
  | Git | Mercurial |
  |  :--:  |  :--:  |
  | Distributed VCS | Distributed VCS |
  | 좀 더 Linux 친화적 | Windows에서 Git 보다 더 나은 성능 |
  | 기본 명령만 제공하는 것 같지만<br/> 명령 확장성이 좋음 | 명령 확장성은 좋지 않지만<br/> 이미 웬만한 명령어는 다 있음 |
  | 파일 전체 내용을 트래킹 <br/> = 저장소 용량이 급격히 올라감 <br/> = gc 명령으로 이걸 정리해 줌 | 변경된 내용만 트래킹 <br/> = git보다 저장소 용량이 완만하게 올라감 <br/> = 별도의 저장소 관리 필요없음 |
  | 스냅샷 기반이라 Mercurial보다 대체로 빠름 | - |


* 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
  | Facebook | Google |
  |  :--:  |  :--:  |
  | Mercurial | Piper (in-house) |

  - git의 단점 <br/>
  <img src="https://d2u3dcdbebyaiu.cloudfront.net/uploads/atch_img/177/467819caa4be6a14a9bb2aa650477043_res.jpeg" width="400"/>
