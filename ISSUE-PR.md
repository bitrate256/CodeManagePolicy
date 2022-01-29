# Issue, PR 작성 방법

* __Commit Message 제목 끝에는 마침표(.) 달지 맙시다.__
* Commit 여러 개가 Issue 1건에 포함될 수도 있으며, Commit 1개가 PR 1건이 될 수도 있고, Issue 여러 개가 PR 1건이 될 수도 있습니다.   
  어찌됐건 __PR이 가장 높은 단위입니다.__   

## Issue 생성 or 확인
github repository 내 코드 탭 우측 Issue 탭 진입하여 Issue 작성후 Issue번호 확인, 혹은 Issue 리스트중 필요한 Issue번호 확인.   
ex) Issue이름 __#번호__   

## Commit 작성시 Issue 포함
Commit Message 제목 끝에 Issue번호 추가하여 작성.   
이후로도 이슈 해당 커밋 작성시 계속 Commit Message 제목 첫글자에 __#번호__ 부여.   
ex) __#번호__ 커밋메세지제목   

## Commit 과 함께 Issue를 close 하기
PR 없이 Commit과 함께 Issue를 닫아야 할 수도 있습니다. Commit Message 작성시 아래 키워드를 사용하게되면 이슈를 같이 Close 할 수 있어 굳이 이슈에 들어가 Close 상태로 전환하지 않아도 됩니다.   
ex) __키워드__ __#번호__ 커밋메세지제목   
```markdown
* close
* closes
* closed
* fix
* fixes
* fixed
* resolve
* resolves
* resolved
```
첨언하자면 각 키워드마다 기능에 차이는 전혀 없고, 이슈가 닫히는 것은 같습니다. 문법이나 맥락에 맞게 사용하면 됩니다. 다만,
* close 계열은 일반 개발 Issue
* fix 계열은 버그 픽스나 핫 픽스 Issue
* resolve 계열은 문의나 요청 사항에 대응한 Issue
에 사용하면 적당하다는 관례는 있습니다. 예문은 다음과 같습니다.   
```
# 제목에 이슈 한 개 닫기를 적용한 사례
Close #31 - refactoring wrap-up
* This is wrap-up of refactoring main code.
* main.c
  * removed old comments
  * fixed rest indentations
  * method extraction at line no. 35

# 본문에 이슈 여러 개 닫기를 적용한 사례
Update policy 16/04/02
* This closes #128 - cab policy, closes #129 - new hostname, and fixes #78 - bug on logging.
* cablist.txt: changed ACL due to policy update delivered via email on 16/04/02, @mr.parkyou
* hostname.properties: cab hostname is updated
* BeautifulDeveloper.java: logging problem on line no. 78 is fixed. The `if` statement is never happening. This deletes the `if` block.
```
이렇게 Commit을 작성하여 Push하면, Push한 Branch에 따라 Issue가 자동으로 닫힙니다. 예를 들어 Github 저장소의 default Branch를 main로 설정해뒀을 경우, main Branch에 Commit 후 Push하면 즉시 해당 번호의 Issue가 닫힙니다. develop Branch에 푸시했다면, Issue는 닫히지 않고 있다가 나중에 develop -> main Merge가 되었을 때 알아서 닫힙니다.

## PR 순서는?
상황 따라 다르겠지만 해당 Issue들 몇가지를 묶어서 PR 까지 이어져야 한다면, 일련의 Issue 작업(코딩) 종료 후 제목과 내용에 Issue 번호를 달아 PullRequest 요청합니다. __최종적으로 Merge 되면 Issue가 닫히게 됩니다.__   

## 요약
__Issue에 Commit 등록하기__   
Commit Message 제목에 이슈 번호 부여.
```
#2 - ~ 기능을 추가하였습니다
```
__Issue에 Commit/PR 자동 등록 및 이슈 닫기__   
Commit Message : 제목에 이슈 번호 + 키워드 부여. 수정된 요소 여러개일 때는 본문에 번호 부여.   
Pull Request : 본문에 PR에 포함되는 Issue 번호 + 키워드ed 부여.   
1. close : 일반적인 개발요소 완료시
2. fix : BugFix, 혹은 HotFix Issue
3. resolve : 문의나 요청 사항에 대응한 Issue
```
➨ Commit Message 제목
제목 : fix #2 - ~버그를 수정하였습니다
본문 : 수정내역은 ~입니다. CodeReview 진행 완료했습니다.

➨ Pull Request
제목 : 12.22 수요일 수정사항
본문 :
1. fixed #1 ~사항이 수정되었습니다.
2. resolved #5 고객사의 ~요청사항이 반영되었습니다.
3. closed #2 Issue 개발 마무리 되어 Issue가 닫힙니다.
```

# 참고자료 출처
### 이슈발행과 풀리퀘스트
https://m.blog.naver.com/demonic3540/221813167477   

### 좋은 커밋메세지란?
https://meetup.toast.com/posts/106   
