[목록][목록] | [이전][이전] | [다음][다음]

[목록]: ../README.md "목록"
[이전]: 05_auto-pull.md "이전"
[다음]: 07_order.md "다음"

# **:floppy_disk: 수동으로 내려받기**
    원격저장소 내용을 내려받는 큰 방법으로 pull, fetch 두 방법이 있고,
    두 방법의 차이는 병합의 여부입니다.

<br>

## **:inbox_tray: fetch 가져오기**
- ### 원격저장소 코드를 수동으로 내려받는 작업입니다.
- ### 내려받은 후 현재 브랜치와 자동 병합하지 않습니다.

```bash
$ git fetch [원격저장소URL]
```

>※ 원격저장소의 커밋들만 가지고 오고,<br>
>로컬저장소에서 아무 작업도 하지 않습니다.<br>
>※ fetch 사용 시 임시 브랜치가 생성되지만 이 브랜치에 커밋 할 수 없습니다.

<kbd>
<img width="300" src="https://user-images.githubusercontent.com/45596014/193400275-40b7e500-68cf-4abb-981c-04d0e526fd0b.jpg">
</kbd>

<br>

## **:open_hands: merge 명령어로 수동 병합**
- ### fetch 상태에서 merge를 통해 병합할 수 있습니다.

```bash
$ git merge [원격저장소별칭/브랜치이름]
```

<br><br>

[이전 - 자동으로 내려받기](05_auto-pull.md)

<br>

[다음 - 순서](07_order.md)

<br>

[목차](../README.md)
