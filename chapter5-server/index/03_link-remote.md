# **:link:깃허브 연동 및 원격 등록**
```
서버 저장소를 생성했다면 로컬저장소와 연결해야 합니다.
```

## **:computer: 로컬저장소**
- ### **저장소를 연결하는 방식으로 두 가지가 있습니다.**<br>
    1. 새로운 로컬저장소를 만들고, 이 저장소에 원격저장소를 연결<br>
    2. 기존 로컬저장소를 원격저장소에 연결


- ### **로컬저장소 생성** (Git 터미널이 실행된 상태)
    1. 로컬저장소로 사용할 폴더를 생성합니다.<br>
        ```bash
        $ cd [작업 폴더 상위 주소] # 로컬저장소(폴더)를 만들 상위 폴더로 이동
        $ git init [로컬저장소명] # 현재 위치한 주소에 새 파일 생성
        $ cd [로컬저장소명] # 생성한 로컬저장소로 이동
        ```
    >위 내용을 정상적으로 실행한 경우 터미널 입력창에 branch명이 표시됩니다.<br>
    
    2. 마크다운 파일을 하나 생성합니다.<br>
        ```bash
        $ echo 'hello world' >> README.md # EADME 마크다운 파일 생성
        ```
    3. 스테이지에 등록하고 커밋 합니다.<br>
        ```bash
        $ git add # 스테이지
        $ git commit -m "commit message" # 저장소
        ```

## **:earth_asia: 프로토콜**
서버 통신을 위해 프로토콜을 사용해야 하며,
깃은 기본적으로 Local, HTTP, SSH, Git 네 종류의 전송 방식을 지원합니다.
- ### **Local(로컬)**<br>
    자신의 컴퓨터를 서버로 이용할 때 편리하며, 일반 PC(로컬)에 원격저장소를 생성하는 것을 의미합니다.<br>

    ```bash
    $ git remote add [원격저장소별칭] [폴더 경로] # 원격저장소 연결
    ```
    >※ 간단하게 서버를 구축할 수 있고, 빠른 동작이 가능하다는 장점이 있지만,<br>
    모든 자료가 자신의 컴퓨터에 집중되는 위험도 있습니다.

<br>

- ### **HTTP (Hyper Text Transfer Protocol)**
    **특징**
    - HTTP는 SSH처럼 많이 사용하는 프로토콜 중 하나입니다.
    - 깃허브, 비트 버킷 같은 호스팅 서버도 HTTP 프로토콜을 지원합니다.

    **접속**
    - 서버에 접속하려면 로그인 절차를 거쳐야 합니다.
    >1. 기존 아이디와 비밀번호만으로 접속자를 인증하여 처리가 가능합니다.
    >2. HTTP는 익명으로 처리가 가능합니다.
    >3. 계정을 이용하여 처리할 수 있습니다.

<br>

- ### **SSH (Secure Shell)**
    **특징**
    - 깃에서 권장하는 프로토콜로 높은 수준의 보안 통신으로 처리하여 안전하게 운영이 가능합니다.
    - SSH 프로토콜 사용 시 주소 앞에 ssh://계정@주소 와 같이 프로토콜 타입을 지정해 줘야 합니다.

    **접속**
    - 접속 시 인증서를 만들어 사용하며 인증서를 만들 시 로그인 절차 없이 접속이 가능합니다.
    > 인증서는 공개키와 개인키로 구분되며 **공개키는 서버에 등록, 개인키는 로컬**에 저장합니다.<br>
    > HTTP와 다르게 익명으로 접속이 불가능하여, 기업에서 깃 서버 운영 시에 적합한 프로토콜입니다.

<br>

- ### **Git**
    - 깃 데몬 서비스를 위한 전용 프로토콜 방식입니다.
    - SSH와 유사하며 인증 시스템이 없어 보안에 취약합니다.
    - 잘 사용하지 않습니다.

## **:bookmark: 원격저장소의 리모트 목록 관리**
### 원격저장소 관리 시 remote 명령어를 사용하여 저장소 목록 확인, 등록, 취소 작업이 가능합니다.
>※ remote 명령에 -help 옵션 사용 시 remote의 여러 옵션을 확인할 수 있습니다.<br>
>※ 연결된 원격저장소가 없는 경우 출력되지 않습니다.<br>

<kbd>
<img width="500" alt="image" src="https://user-images.githubusercontent.com/45596014/193407314-74aa565b-a71d-4c8f-972e-75b0fad595f4.jpg">
</kbd>

<br>

- ### **원격저장소 이름(별칭) 출력 명령어**
    ```bash
    $ git remote
    ```
    <kbd>
    <image width="400" src="https://user-images.githubusercontent.com/45596014/193407244-423c705a-3e0f-4cdf-9a39-cc6092a604c1.jpg">

    </kbd>

- ### **URL까지 확인 시**
    ```bash
    $ git remote -v
    ```
    
    <kbd>
    <img width="500" src="https://user-images.githubusercontent.com/45596014/193407558-20587eeb-ee97-4c30-8588-e21718c57723.jpg">
    </kbd>

<br>

## **:mailbox: 주소와 별칭**
로컬저장소에 원격저장소(서버) 등록 시 서버 주소가 필요하며,
프로토콜 + 도메인 주소 형태로 된 것을 확인할 수 있습니다.
- ### **원격저장소별칭**
    - 원격 서버 주소는 긴 문자열로 되어있습니다.<br>
    - 이 긴 문자열을 별칭으로 만들어 편하게 사용할 수 있습니다.<br>
    <kbd>
    <img width="500" src="https://user-images.githubusercontent.com/45596014/193394676-d3bff961-d6d7-466b-bd62-d2ae1f406da4.png">
    </kbd>
- ### **origin**
    - 대표적으로 많이 사용하는 별칭입니다.
    - 자신의 목적에 따라 다른 별칭을 사용할 수 있습니다.

<br>

## **:electric_plug: 원격저장소에 연결**
- ### 원격저장소 연결 시 add 옵션을 이용합니다.
    ```
    $ git remote add [원격저장소별칭] [원격저장소 URL]
    ```
- ### **fetch, push** 두 주소 출력
    - push는 서버로 전송하는 동작
    - fetch는 반대로 서버에서 가지고 오는 동작

<br>

## **:evergreen_tree: 소스 트리에서 원격 브랜치**
- ### 원격저장소 등록 시 [master] 브랜치와 [원격] 브랜치가 생성됩니다.<br>
- ### 로컬저장소와 서버 저장소를 구분하여 표시한 것으로 서로 동기화한 시점을 판별할 수 있습니다.

<br>

## **:name_badge: 별칭 이름 변경과 정보**
- 별칭 변경 방법<br>
    ```bash
    $ git remote rename [변경 전] [변경 후]
    ```
- 원격저장소에 관한 상세한 정보를 보는 방법<br>
    ```bash
    $ git remote show 원격저장소별칭
    ```
    <kbd>
    <img width="650" src="https://user-images.githubusercontent.com/45596014/193407693-2a8b4d53-d4dc-4388-83b2-39035e945b67.jpg">
    </kbd>


<br>

## **:scissors: 원격 서버 삭제**
`$ git remote rm origin(원격저장소별칭)`
- 삭제 전 상태<br>
    <kbd>
    <img width="469" alt="image" src="https://user-images.githubusercontent.com/45596014/193407558-20587eeb-ee97-4c30-8588-e21718c57723.jpg">
    </kbd>

- 삭제 후 상태<br>
    <kbd>
    <img width="469" src="https://user-images.githubusercontent.com/45596014/193407798-c72ac5f1-b03e-4d88-8a09-5d9126ad5416.jpg">
    </kbd>

> ※ 삭제한 별칭의 fetch와 push 모두 삭제된 것을 확인할 수 있습니다.<br>
> ※ $ git remote -v 로 확인한 상태 결과입니다.

<br>

[이전 - 서버 준비](02_server-ready.md)

<br>

[다음 - 서버 전송](04_push.md)

<br>

[목차](../README.md)
