# CodeManagePolicy README
코드관리정책 공지용 Repository 입니다. 모든 개발 관련 전달 및 정책은 이곳에 게시합니다.

## 개발용 에디터(이클립스, 인텔리J 등)
1. 모두 사용 가능합니다만, 현 시점부터는 생산성을 위해 인텔리J로 통일하겠습니다.
2. 다음과 같은 에디터의 제외해야 하는 설정파일이 정의되어 있으니 불필요한 파일이 commit 되는 일은 없습니다만, 혹시 불필요한 파일이 commit 리스트에 포함되었다면 따로 말씀 부탁드립니다.
* STS, Eclipse
* IntelliJ 
3. 최초 코딩 전에 반드시 사용하시는 에디터의 __인코딩을 UTF-8로 변경__ 하십시오.

## 메인 API 개발 환경
* 빌드 도구 : maven
* 자바버전 : 1.8
* DB : mysql 5.7.15
* 톰캣 : 9
* 자동 병합+빌드 체계 : 리눅스+젠킨스 기반으로 개발중

## Project 명명 규칙
프로젝트 컨셉을 그대로 사용하여도 무방하나, 특정 기술의 명시가 필요하다면 프로젝트 이름을 __RESTApi__ 라고 가정할 때, __프로젝트이름Api-SpringLegacy__ 등으로 생성하십시오. 이하는 예시 입니다.   
예시 :   
POSApi(스프링레거시) ➙ POSApi-SpringLegacy   
POSApi(스프링부트) ➙ POSApi-SpringBoot   

## Project 내 클래스, 변수 명명 규칙
* 카멜케이스 명명법 사용 : 첫글자 소문자, 이후 연결단어들의 첫글자를 대문자
ex) camelCaseParameter
* 이하 구체적인 명명법 :   
* * *
### class (클래스)   
대문자로 시작하고, 명사를 사용합니다.   
```java
class Thread;
class Raster;
class ImageSprite;
```
### interface (인터페이스)   
대문자로 시작하고, 형용사를 사용합니다.   
```java
interface Runnable;
interface RasterDelegate;
interface Storing;
```
### method (함수)   
소문자로 시작하고, 동사를 사용합니다.   
```java
add();
runFast();
getBackground();
```
### variable (변수)   
소문자로 시작합니다.   
```java
int i;
char c;
float myWidth;
String phoneNumber;
```
### Package (패키지)   
소문자로 시작합니다.   
```java
com.sun.eng
com.apple.quicktime.v2
edu.cmu.cs.bovik.cheese
```
constant (상수)  
### 대문자로 시작합니다.
```java
static final int MAX_WIDTH = 999;
static final int GET_THE_CPU = 1;
```
* * *

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
향후 실제 개발 진행시 Push/Pull 꼬이지 않도록 절차를 정해두고자 합니다.   

* 개발/이슈branch 생성 필요사항은 다음과 같습니다.
1. 원격근무시(자가격리, 혹은 원격근무 하는 외주인력 등)
   해당 상황은 대면 회의가 아니고 착오가 발생할 확률이 높기 때문에 github의 코드리뷰 화면을 보고 병합여부를 판단해야 합니다.
2. 기타 위험도가 높다고 판단된 개발사항

* 병합 방안은 다음과 같습니다만, 기본적으로 2번 제안으로 원본코드 보존하면서 진행하겠습니다.
__정말 특별한 경우 제외하고 메인branch에 직접 commit 하는 일은 없도록 하겠습니다.__   

## 긴급진행시
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
