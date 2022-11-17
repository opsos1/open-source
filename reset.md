# **:red_circle: 리셋**
`reset` 은 커밋을 기준으로 이전 코드로 되돌리는 방법으로,<br>
기록한 커밋을 취소합니다.
> ※ 커밋을 취소하는 만큼 리셋할 때는 항상 신중하게 작업해야 합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202358888-d43619e0-230a-4974-aede-9f392ef7f2f1.jpg">
</kbd>

<br><br>

## **:triangular_flag_on_post: 복귀 시점**
이전 코드로 복귀하려면 복귀 시점을 알려 주어야 합니다.<br>
`reset` 은 이 시점을 `commit` 을 기준으로 정합니다.<br>
> ※ 커밋은 `log` 명령을 통해 해시 값을 조회할 수 있고,<br>
> ※ 이는 복귀할 특정 시점을 찾는 데 매우 유용합니다.

### **로그 기록 확인**<br>
- `reset` 을 사용하기 전 커밋의 해시 값을 확인해야합니다.<br>
- 이때 `commit message` 는 특정 commit 시점을 파악하기에 매우 중요합니다.<br>

    > ※ 실습 시 커밋의 해시 값이 중요하며,<br>
    > ※ 본 예시에서 출력된 해시 값이 아닌 본인 로그의 해시 값을 확인해야 합니다.

    > ※  해시 값을 사용하지 않아도, HEAD 포인터를 통해 상대적 위치를 지정할 수 있습니다.<br>
    > &nbsp;&nbsp;&nbsp;&nbsp;`$ git reset -hard HEAD^^^`

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인

> 7f068b6 (HEAD -> master) menu5
> 6619c99 menu4
> b728366 menu3
> f1c704f menu2
> b741eef menu1
> 69bf712 first
```

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202359162-7b60545c-8d21-4ffa-89de-2fa89eb50e4e.jpg">
</kbd>

<br><br>

## **:page_with_curl: reset 명령어**
`reset` 명령어 사용 시 특정 커밋의 해시 값 상태로 모든 코드를 복구합니다.<br>
```bash
$ git reset [옵션] [커밋ID]
```
### **옵션**<br>
`reset` 명령어는 옵션을 함께 사용해야하며, 3가지 옵션이 있습니다.<br>
> ※ 기본 옵션 값은 mixed입니다. <br>
> ※ soft 옵션과 mixed 옵션 차이는 크게 스테이지 영역과 관련이 있습니다.<br>
> ※ hard 옵션은 워킹 디렉터리와 관련이 있습니다.
- **`soft`** : 스테이지 영역을 포함한 상태로 복원합니다.
- **`mixed`** : reset 명령어를 사용할 때 옵션을 지정하지 않으면 기본값인 mixed로 선택됩니다.
- **`hard`** : 실제 파일이 삭제된 이전 상태로 복원합니다.

<br>

## **:ghost: soft 옵션**
soft 옵션은 가장 낮은 단계의 리셋 동작입니다.
> ※ soft 옵션을 사용하면 별도의 메시지가 출력되지 않습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset –soft HEAD~  # 이전 커밋으로 soft 옵션을 사용한 리셋
```
### **현재 상태**<br>
soft 옵션은 지정한 커밋 위치로 복귀하며,<br>
복귀하면서 스테이지 영역의 상태도 같이 복귀합니다<br>
- soft 옵션은 파일을 수정 후 스테이지 영역에 올려 커밋을 실행하기 직전의 단계로 되돌립니다.

> ※ 이처럼 soft 옵션은 단순히 HEAD 위치를 이동하는 역할만 합니다.<br>
> ※ 마치 직전의 커밋 단계로 체크아웃하라는 명령과 유사합니다.
> > ※ `reset --soft` 명령어와 체크아웃 명령어는 HEAD 위치를 이동한다는 점에서는 동일하지만,<br>
> > ※ 브랜치를 변경하지 않는다는 점에서 차이가 있습니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202376091-441f4bf5-ac00-4102-9d0a-1d19ddaeb06e.jpg">
</kbd>
<!----------------------------------------------------------->
<details>
<summary>

**소스트리 확인**<br>

</summary>

- 마지막 menu5 커밋이 사라지고 커밋하지 않은 변경 사항이 보입니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201473560-874bcd80-135a-4508-a076-46c09d8ae77c.png">
</kbd>
</details>
<!----------------------------------------------------------->
<details>
<summary>

**log 명령어로 확인**

</summary>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인

> 6619c99 (HEAD -> master) menu4 
> b728366 menu3
> f1c704f menu2
> b741eef menu1
> 69bf712 first
```

**menu.htm 확인**<br>
reset 하기 전 내용이 그대로 남아있습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm  # VS Code 실행
```
    
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202371426-e0d31c5c-585a-4d56-bde4-84263cbe95d6.jpg">
</kbd>
    
</details>
<!----------------------------------------------------------->
<details>
<summary>

**diff를 통한 차이 확인**<br>

</summary>

menu.htm 파일에 새로운 menu5가 추가된 것을 확인할 수 있습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD  # 커밋 비교
> diff –git a/menu.htm b/menu.htm
> index f717854..9ae7cfc 100644
> — a/menu.htm
> +++ b/menu.htm
> @@ -3,4 +3,5 @@
>      <li>menu2</li>
>      <li>menu3</li>
>      <li>menu4</li>
> +    <li>menu5</li>  # 파일 수정이 추가됨
>  </ul>
> \ No newline at end of file
```
</details>
<!----------------------------------------------------------->
<details>
<summary>

**status를 통한 상태 확인**

</summary>

메뉴 파일은 수정된 상태이며,<br>
수정된 파일은 스테이지 영역에 등록되어 있습니다.
> ※ status 명령어를 실행한 출력 결과에서 메시지가 초록색으로 표기되는 것을 보면,<br>
> add 명령어를 사용하지 않고도 바로 커밋할 수 있는 직전의 상황입니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status  # 상태 확인
> On branch master
> Changes to be committed:
>   (use "git reset HEAD <file>…" to unstage)
>  modified: menu.htm  # 파일이 변경된 상태
```

</details>

### **menu5 재 커밋**
처음과 동일한 상태가 된 것을 확인할 수 있습니다.
> ※ 새로 커밋을 했기 때문에 처음 커밋 해시 값과는 다른 것을 볼 수 있습니다.<br>
> ※ reset –soft 명령어의 원리를 이용하면 마지막 커밋을 수정할 수 있습니다.<br>
> &nbsp;&nbsp;&nbsp;&nbsp;마치 –amend 명령어와 유사합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu5"  # 다시 커밋
> [master 34df5c3] menu5
>  1 file changed, 1 insertion(+)
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202375647-c5663b88-281a-4713-a230-4fe281aa3af8.jpg">
</kbd>

<br>

**log 확인**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인
> 34df5c3 (HEAD -> master) menu5  # 커밋 해시 값이 변경됨
> 6619c99 menu4
> b728366 menu3
> f1c704f menu2
> b741eef menu1
> 69bf712 first
```

<br>

## **:rainbow: mixed 옵션**
`mixed` 옵션은 `reset` 의 기본 옵션입니다.
```bash
$ git reset -mixed [commit ID]
$ git reset [commit ID]  # -mixed 생략 가능
```
### **mixed 사용 실습**<br>
unstaged 상태로 변경되었다는 리셋 메시지가 같이 표시됩니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset –mixed HEAD~   # mixed 옵션을 사용한 리셋 실행
> Unstaged changes after reset:
> M       menu.htm
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202376905-5dc39a74-3b69-4e93-959f-e95f9f1b25b2.jpg">
</kbd>

<!----------------------------------------------------------->
<details>
<summary>

**status를 통한 확인**

</summary>

스테이지 상태를 제외하고 복원하기 때문에 Unstaged 상태가 되어<br>
메시지가 빨간색으로 표시됩니다.
> ※ soft 옵션과 달리 리셋한 후 스테이지 상태까지 복원하지 않습니다.<br>
> ※ status 명령어로 깃의 상태를 확인합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status  # 상태 확인
> On branch master
> Changes not staged for commit:
>   (use "git add <file>…" to update what will be committed)
>   (use "git checkout – <file>…" to discard changes in working directory)
>   modified:   menu.htm
> no changes added to commit (use "git add" and/or "git commit -a")
```
</details>
<!----------------------------------------------------------->
<details>
<summary>

**menu.htm 확인**

</summary>

<kbd>
<img width="600" src="https://user-images.githubusercontent.com/45596014/202371426-e0d31c5c-585a-4d56-bde4-84263cbe95d6.jpg">
</kbd>
</details>
<!----------------------------------------------------------->
<details>
<summary>

**diff를 통한 차이 확인**

</summary>

새로운 menu5가 추가되었다고 나옵니다. 변경 파일 내용은 워킹 디렉터리에 저장되었습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD  # 커밋 비교
> diff –git a/menu.htm b/menu.htm
> index f717854..9ae7cfc 100644
> — a/menu.htm
> +++ b/menu.htm
> @@ -3,4 +3,5 @@
>      <li>menu2</li>
>      <li>menu3</li>
>      <li>menu4</li>
> +    <li>menu5</li> 파일 수정이 추가됨
>  </ul>
> \ No newline at end of file
```
</details>

### **menu5 재 커밋**
다음 실습을 위해 다시 menu5를 등록하여 커밋합니다.
> ※ mixed 실행 후 다시 커밋하려면 꼭 add 명령어를 실행해야합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git add menu.htm  # 스테이지에 등록
 
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu5"  # 커밋
> [master 1a79348] menu5
>  1 file changed, 1 insertion(+)
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202425451-42a60916-2b71-435c-b780-7a0a441ffbc4.jpg">
</kbd>

<br><br>

## **:wrench: hard 옵션**
리셋되는 복귀 시점의 커밋 상태와 해당 커밋의 워킹 디렉터리까지 모두 되돌립니다.<br>
- hard 옵션을 실행하면 리셋된 결과 메시지가 출력됩니다.<br>
- 삭제 이후의 마지막 HEAD 커밋의 해시 값이 출력됩니다.
> ※ reset –hard 명령어를 사용한 커밋 이후의 모든 내용은 삭제됩니다.<br>
> ※ 따라서 hard 옵션은 주의해서 사용해야 합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset –hard HEAD~  # 완전 삭제
> HEAD is now at 6619c99 menu4
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202425990-befdba85-e3b6-477c-89d8-f1920a08fc73.jpg">
</kbd>
<!----------------------------------------------------------->
<details>
<summary>

**소스트리를 통한 확인**

</summary>
soft 옵션 리셋과 달리 '커밋하지 않은 변경 사항'이 없습니다.<br>
그리고 menu4로 HEAD 포인터가 변경되었습니다.

<br>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201517305-97e86742-1c94-47ee-905a-0e084ddb6a47.png">
</kbd>

</details>
<!----------------------------------------------------------->
<details>
<summary>

**log를 통한 확인**

</summary>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인
> 6619c99 (HEAD -> master) menu4
> b728366 menu3
> f1c704f menu2
> b741eef menu1
> 69bf712 first
```

</details>
<!----------------------------------------------------------->
<details>
<summary>

**menu.htm 확인**

</summary>

이번에는 파일에서 `<li>menu5</li>` 코드가 삭제되었습니다.<br>
실제 파일 내용이 변경되는 것은 `hard` 옵션을 사용하면 워킹 디렉터리 내용도 함께 삭제되기 때문입니다.
> ※ 이전 커밋으로 완전히 리셋된 것을 확인할 수 있습니다.

`menu.htm`
```html
<ul>
    <li>menu1</li>
    <li>menu2</li>
    <li>menu3</li>
    <li>menu4</li>
</ul>
```

</details>
<!----------------------------------------------------------->
<details>
<summary>

**status를 통한 확인**

</summary>

워킹 디렉터리와 스테이지가 모두 비어 있는 깨끗한 상태입니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status  # 상태 확인
> On branch master
> nothing to commit, working tree clean
```

</details>

<br>

## **:evergreen_tree: 소스트리**
리셋을 하기 위해 커밋 해시 값이 필요하며,<br>
소스트리를 이용해 더 쉽게 리셋할 수 있습니다.

### **소스트리 사용**
**:one:** &nbsp;&nbsp;먼저 소스트리의 커밋 그래프에서 복귀할 커밋을 선택합니다.<br>
그리고 마우스 오른쪽 버튼을 눌러 이 커밋까지 현재 브랜치를 초기화 메뉴를 선택합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202426298-b03f2658-710b-4714-9f54-5d5030097647.jpg">
</kbd>

<br><br>

**:two:** &nbsp;&nbsp;1번 실생 시 팝업창이 열립니다.<br>
앞에서 학습한 soft, mixed, hard 리셋 옵션을 선택할 수 있습니다.
> ※ `hard` 옵션 선택 시 경고 메시지를 출력하며 진행 여부를 확인합니다.<br>
> ※ 진행 시 `예`를 누릅니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201517749-a49c341f-0470-4c0e-8092-16bcf13c7686.png">
</kbd>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202426459-4beecce1-fa4b-4166-9893-1871d5fb41fa.jpg">
</kbd>

<br><br>

## **:hamburger: 커밋 합치기**
앞서 `rebase` 병합의 `-i` 옵션은 여러 커밋을 하나로 합치는 동작을 수행하고,<br>
단일 커밋은 커밋 명령어의 `-amend` 옵션으로 수정할 수 있었습니다.

리셋 동작의 원리를 이해한다면, `-soft` 옵션으로 커밋을 수정할 수 있습니다.

### **로그 확인**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인
> 6619c99 (HEAD -> master) menu4
> b728366 menu3
> f1c704f menu2
> b741eef menu1
> 69bf712 first
```

### **커밋 합치기 실습**
최신 커밋 HEAD를 기준으로 2단계 전 상태로 리셋합니다.
> ※ menu2를 가리키는 f1c704f 커밋을 의미합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset –soft HEAD~2  # 2단계 전의 커밋으로 리셋
```

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log –oneline  # 로그 확인
> f1c704f (HEAD -> master) menu2
> b741eef menu1
> 69bf712 first
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202427352-38e7db42-e356-4760-8c0f-cbc9493a89a3.jpg">
</kbd>

<!----------------------------------------------------------->
<details>
<summary>

**diff를 통한 확인**

</summary>

워킹 디렉터리와 스테이지가 모두 비어 있는 깨끗한 상태입니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD~  # 커밋 비교
> diff –git a/menu.htm b/menu.htm
> index d11d058..f717854 100644
> — a/menu.htm
> +++ b/menu.htm
> @@ -1,3 +1,6 @@
>  <ul>
>      <li>menu1</li>
> +    <li>menu2</li> 추가로 상태가 변경됨
> +    <li>menu3</li>
> +    <li>menu4</li>
>  </ul>
> \ No newline at end of file
```

</details>
<!----------------------------------------------------------->
<details>
<summary>

**소스트리를 통한 확인**

</summary>

소스 코드는 기존 menu2에 추가된 내용과 menu3, menu4가 남아 추가된 상태이며<br>
워킹 디렉터리와 스테이지 영역이 변경되었습니다. 

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201520269-d5f2f1e2-0304-4af8-9132-ce91b1f91b39.png">
</kbd>

</details>

**커밋 합치기 실습**
합친 커밋을 생성한 후 소스트리의 그래프를 확인하면, menu3과 menu4를 합친 커밋을 볼 수 있습니다.<br>
> ※ menu3과 menu4는 커밋 2개를 합쳐 커밋 하나를 만든 것과 같습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu3/4"  # 커밋
> [master dd6d215] menu3/4
>  1 file changed, 2 insertions(+)
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201520407-33eaccf4-6758-4152-9784-d8597ed5e415.png">
</kbd>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202427967-c9ba3ae2-17f5-453c-b846-f08840ac279d.jpg">
</kbd>

<br><br>

## **:outbox_tray: 스테이지 리셋**
스테이지 영역에서 등록된 파일을 다시 unstage 상태로 만들 때는<br>
reset 명령어를 사용합니다.
> ※ reset 명령어 다음에 커밋 ID 대신 파일 이름을 사용하면 됩니다.
> ※ 중간에 –mixed HEAD가 생략된 형태입니다.
```bash
$ git reset [파일명]  # unstaged
$ git reset -mixed HEAD [파일명]  # 위 명령어와 같음
```
아래와 같이 사용할 수 있습니다.
```bash
$ git reset [commit ID] [파일명]
```

<br>

## **:bomb: 작업취소**
수정 작업을 완전히 취소하려면 워킹 디렉터리와 스테이지 상태를<br>
모두 제거하여 마지막 커밋 상태로 되돌려 놓아야 합니다.
> ※ 리셋할 때의 시점을 현재 HEAD를 기준으로 하면 해당 시점의 수정 작업을 모두 삭제할 수 있습니다.

```bash
$ git reset -hard HEAD
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202428333-5874624a-6fbb-43fb-8437-b3f7f86892be.jpg">
</kbd>

<br><br>

## **:bomb: 병합 취소**
리셋은 병합된 브랜치도 취소할 수 있습니다.<br>

### **실습**
menu2의 커밋 해시키를 직접 지정하여 menu 브랜치를 생성한 후,<br>
menu 브랜치로 체크아웃합니다.
> ※ 실습을 위해 아래와 같은 커밋 환경을 설정합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202428555-b2823715-26b4-43d6-a8d0-016c10b7770f.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git checkout -b menu f1c704f  # menu2의 해시키를 직접 지정
> Switched to a new branch 'menu'
```

만든 브랜치에서 menu.html 파일을 수정, 저장 후 커밋합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ code menu.htm  # VS code 실행
```

<kbd>
<img width="600" src="https://user-images.githubusercontent.com/45596014/201651223-2611e363-3d0c-45ec-80b1-9678724d82cf.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ git commit -am "menu1-1"
> [menu 7f5fad8] menu1-1
>  1 file changed, 5 insertions(+), 1 deletion(-)
```
<!----------------------------------------------------------->
<details>
<summary>

**소스트리를 통한 확인**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201652736-e9895c27-5e38-47a8-910f-518336bcca08.jpg">
</kbd>

</details>

menu 브랜치와 master 브랜치를 병합합니다.
> ※ 다른 브랜치로 체크아웃되어 있다면 병합을 위해 먼저 master 브랜치로 체크아웃합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ git checkout master  # 브랜치 이동
> Switched to branch 'master'
```

<br>

merge 명령어를 실행하며,<br>
두 브랜치는 3-way 방식으로 병합되기 때문에<br>
병합 메시지를 작성해야 합니다.<br>
> ※ 명령어를 실행한 후 vi 에디터 창이 열리면 메시지를 작성하고 저장하여 빠져나옵니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git merge menu  # 병합
> Auto-merging menu.htm
> Merge made by the 'recursive' strategy.
>  menu.htm | 6 +++++-
>  1 file changed, 5 insertions(+), 1 deletion(-)
```

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201658314-77ace812-5541-4f52-baf9-fd165ba09452.jpeg">
</kbd>

커밋 리셋 후 취소하여 확인합니다.
> ※ 병합 커밋이 취소된 것을 확인할 수 있습니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset –merge HEAD~  # 이전 커밋 리셋
```

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201658920-976c3c1c-8c23-45da-b7e0-b583455553c4.jpeg">
</kbd>

<br>

## **:warning: 주의할 점**
1. 리셋 기능을 통해 독립된 개인 프로젝트 관리 시 쉽게 이전 상태로 복귀할 수 있으나,<br>
저장소를 외부에 공개했거나 공유하고 있다면 주의해서 리셋을 사용해야 합니다.<br>
2. 작성된 커밋이 리셋으로 삭제되면 함께 작업하는 개발자에게 혼란을 줄 수 있습니다.<br>
3. 일반적으로 협업하거나 소스 코드를 공유한 후에는 리셋 작업을 하지 않습니다.

<br><br>

[다음 - 리버트(revert)](revert.md)

<br>

[목차](README.md)