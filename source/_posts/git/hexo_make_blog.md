---
title: Hexo로 github blog 만들기
date: 2019-04-23 10:00:00
tags:
	- git
	- hexo
categories:
	- git
	- hexo
---
## [Hexo.io](http://hexo.io) - Hexo 공식 홈
<br>

#### 1. node 설치후 hexo-cli 설치
```bash
$ npm install hexo-cli -g
```
#### 2. Hexo 설치할 폴더
```bash
$ hexo init blog
```
#### 3. Hexo 설치한 폴더로 이동 후 node_module 설치
```bash
$ cd blog
$ npm install
```
#### 4. Hexo Server로 가동하면 localhost:4000으로 로컬 구동
```bash
$ hexo server
```
#### 5. github에서 {username}.github.io 라는 repository 생성 후 폴더 최상단 _config.yml 내용 입력
```bash
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/{username}/{username}.github.io
  branch: master
  message: [message]
```
#### 6. github 배포용 모듈 설치
```bash
$ npm install hexo-deployer-git --save
```
#### 7. git으로 deploy
```bash
$ hexo deploy
```