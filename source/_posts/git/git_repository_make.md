---
title: git repository 만든 후, 로컬에서 연동
date: 2019-04-23 09:00:00
tags: git
categories: git
---
#### 1. github에 블로그로 사용할 빈 repository 생성
#### 2. local 에 [git](https://git-scm.com/downloads) 다운로드 설치
#### 3. 작업 할 장소에 폴더를 만든후 그 폴더에서 git bash 열고 아래 명령어 실행
```bash
$ git clone https://github.com/{username}/{repositoryname}.git

$ git config --global user.name '{username}'
$ git config --global user.email {useremail}
$ git config user.name
$ git config user.email

$ git add .
$ git commit -m 'first commit message'
$ git push origin master
```