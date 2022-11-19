[목록][목록] | [이전][이전]

[목록]: README.md "목록"
[이전]: 10-branch-push.md "이전"

# **:wastebasket: 브랜치 삭제**
```PROPERTIES
브랜치를 삭제하는 것은 그 브랜치의 내용과 커밋을 모두 삭제하는 것입니다.
이에 따라 삭제 명령을 실행할 때 주의가 필요합니다.
```
- 브랜치 삭제는 크게 스테이지 상태에 따라 달라집니다.<br>
- 자신이 위치한 브랜치는 삭제할 수 없습니다.
>※ 삭제 시 다른 브랜치로 잠시 이동해있어야 합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194719313-e7e1f920-3bba-430e-bc43-5dfaf3eea745.jpg">
</kbd>

## **:toilet: 일반적인 삭제**
-d 옵션은 스테이지 상태가 깨끗할 때만 로컬 브랜치의 `삭제를 허용`합니다.
>※ 워킹 디렉터리에 작업한 기록이 있거나, add 명령어로 스테이지의 인덱스가 변경되었다면 삭제하지 않습니다.<br>
>※ 병합되지 않은 브랜치도 삭제할 수 없습니다.
```bash
$ git branch -d [브랜치이름] # d 옵션을 통해 삭제
```
<kbd> 
<img src="https://user-images.githubusercontent.com/45596014/194719392-8b9c9128-610d-44bf-aba0-c23846fd0776.jpg">
</kbd>

<br>

## **:toilet: 강제 삭제**
워킹 디렉터리 또는 스테이지에 추가 커밋 작업이 남아있다면 강제로 삭제해야 합니다.

### 1. 브랜치 생성 및 파일 수정 후 커밋
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194719680-5f7e3c7c-143b-4a25-8a98-8a74d7fc9f09.jpg">
</kbd>

<br>

### 2. 브랜치 이동 후 브랜치 삭제 테스트
commit 작업을 한 기록이 있는 상태에서 -d 옵션 사용 시<br>
오류 메시지가 출력되는 것을 확인할 수 있습니다.<br>
>※ 브랜치 삭제 시 커밋도 같이 삭제되기 때문에 처리되지 않은 기록이 남아있을 경우<br>
>&nbsp;&nbsp;&nbsp;&nbsp;이를 방지하기 위해 오류 메시지가 출력됩니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194719831-5d0e4d4c-856f-4a75-a0cc-5233e86a5166.jpg">
</kbd>

<br>

### 3. 브랜치 강제 삭제
로컬 브랜치를 강제로 삭제합니다.
```bash
$ git branch -D [브랜치이름] # D 옵션을 통해 강제 삭제
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194719965-8600b7d7-dcac-4ed4-9800-df1b79b09892.jpg">
</kbd>

<br><br>

## **:evergreen_tree: 소스트리에서 삭제하는 방법**
소스트리를 통해서도 브랜치를 삭제할 수 있습니다.<br>
소스트리의 왼쪽 브랜치 목록 중 삭제하고 싶은 것을 하나 선택해, 삭제 버튼을 클릭합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194720803-1763574b-68e0-4635-bccb-3beef5380622.png">
</kbd>

<br><br>

## **:warning: 리모트 브랜치를 삭제하는 방법**
삭제 명령을 push 하여 원격저장소의 브랜치를 삭제할 수 있습니다.
>※ 원격 브랜치를 삭제할 경우 원격 브랜치에 기록된 커밋이 모두 삭제되기 때문에,<br>
>&nbsp;&nbsp;&nbsp;&nbsp;함께 사용하는 브랜치의 경우 신중하게 삭제해야 합니다.
```bash
$ git push origin --delete [리모트브랜치이름]
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194721116-e4805267-7afa-4a0c-a78f-a6b4314f96f8.jpg">
</kbd>

<br><br>

[이전 - 브랜치 전송](10-branch-push.md)

<br>

[목록](README.md)
