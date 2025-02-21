---
tags:
  - manual
---
[[Git]]을 이용한 협업방법을 설명하는 메뉴얼이다.
## 환경설정
>[!warning]
>Github 계정 생성, Git 다운로드, Git 초기설정을 사전에 해야함
### 1. 원격 저장소 설정
#### 프로젝트 원격 저장소 Fork
- 프로젝트 원격 저장소를 [[Fork]] 해서 자신의 원격 저장소로 복제

>[!note]
>이제부터 프로젝트 원격 저장소를 복제해 만든 원격 저장소를 Fork한 원격 저장소라고 지칭하겠다.

### 2. 로컬 저장소 설정
#### 프로젝트 폴더에서 터미널 실행
- 파일 탐색기에서 프로젝트 디렉토리를 위치시킬 디렉토리로 이동
- 비어있는 프로젝트 디렉토리 생성
- 프로젝트 디렉토리로 이동
- 오른쪽 클릭 후 "터미널에서 열기"클릭

>[!note]
>앞으로 언급되는 모든 터미널 명령어는 프로젝트 디렉토리에서 실행된다.
#### 로컬 저장소 생성
```bash
git init
```
#### 로컬 저장소와 Fork한 원격 저장소 연결
```bash
git remote add origin <Fork한 원격 저장소 URL>
```
- Fork한 원격 저장소의 Github 페이지에서 URL 확인
- Fork한 원격 저장소를 `origin`이라는 이름으로 접근 가능하게 해줌
#### 로컬 저장소와 프로젝트 원격 저장소 연결
```bash
git remote add upstream <프로젝트 원격 저장소 URL>
```
- 프로젝트 원격 저장소의 Github 페이지에서 URL 확인
- 프로젝트 원격 저장소를 `upstream`이라는 이름으로 접근 가능하게 해줌
## 작업 사이클
### 1. 브랜치 생성
#### 프로젝트 원격 저장소 pull
```bash
git pull upstream main
```
#### 작업 브랜치 생성
```bash
git branch <브랜치 이름>
```
- 브랜치 이름은 `feature/기능요약` 형식을 추천함
#### 작업할 브랜치로 이동
```bash
git switch <브랜치 이름>
```
- 브랜치 이름은 작업 브랜치의 이름을 나타냄
### 2. 변경사항 기록
#### 작업 디렉토리 변경사항 확인
```bash
git status
```
#### 변경사항을 기록할 파일 명시
Git은 작업 디렉토리에서 변경사항이 존재하는 파일들 중에서 우리가 선택한 파일들만 로컬 저장소에 변경사항을 기록한다.
```bash
git add <파일이름1> <파일이름2> ...
```
- 변경사항을 기록할 파일들을 스태이징 영역에 추가함
- 스태이징: 변경사항이 존재하는 특정 파일들을 스태이징 영역에 올리는 과정
- 스태이징 영역: 로컬 저장소의 다음 기록 대상이 되는 파일들
#### 로컬 저장소에 변경사항 기록
```bash
git commit -m "메세지"
```
- 스태이징 영역에 속한 파일들의 변경사항을 로컬 저장소에 기록함

>[!info]
>Git은 특정 Commit으로 프로젝트 상태를 되돌릴 수 있는 기능을 지원하기 때문에 commit은 자주 해줄수록 좋다.
### 3. Pull Request 생성
Fork한 원격 저장소에 기록된 변경사항을 프로젝트 원격 저장소에 반영하고 싶다면 pull request를 생성해야 한다.
#### Fork한 원격 저장소에 변경사항 기록
```bash
git push origin <브랜치 이름>
```
- 로컬 저장소에 기록된 변경사항을 원격 저장소에 기록함
- 브랜치 이름은 작업 브랜치의 이름을 나타냄
#### 프로젝트 원격 저장소에 pull request
- Fork한 원격 저장소 Github 페이지에 접속
- 활성화된 `Compare & pull request` 버튼 클릭
- 프로젝트 원격 저장소 관리자가 pull request 수락
### 4. 브랜치 정리
#### main 브랜치로 이동
```bash
git switch main
```
#### 필요 없어진 작업 브랜치 삭제
```bash
git branch -d <브랜치 이름>
```
- 브랜치 이름은 작업 브랜치의 이름을 나타냄