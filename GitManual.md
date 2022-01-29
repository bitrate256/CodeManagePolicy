# Git 메뉴얼

## clone / fork
__터미널에서 새 저장소 만들어서 PUSH하기__   
…or create a new repository on the command line
```bash
echo "# DIDApi" >> README.md
git init
git add README.md // README.md가 있어야 깃허브에서 인식합니다.
                  // README.md와 함께 프로젝트 파일들 전부 add 해도 정상 인식됩니다.
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/레포지토리 주소
git push -u origin main
```
__터미널에서 기존 저장소를 PUSH 하기__   
…or push an existing repository from the command line
```bash
git remote add origin https://github.com/레포지토리 주소
git branch -M main
git push -u origin main
```

## 저장소 관리
```bash
$ git init - 깃 초기화
$ git clone - 깃 복제
$ git remote add <원격저장소><저장소> - 원격 저장소 추가
## 로그 확인
$ git log
## 로그 확인 + branch가 어떤 commit을 가리키는지 + branch그래프
$ git log --decorate --graph
## diff(변경사항) 확인
$ git diff <커밋ID>
## commit 개별 확인 (커밋 변경내용+태그+날짜+커밋메세지등 모든 정보)
$ git show <커밋ID>
```

## remote(원격) repository 관리
```bash
## 현재 remote 연결되어 있는 원격 repository 확인
$ git remote -v
## remote 연결 제거
$ git remote remove <remote이름>
## remote 연결하기
## → origin으로 지정하세요. 앞으로도 repository uri는 origin 으로 지칭함.
$ git remote add <지정할 remote이름> <uri>
```

## 기초동작 1 (코드 작성 전)
코드 작성 전 fetch/merge 혹은 pull 받기
```bash
## Fetch 받기 → remote 저장소의 커밋을 전부 받기만 함(merge 진행하지 않음)
$ git fetch
$ git merge
## Pull 받기 → remote 저장소의 커밋을 전부 받아 merge 함
git pull
```

## 기초 동작 2 (코드 작성 후)
add-commit-push 과정
```bash
## 저장소에 결과물 추가
$ git add <파일명>
## 저장소에 결과물 일괄 추가
$ git add .
## add된 변경사항 커밋하기
$ git commit <저장소 URL 및 계정정보>
## 변경사항 push
$ git push
## main 브랜치 변경사항 push
## origin(원격저장소, 즉 깃허브주소)의 main(master)브랜치에 push
## -u 옵션 사용시 다음 명령어 부터는 git push 만 해도 자동으로 main브랜치로 push됨.
$ git push origin main
$ git push -u origin main
## 다른 브랜치 변경사항 push
## origin(원격저장소, 즉 깃허브주소)의 TaskBranch(브랜치이름)브랜치에 push
$ git push origin TaskBranch
```

## branch
```bash
## branch 목록 보기
$ git branch
## 원격 branch 목록 보기
$ git branch -r
## 모든 branch 목록 보기
$ git branch -a
## branch 생성
$ git branch <브랜치 이름>
## branch 전환(이동)
$ git checkout <브랜치 이름>
## branch 생성과 동시에 전환
$ git checkout -b <브랜치 이름>
## branch 합치기 (병합, merge)
$ git merge <브랜치 이름>
## branch 병합 취소
$ git merge --abort
## branch 선택 합치기
$ git cherry-pick <커밋 hash>
## branch 삭제
$ git branch -d <삭제할 브랜치 이름>
```

## 특정 파일or확장자 추적제외
git 에서는 추적 제외 항목을 정할수 있습니다. 디렉토리 최상단의 .gitignore에 파일명, 혹은 확장자를 추가하여 커밋하고 .gitignore 파일과 함께 push 하면 적용됩니다. 이미 있는 파일들도 일괄 적용하고 싶다면 아래 명령어를 참고하십시오.
```bash
## 1. .gitignore 파일에 해당 파일 추가.
##    .gitignore 파일이 없다면 생성하여 작업. (명령어는 vim에디터 파일 열기와 동일.)
$ vim .gitignore
## 2. 작성후 commit시 대상파일 삭제됨.
## 3. 목표 remote 로 push
```

## 추적제외 일괄적용
.gitignore에 파일 추가하여 저장한 후 절차 입니다.
```bash
$ git rm -r --cached .
$ git add .
$ git commit -m ".gitignore 일괄적용"
```

## conflict(충돌) 무시하고 강제 push/pull
1. 이대로 push 해도 문제 없는 것이 확인된 코드를 push 혹은 pull시 정상작동하지 않을 때, 충돌을 무시하고 진행함.
2. confilct 발생할 상황을 줄이고 되도록 사용하지 말것.
   → 반드시 작업 이전에 fetch/merge 혹은 pull 선행되어야 함.
   → confilict를 직접 해결하고 push 할 것.
3. 위험성이 높기 때문에 타 개발자와 논의 후 진행할 것.
```bash
## 강제 push
$ git push -u origin main --force
## 강제 push old 버전. 이전에 사용한 명령어 이지만 지금 사용 가능한지는 확실하지 않음.
## 다른 설명자료 읽을 때 참고만 할 것.
$ git push -u origin +main
## 강제 pull
## 1. remote 에서 fetch받은 후에
## 2. local에서 다시 reset hard 사용해 상태를 수정 전으로 되돌리고
## 3. 이후 pull 하면 remote에서 local로 정상적으로 다운로드받아짐
$ git fetch -all
$ git reset --hard origin/main
$ git pull origin main
```

## 태그
```bash
## 태그 확인
$ git tag
## 태그 붙이기 (light weight, 일반 태그. 특정 커밋을 가리킴)
$ git tag <태그이름>
## Annotated 태그 붙이기 (Annotated, 태그만든 개발자 정보+태그메세지 저장)
$ git tag -a <태그이름>
## Annotated 태그 붙이기 + 태그메세지 붙이기
$ git tag -a <태그이름> -m "태그메세지, ~버전입니다 등등"

## 이전 commit에 태그하기
$ git tag <커밋ID>
## 태그 변경
$ git tag
## 태그 삭제
$ git tag -d <커밋ID>
## 원격 저장소의 태그 삭제
$ git tag -d :<커밋ID>
## 태그 push 하기
git push origin <태그명>
## 태그 전부 push 하기
git push origin --tags
## 특정 태그 받기
$ git checkout <특정태그명>
```
