---
title: Git
date: 2021-11-08 23:33:33
tags: [git]
categories: [git]
---

# Git

## 1 GIt, Github

### 1.1 버전관리

Git은 VCS중 하나로 버전을 관리하는 시스템이다. 이렇게 버전관리 시스템이 있기 전에는 폴더에 버전을 붙여 버전별로 로컬에 저장하여 관리하였다. 이를 개선하기 위해 cvs, svn등의 형상관리 프로그램들이 나오게 된다. 이를 CVC(Centralized Version Control)이라고 하는데 각각이 개발자들이 서버에 작업한 내용들을 업데이트하고 즉각적으로 동기화된다. 이런 cvc의 문제점은 서버에 저장되는 형태이기 때문에 서버에 문제가 생길경우 매우 심각한 문제가 발생하고 오프라인 환경에서 작업할 경우 일을 할 수 없는 문제점이 있었다.  
Git의 경우 서버뿐 아니라 각각의 개발자의 컴퓨터에 서버와 동일한 히스토리를 저장한다. 안정적으로 동작하며 오프라인에서도 작업이 가능하다. Git을 사용할 때 회사 내부 서버에 Git을 설치하여 private하게 구축할수도 있고 Github나 Bitbucket같은 클라우드를 이용하고 할 수 있는데 특히 Github가 대중적으로 이용된다. 개발자의 sns라고 해도 과언이 아닐정도로 하나씩은 가지고 있는데 Git이 형상관리툴이라면 Github는 이를 클라우드 서버를 제공하여 업로드 할 수 있게 제공해준다. 온라인상에서 편하게 버전별 수정된 사항들도 볼 수 있고 댓글들도 제공하기 때문에 협업에도 굉장히 유용하다.

### 1.2 Git

Git은 프로젝트의 전체적인 내용을 스냅샷을 찍어 보관한다. 때문에 버전들을 자유롭게 변경하는것이 가능하고 Git의 특징인 브랜치를 나누고 합치는데 있어 오류를 줄였다. 또한 용량관리도 유리한데 매번 스냅샷이 모든 프로젝트 내용을 가지고 있는게 아니라 수정되지 않은 코드들은 이전 소스코들의 링크이기 때문이다.  
Git을 사용해야 하는 이유는

- 이제는 모르면 취업이 힘들정도로 많은 곳에서 사용중이다.
- 오픈소스이기에 무료로 사용가능하다.
- 모든 동작들이 빠르게 동작한다.
- 오프라인에서 작업이 가능하다.
- 서버에 문제가 생겨도 문제가 없을 정도로 안정적이다.
- 작업중 심각한 실수를 범했어도 버전 이동이 쉬워 이전버전으로 돌아가기 쉽다.
- 기능별로 브랜치를 나눠 개발할 수 있기 때문에 협업에 유리하다. 

## 2 셋팅

### 2.1 설치

Git을 사용하는 방법으로는 커멘드로 사용하는 방법과 전용 프로그램을 사용하는 방법이 있다. github desktop의 경우 기본적인 기능만사용 가능하기 때문에 추천하지 않는다. 가장 많이 사용하는 프로그램은 sourcetree가 있는데 전반적인 기능들을 사용할 수 있지만 UI가 단순하고 여전히 Git을 커멘드로 사용하는 것보다는 제한이 있다. UI가 화려한 걸 좋아한다면 GitKraken을 사용하면 된다. Git을 이해하고 있다면 소스트리나 깃 크라켄으로도 대부분의 기능을 사용할 수 있다.  
Git 커멘드를 사용하려면 당연히 터미널이 필요하다. 애플 환경에서는 iTerm2를 사용할 수 있고 윈도우에서는 cmder, Git설치시 자동으로 설치되는 git bash, cmd, powershell 등 편한 프로그램을 사용하면 된다.  
cmder을 설치하였다면 자동으로 Git이 설치되었을 것이고 Git을 다운받으려고한다면 https://git-scm.com/downloads 링크로 들어가면 다운받을 수 있다. 만약 본인이 설치했는지 모르겠다면 `git --version` 명령어를 입력하여 설치된 버전을 확인할 수 있다. Git 애플리케이션을 설치하려 한다면 https://www.sourcetreeapp.com/ 에서 소스트리를 https://www.gitkraken.com/ 경로에서 깃 크라켄을 다운로드 받아 설치하면 된다.

### 2.2 설정

git에 대한 모든 설정을 보고 싶다면 아래 명령어를 사용하면 된다.
``` 
git config --list
```
만약 설정한 내용을 파일로 확인하고 싶다면 아래 명령어를 사용한다.
```
git config --global -e
```
명령어를 사용하면 마치 vi에디터로 보는것처럼 파일내용을 터미널에서 볼 수 있다.
터미널에서 설정을 보는것이 불편하다면 에디터를 통해서도 볼 수 있다.
```
git config --global core.editor "code --wait"
```
global에 설정을 입력할 수 있는데 여기에 에디터를 설정할 수 있다. code는 vscode를 실행하는 명령어이다. --wait은 에디터를 실행하는 동안 터미널이 잠기는 기능을 의미한다. 이렇게 설정 후 다시 위에 에디터를 호출하면 프로그램이 실행된다.  
보통 설치가 완료되고 나면 id와 email을 설정하는데 github에 가입했다면 일치 시켜준다.
```
git config --global user.name "fkfkfk9"
git config --global user.email "fkfkfk999@gmail.com"
```
위처럼 global에 저장 id와 email을 저장해주면 된다.
```
git config --global core.autocrlf true
```
이것은 설정을 많이하는 부분인데 윈도우에선 개행을 \r\n으로 작성되고 리눅스나 맥에서는 \n으로만 입력되기 때문에 이를 일치시켜준다.  

### 2.3 초기화와 삭제

Git 레포지트리를 생성하려면 우선 터미널에서 레포지트리를 생성하고 싶은 경로로 이동한다.  
```
mkdir test
cd test
git init
ls -hidden
```
mkdir로 디렉토리를 만들어주고 cd를 이용해 해당 디렉토리로 이동한다. git init명령어를 통해 초기화를 해주고난 뒤 ls -hidden을 사용하여 숨겨진 파일을 조회하면 .git 폴더가 생성된 것을 확인할 수 있다.  
처음 초기화를 했다면 브랜치는 자동으로 master이 된다. 
삭제의 경우 .git 파일을 삭제해주면 되는데 터미널에서는 권한문제로 삭제가 힘들었다 윈도우인 만큼 해당 경로로 가서 폴더를 삭제해주면 된다.  
GitKraken을 사용하여 초기화 하는것은 매우 쉽다. 프로그램 설치 후 실행하였다면 Open a repo를 클릭하여 기존의 프로젝트를 열 수 있고 clone a repo를 사용하여 github에 있는 프로젝트를 내 로컬에 내려받을 수 있다. Start a local repo를 선택후 프로젝트 이름 프로젝트가 생성될 경로를 넣어주고 완료하면 커멘드와 동일한 프로젝트가 생성된다. 커멘드와 다르게 여러 설정을 해줄 수 있는데 이건 다음에 다루겠다.

### 2.4 명령어 별칭 설정

Git을 커멘드로 사용하다보면 자주 사용하는 기능들은 매번 입력하기 귀찮을 수 있다. 이럴경우 glocal에 alias를 입력하여 축약하여 사용이 가능하다.  
예를들어 아래는 status명령어를 축약하는 과정이다.
```
git status
git config --global alias.st status
git st
```

## 3 기본명령어

### 3.1 Git의 동작방식

Git에는 크게 3가지 작업환경이 있다. `wkroking directory`는 현재 작업하고 있는 폴더를 의미하고 `staging area`는 저장할 준비가 되어있는 파일들을 옮겨놓는다. `.git directory`는 버전의 히스토리를 보관하고 있다.  
`wkroking directory`에서 파일들을 작업하고 있다면 `add`명령어를 통해 히스토리에 저장하고 싶은 파일들을 `staging area`로 이동시킨다. 원하는 작업이 마무리 되어 `.git directory` 히스토리로 저장하고 싶다면 `commit`명령어를 통해 `staging area`의 파일들을 하나의 히스토리로 저장시킨다.  
만약 저장시켜놓은 버전으로 돌아가고 싶다면 `checkout` 명령어를 이용하여 복구가 가능하다.
`.git directory`는 현재 Git이 설치된 컴퓨터에만 저장되기 때문에 결국 컴퓨터에 문제가 생긴다면 옛날에 파일로 보관하던 때의 단점을 해결할 수 없다. 그렇기 때문에 `Github`같은 Git 저장소를 이용하여 `.git directory`를 저장해준다. `.git directory` 에서 `Github`로 업로드 해주는 명령어는 `push`이다. 반대로 다운로드 받는것은 `pull`명령어를 사용한다.  
`wkroking directory`의 경우 2가지로 나눌 수 있는데 `untracked`와 `tracked`이다. `tracked`는 Git이 관리하고 있는 파일들을 의미하고 `untracked` 관리하지 않는 파일을 의미한다. `tracked`의 경우 또 `unmodified`와 `modified`로 나뉘는데 수정된 파일과 수정되지 않는 파일을 의마한다. 만약 `wkroking directory`에서 `staging area`로 파일을 추가하려고 한다면 `unmodified`상태는 수정된것이 없으므로 불가능하다.