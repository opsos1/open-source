# **:feet: 복귀**
깃은 소스 코드의 시간에 따른 변화 흐름을 기록합니다.<br>
이렇게 저장된 변화 흐름 단계를 커밋(commit)이라고 하며,<br>
본 소스에서는 커밋을 기준으로 특정 시점의 상태로 되돌리는 방법을 알아보겠습니다.

<br>

## **:bookmark: 목차**
### [**01. 되돌리기**](History.md)

### [**02. 리셋(reset)**](Current.md)

### [**03. 리버트(revert)**](source.md)

<br>

# **:repeat: 다시시작**
한 두줄 변경된 코드는 언제든 다시 시작할 수 있지만,<br>
몇 시간, 며칠을 작업한 코드의 경우 쉽지 않습니다.<br>

그렇기 때문에 문제가 발생했을 때 문제를 억지로 해결하려고 노력하는 것보다,<br>
지금까지 한 작업을 포기하고 다시 시작하는 것이 좀 더 빠르게 해결할 수 있는 방법이 될 수도 있습니다.<br>

이때 깃에서 `reset`과 `revert`를 통해 기록된 커밋을 기준으로 이전 상태로 되돌릴 수 있습니다.

## **:herb: 실습 준비**
### 새 깃 저장소 초기화
```bash
$ cd 실습폴더  # 실습 폴더의 부모 폴더로 이동
$ mkdir gitstudy09  # 실습 폴더 생성
$ cd gitstudy09  # 실습할 폴더로 이동

infoh@DESKTOP MINGW64 /e/gitstudy09
$ git init  # 저장소 초기화
> Initialized empty Git repository in E:/gitstudy09/.git/
```

### menu.htm 파일 생성 및 수정
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm # 파일 수정/저장을 위한 VS Code 실행
```
`menu.htm`
```html
<ul>
</ul>
```

### **:pencil2: menu.htm 스테이징&커밋**
실습을 위해 총 6번의 커밋을 진행합니다.<br>

**첫 번째 커밋**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git add menu.htm  # 스테이징

infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "first"  # 커밋
[master (root-commit) 69bf712] first
>  1 file changed, 2 insertions(+)
>  create mode 100644 menu.htm
```
<!-------------------------------------------------------------->
<details>
<summary>

**:two: menu.htm 두 번째 커밋**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202429369-ece2797c-7f54-40af-9f4f-7de10c562b83.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am “menu1" menu1 등록 및 커밋
> [master b741eef] menu1
>  1 file changed, 1 insertion(+)
```

</details>
<!-------------------------------------------------------------->
<details>
<summary>

**:three: menu.htm 세 번째 커밋**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202429627-d4c21f7b-a9ec-4c65-94c5-13923a44e162.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu2" menu2 등록 및 커밋
> [master f1c704f] menu2
>  1 file changed, 1 insertion(+)
```
</details>
<!-------------------------------------------------------------->
<details>
<summary>

**:four: menu.htm 네 번째 커밋**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202429973-534c5c9c-3a8b-41a1-8273-40912e8c1cd9.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu3"
> [master b728366] menu3
>  1 file changed, 1 insertion(+)
```

</details>
<!-------------------------------------------------------------->
<details>
<summary>

**:five: menu.htm 다섯 번째 커밋**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202430195-9462c653-0fb3-4b7c-8fa2-22f5bffdb54e.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu4"
> [master 6619c99] menu4
>  1 file changed, 1 insertion(+)
```
</details>
<!-------------------------------------------------------------->
<details>
<summary>

**:six: menu.htm 여섯 번째 커밋**

</summary>

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/202430397-8a720549-24b7-4a30-ada2-e5e3f9d41947.jpg">
</kbd>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am “menu5" menu5 등록 및 커밋
> [master 7f068b6] menu5
>  1 file changed, 1 insertion(+)
```
</details>

### **소스트리에서 커밋 확인**
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/201471781-d76d0432-24a2-4ccc-baef-901cdc11c31b.png">
</kbd>