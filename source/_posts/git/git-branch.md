---
title: git 브런치 생성, 푸쉬
date: 2019-05-02 12:01:24
tags: git
categories: git
---
#### 1. 브랜치 목록 보기
```bash
$ git branch
```

#### 2. 브랜치 생성
```bash
$ git branch "브랜치이름"
```

#### 3. 브랜치 전환
```bash
$ git checkout "브랜치 이름"
# 새로 생성후
$ git checkout -b "브랜치 이름"
```

#### 4. 브랜치 전환 후 push
```bash
#origin의 경우 git에서 clone할 경우 자동생성되는 이름
$ git push origin "브랜치 이름"
```

#### 5. git 정보 확인하기
```bash
$ git remote show origin
```