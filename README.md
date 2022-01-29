# CodeManagePolicy README
코드관리정책 공지용 Repository 입니다. 모든 개발 관련 전달 및 정책은 이곳에 게시합니다.

## 개발용 에디터(이클립스, 인텔리J 등)
1. 기본 에디터는 배포해드린 STS3 입니다. 필요할 수도 있으니 STS4도 설치해두십시오.
2. 취향 따라서 인텔리J 등의 에디터를 사용하실 수도 있으나, 에디터 설정파일등 차이로 불필요한 파일이 Git에 포함될 수도 있습니다. 현재는 다음과 같은 에디터의 파일이 예외정책에 포함되어 있으니 편하신대로 사용하시면 됩니다.
* STS, Eclipse
* IntelliJ 
3. 최초 코딩 전에 반드시 사용하시는 에디터의 __인코딩을 UTF-8로 변경__ 하십시오.

## 메인 API 개발
* __BitOpenAPI__ repository에 메인 API 개발중입니다. 해당 프로젝트가 앞으로 있을 모든 프로젝트의 기본 API 입니다.   

## Project 명명 규칙
프로젝트 이름은 __RESTApi-SpringLegacy__ repository 안에 __프로젝트이름ApiSpringLegacy__ 으로 생성하십시오. 차후 있을 SpringBoot 전환 작업과 구분하기 위함입니다. 이하는 예시 입니다.   
예시 :   
NameApi(스프링레거시) ➙ NameApiSpringLegacy   
NameApi(스프링부트) ➙ NameApiSpringBoot   

## Repository 명명 규칙
* '프로젝트이름' 만 사용하도록 하겠습니다.   
* Repository 이름에 괄호를 사용하지 못하기 때문에 괄호를 사용하면 자동으로 -로 대치됩니다.   
예: [jsp]예제프로젝트 ➙ -jsp-예제프로젝트   
해당 Repository의 주사용 언어는 이름 아래에 표시되며, 목록 윗줄을 보면 Repository타입, 언어 등으로 분류가 가능하니 처음에 처음에 의도했던 분류법 자체에는 문제가 없습니다. 더 좋은 명명 방법이 있다면 제안 주시기 바랍니다.   

## 팀 공식 Git 보안 정책
1. 보안 사항은 __Two Factor(2FA,이중인증)__ 로그인 과정으로 결정되었습니다.
   현재 디렉터리에 마크다운 문서 새로 생성하여 설명드리겠습니다.
   이중인증 사용시 github웹 뿐만 아니라 코드 업로드에도 __인증과정(AccessToken, 혹은 sha256 키)__ 이 추가됩니다.
   github계정의 비밀번호만 이용해서 로그인을 할 수 없기 때문 입니다.
   한번만 등록해두면 이후 개발에 방해되지 않으니 긴 학습이 필요하지는 않습니다.
   잠시 시간 내셔서 주의깊게 읽어보시고 __AccessToken__, 혹은 __sha256__ key중 마음에 드는 것을 등록해주시기 바랍니다.
2. 차후 자동빌드 등의 요구사항에 따라 GitHub 계정을 업그레이드 하거나, 사내 형상관리 서버 등이 필요할 수도 있습니다. 적어도 프로젝트 기간 동안은 GitHub를 계속 사용하겠습니다.

## 추적제외 항목(.gitignore)
git 에서는 추적 제외 항목을 지정할수 있습니다. 일반적으로 jar, .class, war, 이클립스 설정파일등 코딩 자체와 상관 없고 빌드시 방해될 파일을 추적 제외하지만, 프로젝트 별로 요구사항이 다를 수도 있습니다.   
__GitHub에 push 하면 해당 repository에 전부 적용되므로, 변동시이 필요할 때 반드시 모든 인원에게 상황공유하여 결정한 뒤 반영해야 합니다.__   
__자세한 사용법은 GitManual.md를 참고하십시오.__

## 코드 병합 방안
향후 실제 개발 진행시 Push/Pull 꼬이지 않도록 절차를 정해두고자 합니다. 회의 결과, 현재 프로젝트는 개발branch 생성 없이 메인branch에 직접 commit/push 하기로 했습니다. 이후 필요에 따라 1번 제안으로 개발/이슈branch 생성하여 PullRequest 진행하겠습니다.   

* 개발/이슈branch 생성 필요사항은 다음과 같습니다.
1. 원격근무시(자가격리, 혹은 원격근무 하는 외주인력 등)
   해당 상황은 대면 회의가 아니고 착오가 발생할 확률이 높기 때문에 github의 코드리뷰 화면을 보고 병합여부를 판단해야 합니다.
2. 기타 위험도가 높다고 판단된 개발사항

* 프로젝트 종료 후 병합 방안은 다음과 같습니다.
프로젝트 종료 후에 API가 안정화 되면 2번 제안으로 원본코드 보존하면서 진행하겠습니다.
__현재 프로젝트 종료 후 안정화 단계로 진입하면, 정말 특별한 경우 제외하고 메인branch에 직접 commit 하는 일은 없도록 하겠습니다.__   

## 현행 결정사항 (branch 생성 안함)
구조 : 팀계정 Repository 메인branch -(clone)→ 로컬 Repository의 메인branch
1. Clone
   - 팀계정 Repository에서 로컬 Repository로 clone,remote 설정
2. 개발/수정사항 추가(코딩)
3. 개발자간 대면 검토
4. 통과시 팀계정 Repository 메인branch로 commit/push
5. 이후 추가개발시 반복
   로컬 Reposirory의 메인branch 에서 _fetch+merge 혹은 pull 진행해 테스트_ → 요구사항 개발(코딩) → 개발자간 대면 검토 → 팀계정 Repository로 commit/push
* fetch는 github에 있는 코드를 받기만 하고 merge(병합)되지 않습니다. 이후 개발자가 수동으로 merge해야 병합됩니다.
  따라서 fetch하여 테스트 진행한 후 이상 없을 때 merge 하고 추가개발 진행하는 것이 안전합니다.
* 위험요소가 낮고 신속한 작업이 필요하다면 pull하여 바로 작업 진입하시기 바랍니다.

## 제안 1 (Clone한 뒤 개발/이슈 branch 생성)
구조 : 팀계정 Repository 메인branch -(clone)→ 로컬 Repository의 메인branch → 개발/이슈branch
1. Clone
   - 팀계정 Repository에서 로컬 Repository로 clone,remote 설정
2. 개발/이슈branch 생성
3. 개발/수정사항 추가(코딩)
4. Merge PullRequest 생성
5. 검토
6. Confirm Merge 후 개발/이슈branch 삭제
7. 이후 추가개발시 반복
   로컬 Reposiroty에서 _fetch+merge 혹은 pull 진행해 테스트_ → 개발/이슈branch생성하여 작업 → 팀계정 Repository로 PullRequest

## 제안 2 (Fork-Clone한 뒤 개발/이슈branch 생성, 원본코드를 2중 보호)
구조 : 팀계정 Repository의 메인branch -(Fork)→ 개인계정 Repository -(clone)→ 로컬 Repository의 메인branch → 개발/이슈branch
1. Fork
   - 팀계정 Repository에서 개인계정 Repository로 Fork
2. 개인계정 Repository에서 로컬 Repository로 clone  
   - clone,remote 설정
3. 로컬 Repository의 메인branch 에서 개발/이슈branch 생성하여 추가/수정개발
   - branch 생성 및 코딩
4. 작업 후 로컬 Repository에 commit하고 개인계정 Repository(origin)로 push
   - add → commit → push
   - 주의사항 : push 진행시 branch 이름 명시할 것
5. 개인계정 Repository에서 팀계정 Repository쪽으로 Compare&MergePullRequest 생성
6. 검토 후 팀계정 Repository에 최종병합
7. 로컬 Repository와 팀계정 Repository 동기화 후 개발/이슈branch 삭제
   - 로컬 Repository에서 pull remote → 개발/이슈branch 삭제
8. 이후 추가개발시 반복
   로컬 Reposiroty에서 fetch 하여 테스트및 merge → 개발/이슈branch 생성하여 작업 → 개인계정 Repository로 push   
   → 개인계정 Repository에서 팀 Repository로 Compare&MergePullRequest(병합)
* 안정화 단계 에서는 가급적 임의 pull 혹은 메인branch push는 지양해야 바람직합니다.

## 기타 협의 사항
1. 설명드린바 같이 현재 무료 플랜 이용중이기 때문에 몇가지 기능제약이 있을 수 있지만,   
   코드 형상관리 목적으로는 큰 무리가 없을 것으로 생각됩니다. 건의사항은 언제든지 문의 주시기 바랍니다.

## 참고자료 출처
_PullReqauest(이하 PR)_
git 초보를 위한 PR 가이드   
https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/   
오픈소스에 PR 기여하기   
https://chanhuiseok.github.io/posts/git-3/   
PR 관리 방법   
https://medium.com/prnd/%ED%97%A4%EC%9D%B4%EB%94%9C%EB%9F%AC-%EA%B0%9C%EB%B0%9C%ED%8C%80-%EB%AA%A8%EB%91%90%EA%B0%80-%ED%96%89%EB%B3%B5%ED%95%9C-%EA%B0%9C%EB%B0%9C-pr%EA%B4%80%EB%A6%AC-%EB%B0%A9%EB%B2%95-7%EA%B0%80%EC%A7%80-1d4cd5d091f0   
PR 리뷰&테스트 강제하여 브랜치 보호(유료계정 기능. 현재 사용 불가)   
https://hbase.tistory.com/215   
커밋 취소, 되돌리기, 덮어쓰기 명령어 가이드   
https://www.lainyzine.com/ko/article/git-reset-and-git-revert-and-git-commit-amend/   

## 이중인증 참고 링크
2FA 인증 튜토리얼   
https://jojoldu.tistory.com/449   
ssh키 생성 및 등록   
https://velog.io/@igotoo/github-%EC%A0%91%EC%86%8D%EC%9D%84-https%EC%97%90%EC%84%9C-ssh-%EC%A0%91%EC%86%8D%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B8%B0   
토큰 생성 및 등록   
https://curryyou.tistory.com/344
