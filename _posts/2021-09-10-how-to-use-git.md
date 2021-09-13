---
layout: post
title: 'How to use Git'
category : [Useful]
tag: [Git]
---

VS code의 편의성 때문에 Atom을 더 이상 사용하지 않기로 했다. 에디터 내에서 터미널 접근이 가능해서 편리하다. 일 년 넘게 방치하다가 오랜만에 관리하려니까 기억이 나지 않아 고생했다. 또 방치할 수도 있으니 기록해두자.


# Workflow
Git 작업 흐름은 대략 다음과 같다. Git은 주로 협업에서 사용되므로 branch 관리도 굉장히 중요하지만 일단은 기본적인 흐름만 알아보도록 하자.

> 저장소(repository) `clone`or `pull` -> 코드 생성 및 수정 -> 변경사항 `staging` -> `commit` -> `push`

로컬 컴퓨터에서 git을 사용하려면 먼저 git을 설치해야 한다. Mac OS의 경우, 터미널에서 `git status`만 입력해도 git이 설치가 안 되어 있다면 알아서 git을 설치한다. 그리고 여러 저장소(repository)에 `commit`하는 사용자가 누구인지를 알려줘야 하기 때문에 사용자 정보를 설정해야 한다. 해당 명령어는 아래와 같다. 수정하기 어려우니까 잘 입력하자.

```
$ git config --global user.name yourname
$ git config --global user.email your@email.com
```

간혹 `commit`을 했는데에도 본인의 contributions이 기록되지 않는다는 이야기를 듣는데, 이것은 위의 설정에서 입력한 이름과 이메일이 본인의 깃허브 계정과 맞지 않아서이다. 그럴 경우, 사용자 정보를 다시 설정하면 된다.

<p align="center">
  <img width="600" src="/public/img/contributions.png">
  <font size="2" color="#808080"> Github에서 볼 수 있는 contribution 차트 </font>
</p>




## clone or pull
작업하고자 하는 git 저장소를 로컬에 가져오는 과정이다. 처음 접근하는 경우, 다음의 명령어로 저장소의 파일을 로컬로 가져오면 된다. VS code를 사용한다면 `cmd`+`shift`+`p`로 팝업 창을 띄우고 `>Git: clone`을 통해 url을 입력하자.

```terminal
$ git clone URL
```

이미 이전에 `clone` 했다면 다음의 명령어로 업데이트만 하면 된다. 참고로 `clone` 되어 있는 폴더를 살펴보면 .git 파일이 숨어 있다. 그래서 매번 `clone` 할 필요가 없다.

```terminal
$ git pull origin master
```

주의할 점은 `pull` 하지 않고 변경사항을 `push`하면 버전이 맞지 않아 에러가 발생한다. 그러니 꼭 `pull` 부터 하자. 참고로 `pull`=`fetch`+`merge`이다. `fetch`는 repository의 변경사항을 가져오기만 하는 것이기 때문에 `merge`하기 전까지는 로컬에 아무런 변화가 없다. 여기까지 완료되었다면 저장소의 파일을 가지고 로컬에서 작업하면 된다. 별다른 명령어가 필요하지 않다.


## staging
로컬에서 발생한 수정사항이 자동으로 저장소에 반영되지 않는다. 그래서 변경사항을 `staging` 영역에 추가해 주어야 한다. 명령어는 다음과 같다.

1. 현재 디렉토리에 있는 모든 업데이트된 파일을 `stage`할 경우
```terminal
$ git add .
```

2. 수정된 파일만을 stage할 경우
```terminal
$ git add -a
```

3. add 내역 확인
```terminal
$ git status
```

## commit
`staging` 영역의 내용을 저장소에 `commit` 하는 단계이다. 커밋 내용은 되도록이면 자세하게 적는 습관을 가지는게 좋다.

```terminal
$ git commit -m "commit message"
```

## push
마지막으로 원격 저장소로 보내기 위해 `push` 해야 한다. 우선 원격 저장소를 연결하자. 여기서 origin은 원격 저장소의 이름인데, 다른 이름으로 해도 무방하다.

```terminal
$ git remote add origin URL
```

그 다음 `master` 브랜치로 `push` 하면 저장소에 반영된다. 간혹 `master`가 아닌 `main`인 경우도 있으니 확인 후 작업하자.

```terminal
$ git push origin master
```

Visual Studio, IntelliJ 등 많은 IDE들은 git과 연동하여 관리할 수 있는 기능들을 제공한다. 현재 사용 중인 VS code는 좌측의 세 번째 탭에서 `staging`과 `commit`을 한 번에 처리할 수 있다. 공란에 메시지를 입력하고 `cmd`+`enter`를 입력하거나 상단의 체크 버튼을 누르면 된다. 그 다음, 터미널(터미널은 `ctrl`+``` ` ```로 열 수 있다)로 `push`만 하면 돼서 작업이 한결 간편해졌다. 각자의 취향에 맞게 사용하면 될 듯 하다.

## branch
브랜치를 관리하는 내용도 담고 싶은데 양이 너무 많아서 아래에 참고할만한 좋은 글들의 링크를 달아두었다. 직접 사용하면서 익숙해지도록 하자. 한 가지 신기한 점을 발견했는데, 저장소를 로컬에 `clone`하고 작업을 하다가 다른 브랜치로(ex. `master` -> `develop`) 이동하면 로컬의 폴더에서도 알아서(?) 해당 브랜치의 파일만 보여준다. 파일이 삭제되는 것은 아닌 것 같고 어떤 방식인지 모르겠다.



# Further Reading

1. [Git 뉴비를 위한 기초 사용법 - 시작하기](https://evan-moon.github.io/2019/07/25/git-tutorial/)
2. [어떻게 깃을 사용하는지 빠르게 알아봅시다](https://github.com/KennethanCeyer/tutorial-git)