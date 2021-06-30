---
layout: post
title: 'Git Workflow 정리'
category : [Useful]
tag: [Git]
---

VS code의 편의성 때문에 Atom을 더 이상 사용하지 않기로 했다. 에디터 내에서 터미널 접근이 가능해서 편리하다. 일 년 넘게 방치하다가 오랜만에 관리하려니까 기억이 나지 않아 고생했다. 또 방치할 수도 있으니 기록해두자.


# Workflow
Git 작업 흐름은 대략 다음과 같다.

> 저장소(repository) clone or pull -> 코드 생성 및 수정 -> 변경사항 staging -> commit -> push


## clone or pull
작업하고자 하는 git 저장소를 로컬에 가져오는 과정이다. 처음 접근하는 경우, 다음의 명령어로 저장소의 파일을 로컬로 가져오면 된다.

```terminal
git clone URL
```

이미 이전에 clone 했다면 다음의 명령어로 최신화만 시켜주면 된다. 참고로 clone 되어 있는 폴더를 살펴보면 .git 파일이 있다. 그래서 매번 clone 할 필요가 없다.

```terminal
git pull URL
```

주의할 점은, pull 하지 않고 변경사항을 push하면 버젼이 맞지 않아 에러가 발생한다. 그러니 꼭 pull 부터 하자.


## 코드 생성 및 수정
새로운 코드를 생성 혹은 수정하고 저장하는 단계이다. 별다른 명령어가 필요하지 않다. Git workflow에서는 가장 짧겠지만, 실제로는 가장 오래 걸리는 작업...


## staging
앞 단계에서 저장했다고 해서 저장소에 반영되지는 않는다. 로컬에서 작업한 것이기 때문. 그래서 변경사항을 staging 영역에 추가해 주어야 한다. 명령어는 다음과 같다.

1. 현재 디렉토리에 있는 모든 업데이트된 파일을 stage할 경우
```terminal
git add .
```

2. 수정된 파일만을 stage할 경우
```terminal
git add -a
```

3. add 내역 확인
```terminal
git status
```

## commit
staging 영역의 내용을 저장소에 commit 하는 단계이다. message는 되도록이면 자세하게 적는 습관을 가지자.

```terminal
git commit -m "commit message"
```

## push
마지막으로 원격 저장소로 보내기 위해 push 해야 한다. 우선 원격 저장소를 연결하자. 여기서 origin은 원격 저장소의 이름인데, 다른 이름으로 해도 무방하다.

```terminal
git remote add origin URL
```

그 다음 master 브랜치로 push 하면 Git 저장소에 반영된다.

```terminal
git push origin master
```


# VS code
VS code에서는 staging과 commit을 한 번에 할 수 있다. 파일을 저장하고 체크 버튼만 누르면 끝이다. 그 다음 터미널을 열어서 push 하면 된다.