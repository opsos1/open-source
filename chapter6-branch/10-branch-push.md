[목록][목록] | [이전][이전] | [다음][다음]

[목록]: README.md "목록"
[이전]: 09-remote-branch.md "이전"
[다음]: 11-branch-remove.md "다음"

# **:outbox_tray: 브랜치 전송**
```PROPERTIES
로컬저장소의 브랜치를 원격저장소로 전송하는 다른 방법이 있습니다.
```

## **:rocket: 브랜치 푸시**
깃의 push 작업은 로컬저장소의 `파일 뿐 아니라, 브랜치 정보, 커밋`까지 모두 원격저장소로 전송합니다.<br>
처음으로 로컬저장소에 새 원격저장소가 등록되면 다음과 같이 push 할 때 오류가 출력됩니다.<br>
>※ 처음 commit과 push를 할 때, 업스트림 설정이 필요합니다.<br>
>&nbsp;&nbsp;&nbsp;&nbsp;원격저장소와 연결한 것만으로 업스트림이 자동으로 되지 않습니다.<br>
>※ 깃이 원격저장소의 어느 브랜치에 어떻게 푸시할지를 모르기 때문입니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194717521-8344e559-ee45-4eb6-a5a2-388b150ca01a.jpg">
</kbd>

<br>

### **수동 업스트림 설정**
```bash
$ git push --set-upstream origin main # 현재 선택된 브랜치를 origin(저장소 별칭)의 main 브랜치로 보낸다는 의미
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194717493-fc6ef020-79e8-4fe1-943c-f96d103f49ab.jpg">
</kbd>

<br>

### **참고사항**
최초로 로컬저장소에서 원격저장소로 push 할 때, 아이디와 패스워드를 확인합니다.<br>
해당 원격저장소에 대해 권한을 가진 계정으로 로그인할 경우 정상적으로 push 됩니다.<br>
만약 아래와 같은 에러 문구가 출력된다면 권한이 부족한 것입니다.
```
error: insufficient permission for adding an object to repository database
```
직접 서버를 운영한다면 아래와 같이 권한을 줄 수 있습니다.
```bash
$ chmod -R g+ws *
$ chgrp -R git *
```

<br>

## **:triangular_flag_on_post: 브랜치 페치**
일반 커밋 페치와 동일하게 원격 브랜치를 페치한다고 자동으로 로컬저장소에 새 브랜치가 생성되지 않습니다.
>※ fetch는 내려받기만 할 뿐, 자동 병합되지 않기 때문입니다. 

페치가 되면 깃은 단순히 `원격저장소별칭/브랜치` 포인터만 생성합니다.<br>
새 브랜치를 반영하기 위해 병합 명령어를 실행해야 합니다.
```bash
$ git merge [원격저장소별칭/브랜치이름]
```
페치된 브랜치를 병합하지 않고 테스트만 할 때,<br>
원격 브랜치의 포인터를 사용해 `임시 브랜치를 생성`하거나, `직접 체크아웃`할 수 있습니다.
```bash
$ git checkout -b [임시브랜치이름] [origin/브랜치이름] # [임시브랜치 - 원격브랜치] 트래킹
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194718685-22037020-f106-4c53-8349-dd825bd7b086.jpg">
</kbd>

<br><br>

[이전 - 원격 브랜치](09-remote-branch.md)

<br>

[다음 - 브랜치 삭제](11-branch-remove.md)

<br>

[목록](README.md)
