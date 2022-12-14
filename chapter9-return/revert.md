[목록][목록] | [이전][이전]

[목록]: ../README.md "목록"
[이전]: reset.md "이전"

# **:recycle: 리버트**
공개된 커밋은 보통 리셋 작업을 하지 않으며,<br>
공개된 커밋을 이전 상태로 되돌리기 위해 `revert` 를 사용합니다.
리버트와 리셋의 차이점은 커밋 정보 삭제 여부 입니다.

## **:scissors: 취소커밋**
`reset` 은 기존 커밋 정보를 삭제하는 반면,<br>
`revert` 는 기존 커밋을 남겨두고 취소에 대한 `새로운 커밋` 을 생성합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202175520-31d2b8de-f6ba-40da-9a1d-ae9d95d40377.jpg">
</kbd>

### **실습**
1. `revert` 명령 실습을 위해 master 브랜치에서<br>
    코드를 수정한 후 커밋을 몇 개 추가합니다.
    <!-------------------------------------------------------->
    <details>
    <summary>

    **commit 1 (menu 5)**<br>

    </summary>
    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202175340-0e9fc626-0624-457f-a455-28deca65d759.jpg">
    </kbd>

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git commit -am "menu5"  # menu5 등록 및 커밋
    > [master e19c0b4] menu5
    >  1 file changed, 1 insertion(+)
    ```
    </details>
    <!---------------------------------------------------------->
    <details>
    <summary>

    **commit 2 (menu6)**

    </summary>

    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202176487-854d183a-2ac5-4717-ad4f-43a31621a20b.jpg">
    </kbd>

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git commit -am "menu6"  # menu6 등록 및 커밋
    > [master 1ea5e47] menu6
    >  1 file changed, 1 insertion(+)
    ```

    </details>

    <!---------------------------------------------------------->
    <details>
    <summary>

    **commit 3 (menu7)**

    </summary>
    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202178341-33c24dad-0e3a-447f-a5cd-fd612ff5fb2f.jpg">
    </kbd>

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git commit -am "menu7"  # menu7 등록 및 커밋
    > [master 5374918] menu7
    >  1 file changed, 1 insertion(+)
    ```

    </details>

<br>

2. 현재 마지막 커밋의 상태는 menu7까지 이며,<br>
    마지막 커밋인 menu7을 취소할 경우 `revert` 를 사용합니다.
    > ※ revert 명령어를 사용하면 병합할 때처럼<br>
    > &nbsp;&nbsp;&nbsp;&nbsp;메시지를 작성할 수 있는 vi 에디터가 실행됩니다.<br>
    > ※ revert 메시지를 작성한 후 저장합니다.


    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git revert HEAD  # 현재 커밋을 리버트
    ```

    <kbd>
    <img width="800" src="https://user-images.githubusercontent.com/45596014/202322930-83e96938-4fef-46fb-a29a-c7eb864d3ad2.png">
    </kbd>

    **2-1.** 메시지 저장 후 출력되는 메시지
    ```bash
    > [master 00d7770] Revert "menu7"
    >  1 file changed, 1 deletion(-)
    ```

<br>

3. 상태<br>
    

    **3-1.** menu.htm 상태<br>
    menu7 가 담긴 \<li> 태그가 사라졌습니다.

    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202325173-cac69c22-6495-4369-bc8b-d2f0bcb550d1.png">
    </kbd>

    **3-2.** 소스트리 상태<br>
    menu7 커밋 위에 새 리버트 커밋이 생성되었습니다.

    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/202325673-c9467103-fd1a-41a3-b42f-275410cc12e6.jpeg">
    </kbd>

<br>

### **리버트 지정**
`revert` 는 한 번에 한 커밋만 취소할 수 있기 때문에<br>
여러 커밋을 `revert` 하기 위해서 최신 커밋부터 순차적으로 취소해야합니다.

1. `revert` 에서 특정 커밋을 취소할 경우 해시 값을 지정합니다.
    ```bash
    $ git revert [commit ID]
    ```

2. 범위 연산자를 지정해서 여러 커밋을 리버트할 수도 있습니다.
    > ※ 연산자 `..` 을 같이 사용합니다.
    ```bash
    $ git revert [commit ID] .. [commit ID]
    ```

<br>

### **소스트리에서 리버트**
소스트리에서 커밋을 선택하고, 마우스 우클릭을 한 후,<br>
`커밋 되돌리기` 메뉴를 선택합니다.
> ※ 알림창이 나오고, 리버트를 진행하려면 "예"를 누릅니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202436371-137acfea-5395-4cf8-90d0-1388ea6104f8.jpg">
</kbd>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202436511-6f79c24b-9452-41bb-af03-476427907348.jpg">
</kbd>

<br>

### **병합 취소**
리셋은 방금 전 실행한 병합만 삭제합니다.<br>
하지만 리버트는 시간이 지난 후에도 과거의 병합을 선택하여 취소할 수 있습니다.

1. 병합 취소 실습을 위해 menu 브랜치를 다시 병합합니다.
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git merge menu  # 병합
    > Auto-merging menu.htm
    > Merge made by the 'recursive' strategy.
    >  menu.htm | 6 +++++-
    >  1 file changed, 5 insertions(+), 1 deletion(-)
    ```
2. master 브랜치의 코드를 수정 후 커밋합니다.
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ code menu.htm  # VS Code 실행

    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git commit -am "menu7"  # 등록 및 커밋
    > [master da4d8e4] menu7
    >  1 file changed, 1 insertion(+)
    ```
    
    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202333839-00ec50f7-4799-4a3f-ade3-bcc12fb2db8e.jpg">
    </kbd>

3. 소스트리를 통해 병합 커밋과 새로운 추가 커밋이<br>
하나 더 생성된 것을 확인할 수 있습니다.

    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/202335734-fd726f19-b446-427d-91fe-2c3ea167da1a.jpeg">
    </kbd>

4. 리버트로 병합 취소 시 --mainline 옵션을 함께 사용할 수 있습니다.
    > ※ 리버트로 병합이 취소되면 둘 중 한 브랜치로 체크아웃 해야합니다.<br>
    > ※ `--mainline` 옵션은 병합을 취소한 후 체크아웃되는 브랜치를 표시합니다.<br>
    > ※ `--mainline`은 체크아웃으로 되돌아가는 커밋 번호 입니다.

    ```bash
    $ git revert --mainline [Number] [merge-commit ID]
    ```

5. 실습 전 현재 커밋 상태<br>
    --graph 옵션을 사용하여 그래프 형태로 로그를 확인합니다.

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git log –oneline –graph
    > * da4d8e4 (HEAD -> master) menu7
    > *   84b6618 Merge branch 'menu'
    > |\
    > | * 7f5fad8 (menu) menu1-1
    > * | 00d7770 Revert "menu7"
    > * | 5374918 menu7
    > * | 1ea5e47 menu6
    > * | e19c0b4 menu5
    > * | dd6d215 menu3/4
    > |/
    > * f1c704f menu2
    > * b741eef menu1
    > * 69bf712 first
    ```

    **5-1.** `-5` 옵션을 사용하면 로그 5개만 출력됩니다.<br>
    - 출력 결과에서 `84b6618`은 병합 시점의 commit ID입니다.<br>
    
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git log –oneline –graph -5  # 로그 확인
    > * da4d8e4 (HEAD -> master) menu7
    > *   84b6618 Merge branch 'menu'
    > |\
    > | * 7f5fad8 (menu) menu1-1
    > * | 00d7770 Revert “menu7”
    > * | 5374918 menu7
    ```

6. 84b6618 시점으로 리버트 합니다.
    > ※ 리버트 메시지도 작성합니다.

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
    $ git revert –mainline 1 84b6618  # 리버트
    > [master 4399642] Revert “Merge branch 'menu'”
    >  1 file changed, 1 insertion(+), 5 deletions(-)
    ```
    
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/202355470-f71ee208-d49d-4f38-91a1-92240ac70e04.jpeg">
    </kbd>
    <details>
    <summary>

    menu.htm 상태

    </summary>

    리베이스된 병합은 리버트하기가 어렵습니다.<br>
    그 이유는 리베이스로 병합된 공통 조상 커밋을 찾기 어렵기 때문입니다.

    <kbd>
    <img width="600" src="https://user-images.githubusercontent.com/45596014/202355827-156b93f0-a0c7-49aa-bae2-cd2d841604fd.png">
    </kbd>

    </details>

    <br>

### **리버트 히스토리**
`revert` 실행 시 새 커밋이 생성되기 때문에 커밋이력이 복잡해집니다.<br>
깔끔한 이력 관리를 위해 `reset` 이 더 편리해 보일 수 있습니다.

하지만 저장소가 공개되어있는 상태에서 `reset` 으로 커밋을 삭제하는 것은,<br>
협업 차원에서 위험하기 때문에 이때는 `revert` 가 유용합니다.

<br><br>

## **정리**
- `reset` 과 `revert` 는 모두 과거로 돌아간다는 점에서 비슷합니다.<br>
- `reset` 은 커밋 자체를 삭제하고 전으로 돌아가기 때문에<br>
    협업을 할 때에는 사용하지 않는 것이 좋습니다.
- `revert` 는 취소하려는 커밋의 전 상태를 새로운 커밋으로 생성하기 때문에<br>
    저장소가 공개된 상태에서 사용하는 것이 좋습니다.

<br><br>

[이전 - 리셋(reset)](reset.md)

<br>

[목차](Readme.md)
