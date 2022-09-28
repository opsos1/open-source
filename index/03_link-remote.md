# **:link:깃허브 연동 및 원격 등록**
    서버 저장소를 생성했다면 로컬 저장소와 연결해야합니다.

## **로컬 저장소**
- ### **저장소를 연결하는 방식으로 두 가지가 있습니다.**<br>
    1. 새로운 로컬 저장소를 만들고, 이 저장소에 원격 저장소를 연결<br>
    2. 기존 로컬 저장소를 원격 저장소에 연결

- ### **로컬 저장소 생성** <span style="font-size:10px; color:gray;">(Git 터미널이 실행된 상태)</span>
    1. 로컬 저장소로 사용할 폴더를 생성합니다.<br>
    `$ cd [작업폴더 상위주소]` <span style="color:gray;">- 로컬 저장소(폴더)를 만들 상위 폴더로 이동</span><br>
    `$ git init [로컬 저장소명]` <span style="color:gray;">- [로컬 저장소명]과 같은 이름의 폴더가 없다면 생성 후 그 저장소를 git에 연동시켜 로컬 저장소로 만듭니다.</span><br>
    `$ cd [로컬 저장소명]` <span style="color:gray;">- 생성한 로컬 저장소로 이동</span><br>
    ><span style="color:gray;">위 내용을 정상적으로 실행한 경우 터미널 입력창에 <u>branch명</u>이 표시됩니다.</span><br>
    >
    2. 파일을 하나 생성합니다.<br>
    `$ echo 'hello world' >> README.md`<br>
    3. 스테이지에 등록하고 커밋합니다.<br>
    `$ git add` <span style="color:gray;">- 스테이지 등록</span><br>
    `$ git commit -m "commit message"` <span style="color:gray;">- 커밋</span>

## **프로토콜**
서버 통신을 위해 프로토콜을 사용해야하며,
깃은 기본적으로 Local, HTTP, SSH, Git 네 종류의 전송 방식을 지원합니다.
- ### **Local(로컬)**<br>
    - 자신의 컴퓨터를 서버로 이용할 때 편리하며, 일반PC(로컬)에 원격 저장소를 생성하는 것을 의미합니다.<br>

    `$ git remote add [원격저장소별칭] [폴더경로]`
    ><span style="color:gray">※ 간단하게 서버를 구축할 수 있고, 빠른 동작이 가능하다는 장점이 있지만,<br>
    모든 자료가 자신의 컴퓨터에 집중되는 위험도 있습니다.</span>

<br>

- ### **HTTP (Hyper Text Transfer Protocol)**
    **특징**
    - HTTP는 SSH처럼 많이 사용하는 프로토콜 중 하나입니다.
    - 깃허브, 비트버킷 같은 호스팅 서버도 HTTP 프로토콜을 지원합니다.

    **접속**
    - 서버에 접속하려면 로그인 절차를 거쳐야 합니다.
    >1. 기존 아이디와 비밀번호만으로 접속자를 인증하여 처리가 가능합니다.
    >2. HTTP는 익명으로 처리가 가능합니다.
    >3. 계정을 이용하여 처리할 수 있습니다.

<br>

- ### **SSH (Secure Shell)**
    **특징**
    - 깃에서 권장하는 프로토콜로 높은 수준의 보안 통신으로 처리하여 안전하게 운영이 가능합니다.
    - SSH 프로토콜 사용 시 주소 앞에 <mark>ssh://계정@주소</mark> 와 같이 프로토콜 타입을 지정해줘야 합니다.

    **접속**
    - 접속 시 인증서를 만들어 사용하며 인증서를 만들 시 <mark>로그인 절차 없이</mark> 접속이 가능합니다.
    > 인증서는 공개키와 개인키로 구분되며 <u>**공개키는 서버에 등록, 개인키는 로컬**</u>에 저장합니다.<br>
    > HTTP와 다르게 익명으로 접속이 불가능하여, 기업에서 깃 서버 운영 시에 적합한 프로토콜입니다.

<br>

- ### **Git**
    - 깃 데몬 서비르르 위한 전용 프로토콜 방식입니다.
    - SSH와 유사하며 인증 시스템이 없어 보안에 취약합니다.
    - 잘 사용하지 않습니다.

## **원격 저장소의 리모트 목록 관리**
원격 저장소 관리 시 remote 명령어를 사용하여 저장소 목록 확인, 등록, 취소 작업이 가능합니다.
><span style="color: gray">※ remote 명령에 -help 옵션 사용 시 remote의 여러 옵션을 확인할 수 있습니다.</span><br>
><span style="color: gray">※ 연결된 원격 저장소가 없는 경우 출력되지 않습니다. </span>

- ### **원격 저장소 이름(별칭) 출력 명령어**
    <원격저장소별칭 출력><br>
    `$ git remote`<br>
    -> origin
- ### **URL 까지 확인 시**
    <출력 내용 - 원격저장소별칭, URL><br>
    `$ git remote -v`<br>
    -> origin https://github.com/opsos1/server_summary.git (fetch)<br>
    -> origin https://github.com/opsos1/server_summary.git (push)

<br>

## **주소와 별칭**
로컬 저장소에 원격 저장소(서버) 등록시 서버 주소가 필요하며,
프로토콜 + 도메인 주소 형태로 된 것을 확인할 수 있습니다.
- ### **원격저장소별칭**
    - 원격 서버 주소는 긴 문자열로 되어있습니다.<br>
    - 이 긴 문자열을 별칭으로 만들어 편하게 사용할 수 있습니다.
- ### **origin**
    - 대표적으로 많이 사용하는 별칭입니다.
    - 자신의 목적에 따라 다른 별칭을 사용할 수 있습니다.

<br>

## **원격 저장소에 연결**
- ### 원격 저장소 연결 시 add 옵션을 이용합니다.
    `임시 예) $ git remote add [원격저장소별칭] [원격저장소URL]`<br>
    `실제 예) $ git remote add origin https://github.com/opsos1/server_summary.git`<br>
    >[출력 예시 - 주소와 별칭](#url-까지-확인-시)
- ### fetch, push 두 주소 출력
    - push는 서버로 전송하는 동작
    - fetch는 반대로 서버에서 가지고오는 동작

<br>

## **소스트리에서 원격 브랜치**
- ### 원격 저장소 등록 시 [main] 브랜치와 [원격] 브랜치가 생성됩니다.<br>
- ### 로컬 저장소와 서버 저장소를 구분하여 표시한 것으로 서로 동기화한 시점을 판별할 수 있습니다.
    >기본 branch명을 main으로 바꾸지 않았다면 main이 아닌 master 브랜치가 생성됩니다.

<br>

## **별칭 이름 변경과 정보**
- 별칭 변경 방법<br>
`임시 예) $ git remote rename 변경전 변경후`<br>
`실제 예) $ git remote rename origin org`
- 원격 저장소에 관한 상세한 정보를 보는 방법<br>
`$ git remote show 원격저장소별칭`
    <출력 내용>
    - 원격저장소별칭
    - `Fetch URL` - 원격 저장소 주소
    - `Push URL` - 원격 저장소 주소
    - `HEAD branch` - 주 브랜치명
    - `Remote branch` - 연결된 브랜치명
    - `Local ref configured for 'git push'` - push 상태

<br>

## **원격 서버 삭제**
`$ git remote rm origin(원격저장소별칭)`
- 삭제 전 상태<br>
    - origin https://github.com/opsos1/server_summary.git (fetch)<br>
    - origin https://github.com/opsos1/server_summary.git (push)
- 삭제 후 상태<br>
    - \-
> ※ 삭제한 별칭의 fetch와 push 모두 삭제된 것을 확인할 수 있습니다.<br>
> ※ $ git remote -v 로 확인한 상태 결과입니다.

<br>
