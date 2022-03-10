---
layout: post
title: 'Atom으로 Git 관리하기'
category : [Useful]
tag: [Git]
---

Atom(아톰)은 Github(깃허브)에서 개발한 자유-오픈 소스 형태의 문서 및 소스 코드 편집기이다. 그래서 Git과의 연동이 꽤 편리하다. Sublime Text 등 다른 텍스트 에디터도 연동을 지원하지만, 아톰의 UI가 마음에 들어서 사용하기로 결정했다.
<!-- more -->

# Git과 연동하기
아톰을 실행하고 `cmd+,`(윈도우는 `ctrl+,`)를 누르면 나오는 `Settings-Install`에서 여러 플러그인을 설치할 수 있다. Git과 연동하기 위해서 다음의 플러그인을 설치해주자.

1.	git-plus
2.	git-clone

## git-plus
git-plus 패키지는 터미널 없이 git 명령어를 수행할 수 있도록 해주는 것인데, 반드시 설치 후에 git-plus의 설정으로 들어가서 git이 설치되어있는 경로를 지정해야 한다. 맥의 경우 터미널에서 다음과 같이 확인할 수 있다.

```terminal
$ which git
> /usr/local/bin/git
```

push하려는 파일을 작업하고 나서 `cmd+shift+h`를 누르면 git 콘솔 창을 열 수 있다. 여기서 add, commit, push를 할 수 있고 `Add All, And Commit and Push`로 한꺼번에 처리할 수 있다. Commit message 입력 후 저장하면 된다.


## git-clone
아쉽게도 git-plus패키지는 remote repository로부터 clone하는 것을 지원하지 않는다. 그래서 clone하고 싶다면 별도의 git-clone 플러그인을 설치해야 한다.

git-clone의 설정에서 파일을 저장할 Target Directory를 지정해준 다음 `cmd+shift+p`를 통해 주소를 입력하여 clone하면 끝. 주의할 점은 `Git Clone : Clone`을 실행해야 Target Directory로 저장된다.(`Github : Clone`은 뭘까...)

문득 `git clone`과 `git remote add`의 차이가 궁금해져서 알아보았다. 전자는 파일을 받아옴으로써 repository를 생성하는 것이고 없는 디렉토리를 지정해도 알아서 생성한다. 후자는 단순히 원격 저장소와 연결만 하는 것이어서 `pull`해서 파일을 가져와야 repository가 생성되며 존재하는 디렉토리에만 연결할 수 있다.


# Atom Theme
플러그인 외에도 여러가지 테마를 다운받아 적용시킬 수 있다. `Settings-Install`에서 Packages 옆의 Themes를 선택하고 검색하면 된다. 개인적으로 마음에 드는 테마를 추천한다. (사실 기본으로 제공되는 테마들도 상당히 깔끔하다.)

*	UI(메뉴 및 상단바)

	1.	Nord Atom UI(사용중)
	2.	Atom Material UI
	3.	Atom Visual Studio UI
	4.	Native UI

*	Syntax(편집창 및 텍스트 하이라이트)

	1.	Seti Syntax
	2.	Monokai Syntax
	3.	Styri Syntax


# 추가사항
마크다운 포맷으로 글을 작성할 때 유용한 플러그인을 소개한다.

1.	markdown-preview-enhanced : 미리보기 기능 제공한다.
2.	markdown-format : 저장하면 틀린 마크다운 포맷을 교정해준다.
3.	markdown-folding : 헤더를 접었다 폈다할 수 있다.

[gomugom님의 블로그](https://gomugom.github.io/atom-packages/)에서 다른 유용한 플러그인을 확인해보기 바람.
