# **:airplane: 순서**
    원격저장소에 다수 개발자가 동시에 commit를 push 할 수 없습니다.
    순차적으로 push 해야합니다.

## **:droplet: 최신 상태**
- push를 할 때 로컬저장소를 항상 원격저장소 보다 최신 상태로 유지해야 합니다.<br>

        A와 B가 같은 커밋 상태의 파일을 작업 후 A가 먼저 commit & push를 한 경우
        B는 최신 원격저장소 상태를 가지지 않기 때문에 push가 거부됩니다.
        이런 경우 서버를 pull 또는 fetch로 다시 받아와 갱신 후 push 해야 합니다.

    >※ push를 할 경우 원격 저장소의 마지막 커밋과 현재 커밋을 병합합니다.<br>
    >※ 이때 새로 추가된 커밋이 없을 경우 프로젝트가 충돌되는 것을 막기 위해 <br>
    >push를 거부합니다.

<br>

## **:newspaper: 최신 상태**
- 깃이 최신 상태에서만 푸시를 허용하는 것은 충돌을 방지하기 위해서입니다.
- 각 개발자들이 다른 영역을 동시에 작업했다면 충돌이 없었을 수 있지만<br>
    같은 영역을 수정한 경우 풀 작업을 할 때 무조건 충돌이 발생합니다.
- 가장 좋은 방식은 로컬저장소와 원격저장소의 상태를 자주 최신으로 맞춰주는 것이 좋습니다.

    ```bash
    pull -> coding -> commit -> pull -> push
    ```

### **인증 정보 캐시**
- ### 깃허브와 같은 호스팅 저장소 이용 시 아이디, 비밀번호가 필요한데,
    ### 깃에서는 인증 정보 캐시 기능을 통해 아이디와 비밀번호를 임시적으로 보관할 수 있습니다.<br><br>

   ```bash
   $ git config --global credential.helper cache
   ```

<br>

### **원격 저장소 관리**
- ### 깃을 원격 저장소에 연결한 경우 ./git/config 파일에 리모트 연결 정보가 추가됩니다.
<br>

    [remote "origin"]
        url = https://github.com/opsos1/server_summary.git
        fetch = +refs/heads/*:refs/remotes/origin/*

<br>

[이전 - 수동으로 내려받기](/index/06_manual-fetch.md)

<br>

[목차](/README.md)
