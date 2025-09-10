## 🧐 상황별 Git 명령어 정리

**git 최초 연동 후 작업할 때**
- [최초 연동시](#최초-연동시)
- [최초 git 푸시](#로컬에서-원격으로)

**git 클론 후 작업할 때**
- [git 클론후 작업시작](#원격에서-로컬로)
- [작업 해제](#연결-해제시)

**항상 사용하는**
- [추가/커밋/푸시](#작업하고-변경된-사항-커밋할-때)

**브랜치랑 관련된**
- [브랜치 확인](#브랜치-확인-방법)
- [브랜치 생성](#새로운-브랜치-생성할-때)
- [브랜치 삭제](#브랜치-삭제할-때)
- [브랜치 복구](#삭제한-브랜치-복구할-때)

**기타 작업**
- [경고 메세지](#경고-메세지)
- [작업 복구](#시점-되돌릴-때)
- [작업 병합](#깃허브에서-pull-request-후-병합할-때)


## **git 최초 연동 후 작업할 때**
#### 최초 연동시

```bash
$ git config --global user.name "ID"
$ git config --global user.email "mail 계정"
$ git config --list
```

#### 로컬에서 원격으로
- 로컬에서 작업하다 git으로 최초 올릴 때

```bash
$ git init
$ git add .
$ git commit -m "message(필수)"
$ git branch -m main
$ git remote add origin 원격-저장소-url
$ git push -u origin main
```

## **git 클론 후 작업할 때**
#### 원격에서 로컬로
- git에 프로젝트 있는 거 가져와서 작업할 때

```bash
$ git clone 원격-저장소-url               # clone은 로컬 저장소로 폴더만 복제해온것임
$ cd 복제한폴더명                         # 경로 이동(클론해오면 폴더 생김)

# $ git init                            # 내가 원하는 폴더에서 시작하고 싶으면
# $ git remote -v                       # 원격 저장소와 연결 되어 있는지 확인

$ git remote add origin 원격-저장소-url   # 연결 안되어 있으면 수행
$ git branch -m main
$ git pull origin main

$ git push -u origin main               # 첫 push시 위 명령어 수행
```

#### 연결 해제시

```bash
$ git remote rm origin
```

## **항상 사용하는**
#### 작업하고 변경된 사항 커밋할 때
- 최초 push 이후

```bash
$ git add .
$ git commit -m "메세지(필수)"
$ git push
```

## **브랜치랑 관련된**
#### 새로운 브랜치 생성할 때

```bash
$ git checkout -b 브랜치명   
$ git push --set-upstream origin 브랜치명
$ git push origin 브랜치명
```

#### 브랜치 확인 방법

```bash
$ git branch        # 현재 위치한 브랜치 확인
$ git branch -a     # 브랜치 목록 확인
$ git branch -r     # 원격 브랜치 목록 확인
```

#### 브랜치 삭제할 때

```bash
$ git branch -d 브랜치명        # 로컬 브랜치 삭제
$ git push origin -d 브랜치명   # 원격 브랜치 삭제
```

#### 삭제한 브랜치 복구할 때

```bash
$ git reflog                            # 삭제한 브랜치와 커밋 해시값 확인
$ git checkout -b 삭제한브랜치명 해시값
```

## **기타 작업**
#### 시점 되돌릴 때
- 커밋 후 작업 되돌리고 싶을 때

```bash
$ git revert hash값     # hash값: 되돌리고 싶은 시점 값
```

#### 경고 메세지 
- 줄바꿈(LF vs CRLF) 문제로 인한 Git 경고 메세지 나올 때

<p align="left">
  <img src="./img/lf_warning_msg.png" width="300"/>
</p>

```bash
$ git config --global core.autocrlf true
```

#### 깃허브에서 pull request 후 병합할 때
[충동발생시](https://chaeyoung2.tistory.com/61)

#### 이슈 사용법
[이슈사용법](https://velog.io/@dohaeng0/GitHub-Project-Issue-%ED%99%9C%EC%9A%A9)