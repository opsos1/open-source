# **:pencil2: 리베이스**
```
브랜치를 합치는 방법으로는 병합(merge)과 리베이스(rebase) 두 가지가 있습니다.
그중 리베이스(rebase) 는 커밋의 트리 구조를 재배열합니다.
```
> ※ 실무에서는 merge 명령어보다 리베이스를 더 선호하는 편입니다.

<br>

## :guitar: 베이스
브랜치는 커밋 하나를 기준으로 새로운 작업을 진행할 수 있는 분리된 작업 경로를 의미합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199457387-960277ba-103b-4f71-a35f-c0c586c1c5b4.jpg">
</kbd>

> ※ 그림에서 새로운 브랜치가 커밋2에서 파생되며, <br>
> &nbsp;&nbsp;&nbsp; 새로운 브랜치가 파생되는 커밋2를 **베이스(base)** 라고 합니다. <br>
> ※ 병합에서는 이를 **공통 조상 커밋** 이라고 합니다.

## **:cloud: 베이스 변경**
파생된 브랜치의 기준이 되는 **베이스 커밋**을 변경하는 것입니다.<br>
여기서 브랜치의 베이스를 변경하는 이유는 커밋의 진행 모습을 단순화하기 위함입니다. <br><br>
리베이스는 코드의 베이스 분기점을 변경하여 마치 하나의 기찻길 처럼 만듭니다.<br>
여러 갈래로 갈라지지 않아 커밋의 진행 사항을 좀 더 쉽게 파악할 수 있습니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199467429-329faee6-70bd-4fef-a00b-756ab4c4bf62.jpg">
</kbd>

<br>

## **:straight_ruler: 리베이스 vs 병합**
### **병합**
병합은 파생된 두 브랜치를 하나로 합치는 과정으로,<br>
병합하려면 두 브랜치의 공통 조상 커밋을 먼저 찾아야 합니다.<br>
공통 조상 커밋을 찾으면 서로 다르게 커밋이 진행된 두 브랜치를 3-way 방식으로 병합할 수 있습니다.
> ※ 공통 조상 커밋은 두 브랜치를 병합하는 베이스 커밋입니다.<br>
> ※ 병합하는 두 브랜치는 순차적으로 커밋을 비교하면서 마지막 최종 커밋을 생성합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199469114-6315e35a-8781-4741-9b81-7539fb4e6b93.jpg">
</kbd>

<br>

### **리베이스**
리베이스는 두 브랜치를 서로 비교하지 않고 순차적으로 커밋 병합을 시도합니다.<br>

### **리베이스에서 브랜치의 커밋을 결합하는 순서**
1. 공통 조상 커밋 찾기
2. 베이스 커밋을 변경하여 두 브랜치의 커밋 위치 바꾸기
3. 파생된 브랜치의 diff를 임시 공간에 잠시 보관
4. master 브랜치의 커밋1 -> 커밋2 -> 커밋5 -> 커밋6 까지 진행
5. 기존 베이스 커밋2에서 커밋6으로 베이스 기준점 변경
6. 변경하는 기준 브랜치의 마지막 커밋에서 차례로 임시 공간에 저장한 diff를 하나씩 적용
7. 새로운 베이스 기준점을 기반으로 한 브랜치에서 커밋3 -> 커밋4를 커밋6에서 연장하여 수정 재배치

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199472290-badc6cd0-1806-45a9-8562-ccb7b704d025.jpg">
</kbd>

### **결과**
브랜치의 커밋4는 최종 코드로 모든 코드 내용이 반영되어 있습니다.<br>
커맷4 입장에서는 두 브랜치를 병합한 결과물입니다.

리베이스 결과물을 보면 기존 병합과 두 가지 차이점이 있습니다.<br>
1. 3-way 병합은 병합 커밋이 있지만 리베이스를 하면 병합 커밋은 없습니다.
2. 브랜치의 마지막을 가리키는 커밋 위치가 다릅니다.

브랜치 A는 커밋4를 가리키지만, master 브랜치는 아직 커밋6을 가리킵니다.

<br>

## **:computer: 리베이스 명령어**
```bash
$ git rebase [브랜치]
```

### **실습**
1. **새로운 브랜치 생성 (description)**
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git checkout -b description  # 브랜치 생성
    ```
2. **description 브랜치에서 study.md 파일 수정 후 커밋**
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    $ code index.htm  # VS code 실행(수정)
    ```
    <kbd>
    <img width="300" src="https://user-images.githubusercontent.com/45596014/199481604-beb5a963-df59-40c2-86a1-0be7854a23b6.jpg">
    </kbd>

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    $ git commit -am "add description"  # 커밋
    > [description 079bdc1] add description
    >  1file changed, 1 insertion (+)
    ```
3. **다시 마스터 브랜치로 체크아웃 후 수정하여 두 번 커밋**
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    $ git checkout -b master  # 브랜치 이동
    ```

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ code index.htm  # VS code 실행(수정)

    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git commit -am "add test1"  # 첫 번째 커밋
    ```
    <kbd>
    <img width="300" src="https://user-images.githubusercontent.com/45596014/199482042-f13cd40e-bce7-4a1b-9b50-adf98cb8e8f1.jpg">
    </kbd>

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ code index.htm  # VS code 실행(수정)

    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git commit -am "add test2"  # 두 번째 커밋
    ```
    <kbd>
    <img width="300" src="https://user-images.githubusercontent.com/45596014/199483231-f145f01b-c3ef-48e2-8fb2-ec5f543b40db.jpg">
    </kbd>
4. **소스트리를 통한 결과 확인**<br>
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/199479109-42a1b25e-d2a2-4b06-96d3-17c75aff9c66.jpg">
    </kbd>

<br>
<details>
<summary>리베이스와 병합 방식 및 진행상황</summary>
## **:incoming_envelope:리베이스 병합**
리베이스는 병합 기준 브랜치가 merge 명령어와 반대입니다.<br>
merge 명령어를 사용한 병합은 현재의 기준 브랜치에서 다른 브랜치를 읽어와서 결합합니다.

**merge 방식**<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199484767-6f66283f-0f9b-42a2-956f-87462f85ca75.jpg">
</kbd>

<br>

**리베이스 방식**<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199485190-5b217dc0-8c53-49cf-8575-b2090403a3e8.jpg">
</kbd>

<br>

**현재까지 실습 과정**<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199485627-5caa825e-74d7-4983-a74e-af32dca7626a.jpg">
</kbd>
</details>

<br>

5. **리베이스를 위해 description 브랜치로 체크아웃**
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git checkout description
    > Switchec to branch 'description'

    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    ```
6. description 브랜치에서 원본 master 브랜치를 리베이스
    > ※ 파생 브랜치의 커밋들은 기준 브랜치의 마지막 커밋으로 재정렬됩니다.
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    $ git rebase master
    > First rewinding head to replay your work on top of it...
    > Applying: add description
    ```

    **소스트리 결과**<br>
    > ※ master 브랜치의 마지막 커밋 ‘add menu6’ 뒤에 파생 브랜치의 커밋이 연결된 것을 볼 수 있습니다.<br>
    > ※ 두 브랜치를 하나의 그래프 모양으로 합친 형태입니다.

    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/199487881-fa510c66-7981-40cb-a74d-4186caca7f2f.jpg">
    </kbd>

    <br>

## **:heavy_check_mark: 리베이스되었는지 확인**
베이스 커밋을 변경하는 과정에서 커밋들은 재배치 작업을 합니다.<br>
이 과정에서 커밋의 해시 값이 변경됩니다.

### **리베이스한 후 로그상태**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
$ git log -3 로그 확인

> commit 48caea016f0e330cfc1dfcd587996fa9a32042fd (HEAD -> description)
> Author: hojin <infohojin@gmail.com>
> Date:   Sat May 18 17:27:09 2019 +0900
    add description
 
> commit a7fe40bb622f6c8af0b1f25b0d86ea96c7896c50 (master)
> Author: hojin <infohojin@gmail.com>
> Date:   Sat May 18 17:28:59 2019 +0900
>     add menu6
 
> commit 8959f0cca024504cfe321adf440c9c888f8e4693
> Author: hojin <infohojin@gmail.com>
> Date:   Sat May 18 17:28:29 2019 +0900
>     add menu5
```
### **바뀐 점**
리베이스 병합 이후에 커밋 ID가 변경되었습니다.
> ※ 커밋 위치가 변경될 때 해시 값 중복을 방지하려고<br>
> &nbsp;&nbsp;&nbsp;새로운 커밋 해시를 생성합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199490265-b329be1a-900a-4de7-b0f3-00a08decfd58.jpg">
</kbd>

<br>

### **리베이스 후 브랜치**
리베이스 병합 이후 커밋은 정리되었지만, 브랜치 모양이 약간 다릅니다.<br>
<kbd>**리베이스 후 브랜치의 마지막 커밋 위치**<br>
<img src="https://user-images.githubusercontent.com/45596014/199490884-a03fed2b-8231-4cd1-8f6a-7c30935325d0.jpg">
</kbd>

<br>

일반적으로 병합을 한 후 두 브랜치는 같은 커밋 ID를 가리킵니다.<br>
하지만 소스트리에서 확인된 브랜치 위치는 서로 다릅니다.<br><br>
<kbd>**브랜치의 HEAD 포인터**<br>
<img src="https://user-images.githubusercontent.com/45596014/199491203-8b19055c-1b75-4a5f-a242-b1459eab4a3d.jpg">
</kbd>

리베이스는 `커밋 위치`를 재조정할 뿐 브랜치의 HEAD 포인터까지 옮겨 주지는 않습니다.<br>
리베이스한 후에는 이러한 병합 브랜치의 HEAD를 맞추어야 합니다.<br>
> ※ 즉, 리베이스된 브랜치를 병합해야 합니다.<br>

<br>

7. 병합을 위해 master 브랜치로 체크아웃합니다.<br>
그리고 master 브랜치에서 merge 명령어를 실행합니다.

    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (description)
    $ git checkout master  # 마스터 브랜치로 변경

    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git merge description  # HEAD 포인터 조정(병합)
    > Updating a7fe40b..48caea0
    > Fast-forward 병합 방식 확인
    >  index.htm | 1 +
    >  1 file changed, 1 insertion(+)
    ```
<kbd>**병합 후 소스트리 상태**<br>
<img src="https://user-images.githubusercontent.com/45596014/199624049-75a9cc1b-5008-4130-913f-367b0c57374c.jpg">
</kbd>

> ※ 두 브랜치 HEAD가 동일한 커밋 위치를 가리키고 있습니다.

<br>

### **리베이스 후 실행한 병합 메시지**
```bash
infoh@DESKTOP MINGW64 /e/gitsudy08 (master)
$ git branch -d description
> Deleted branch description (was 48caea0).
```
1. `Fast-Forward` 방식으로 병합했다는 것을 알 수 있습니다.
2. HEAD 포인터의 위치만 생각해 보면 master 브랜치는 추가 커밋이 없는 상태입니다.
3. 리베이스한 브랜치에만 커밋이 진행된 것처럼 보이는 것을 확인할 수 있습니다.
    > ※ 즉, 리베이스한 후 HEAD 포인터의 위치 모양은 Fast-Forward 병합을 실습할 때와 같은 형태입니다.

4. 리베이스는 커밋을 재배치만 할 뿐 실제 병합과 같은 최종 상태는 가지지 않습니다. 
    > ※ 즉, 리베이스한 후에도 HEAD 포인터를 일치하기 위해 Fast-Forward 병합을 실행해 주어야 합니다.
5. 두 브랜치의 HEAD를 일치시키는 작업까지 해야 최종 병합을 완성할 수 있습니다.
6. 리베이스 및 병합 작업까지 했다면 필요 없는 브랜치는 삭제합시다.
    > ※ 이처럼 리베이스하게 되면 복잡한 트리 모양의 구조가 아니라 선형 구조로 브랜치를 변경할 수 있습니다


<br>

## **:boom: 리베이스 충돌과 해결**
리베이스는 기준점을 변경 하며,<br>
리베이스 역시 병합 과정에서 충돌이 발생할 수 있습니다.<br>
> ※ 리베이스 충돌 또한 사용자가 직접 수동으로 해결해야 합니다.

### **브랜치 생성 및 커밋**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout -b menu  # menu 브랜치 생성 및 이동

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)
$ code index.htm  # VS code 실행(수정)

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)
$ git commit -am "edit menu5"  # 커밋
> [menu 9f0bc0d] edit menu6
>  1file changed, 5 insertions(+), 2 deletions(-)
```

<kbd>
<img height="280" src="https://user-images.githubusercontent.com/45596014/199630232-67bcee15-fafa-4735-83d9-65842088c833.jpg">
</kbd>

### **충돌 생성**
master 브랜치에서도 동일한 위치의 내용을 수정하여 충돌을 만들겠습니다.<br>
> ※ master 브랜치로 체크아웃합니다.<br>
> ※ 그리고 master 브랜치에서 index.htm 파일을 수정하고 커밋합니다. 
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)
$ git checkout master  # master 브랜치로 이동

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ code index.htm  # VS code 실행(수정)

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git commit -am "edit submenu for menu5"
> [master 93aa6eb] edit submenu for menu5
>  1 file changed, 1 insertion(+), 1 deletion(-)
```
<kbd>
<img height="250" src="https://user-images.githubusercontent.com/45596014/199629752-a6ca8809-fc0a-40fa-b38f-de1ed3317397.jpg">
</kbd>

### **현재 상태**
> ※ 서로 다른 브랜치 모양으로 분기되었습니다

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199631833-902331ae-dfac-41e0-88b3-e7cd59d8e7fc.png">
</kbd>

<br>

### **리베이스를 통한 병합**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout menu  # menu 브랜치로 이동
> Switched to branch 'menu'

infoh@DESKTOP MINGW64 /e/gitstudy08 (main)
$ git rebase master
> First, rewinding head to replay your work on top of it...
> Applying: edit menu5
> Using index info to reconstruct a base tree...
> M       index.htm
> Falling back to patching base and 3-way merge…
> Auto-merging index.htm
> CONFLICT (content): Merge conflict in index.htm  # 충돌
# 기타 에러 코드
```

<details>
<summary>세부 에러 코드</summary>

```
error: Failed to merge in the changes.
hint: Use ‘git am –show-current-patch’ to see the failed patch
Patch failed at 0001 edit menu5

Resolve all conflicts manually, mark them as resolved with
“git add/rm <conflicted_files>”, then run “git rebase –continue”.
You can instead skip this commit: run “git rebase –skip”.
To abort and get back to the state before “git rebase”, run “git rebase –abort”.
PREV
BUY
```

</details>

<br>

### **충돌 시 문제해결**
충돌을 수정한 시 rebase 명령어와 --continue 옵션을 사용합니다.

```bash
$ git rebase --continue
```

1. 코드 확인
    > ※ 앞에 배운 병합과 동일하시 충돌기호가 표시됩니다.
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (menu|REBASE 1/2)
    code index.htm  # VS code 실행
    ```
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/199634951-2ed5898e-c627-446a-98dc-0044bc61d6bf.png">
    </kbd>
2. 수정<br>
    <kbd>
    <img width="400" src="https://user-images.githubusercontent.com/45596014/199635163-739e3e11-797f-482e-9d79-959d4bbf2d9b.jpg">
    </kbd>
3. 충돌 수정 적용
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (menu|REBASE 1/2)
    $ git rebase --continue
    > Applying: edit menu5
    > Applying: edit menu6
    > Using index info to reconstruct a base tree…
    > M       index.htm
    > Falling back to patching base and 3-way merge…
    > No changes – Patch already applied.

    > infoh@DESKTOP MINGW64 /e/gitstudy08 (menu) # 충돌 해결
    ```

<br>

### **특정 커밋 충돌 제외**
- `--skip` 옵션을 사용하여 특정 커밋의 충돌을 제외할 수 있으나 추천하는 방법은 아닙니다.<br>
- 대부분 코드는 이전 코드와 많이 연결되어 있기 때문에 직접 문제를 해결하고
- --continue 옵션을 사용하여 다음 단계로 넘어가는 것이 좋습니다.<br>
- 리베이스를 취소할 경우 –-abort 옵션을 사용합니다.
    ```bash
    git rebase --abort
    ```
### 충돌 해결 후 병합
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)
$ git checkout master  # master브랜치로 변경
> Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git merge menu  # 병합, HEAD 일치시키기
> Updation 93aa6eb..690cc95
> Fast-forward
>  index.htm | 7 +++++--
>  1 file changed, 5 insertions(+), 2 deletions(-)

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git branch -d menu  # menu 브랜치 삭제
> Deleted branch menu (was 690cc95).
```

<br>

## **rebase 명령어로 커밋 수정**
rebase 명령어로 최종 커밋을 수정할 수 있습니다.
- 실제 병합은 아니지만 리베이스는 `커밋 위치` 를 재조정하여 `병합` 과 `유사한`  효과를 보입니다.<br>
- Fast-Forward 병합을 이용하여 선형 구조 형태로 브랜치 모양을 정리합니다.
> ※ `--amend` 옵션으로도 마지막 커밋을 수정할 수 있습니다.<br>
> ※ 리베이스는 커밋을 재조정하는 것 외에도 여러 커밋을 한 커밋으로 묶을 수 있습니다.<br>
> ※ 이때는 -i 옵션을 사용합니다.

### **실습**
1. 저장소 상태 확인
    > ※ 세 번 커밋해서 리베이스 했으나 커밋들의 작업이 비슷합니다.
    ```bash
    infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
    $ git log -3  # 로그 3개 확인
    > commit 690cc959dd410aad516c17c3bd1b46e3e022b2b6 (HEAD -> master)
    > Author: hojin <infohojin@gmail.com>
    > Date:   Sat May 18 18:08:28 2019 +0900
    >     edit menu5
    
    > commit 93aa6eb8ad3cf50845dd04d9b4e92838279df2b4
    > Author: hojin <infohojin@gmail.com>
    > Date:   Sat May 18 18:12:56 2019 +0900
    >     edit submenu for menu5
    
    > commit 48caea016f0e330cfc1dfcd587996fa9a32042fd
    > Author: hojin <infohojin@gmail.com>
    > Date:   Sat May 18 17:27:09 2019 +0900
    > add description
    ```
2. 커밋 묶기<br>
    메시지를 입력할 수 있는 vi 에디터를 실행하면서, <br>
    리베이스 병합할 커밋들의 정보도 자동으로 작성됩니다.
    > ※ 저장 시 다음 메시지 출력 후 커밋 3개가 커밋 하나로 변경됩니다.<br>
    > `Successfully rebased and updated refs/heads/master.`<br>
    > ※ 합친 커밋에는 새 해시 값이 부여됩니다.
    ```bash
    git rebase -i HEAD~3  # vi editer 실행
    ```
    <kbd>
    <img width="550" src="https://user-images.githubusercontent.com/45596014/199643845-7d01a1bd-72e4-4b59-b1e9-63655b94ec1d.png">
    </kbd>

    <br>

## **리베이스할 때 주의할 점**
리베이스는 **커밋 위치** 와 **해시 값** 을 변경합니다.<br>
- 저장소를 외부에 공개했다면 공개된 순간부터 커밋은 리베이스를 사용하지 않는 것이 원칙입니다.
- 리베이스는 외부로 코드를 푸시하거나 공개하기 전에 로컬에서만 실행하는 것이 좋습니다.<br>
- 외부에 공개된 커밋을 리베이스하면 커밋 위치와 해시 값이 변경되어 너무 혼란스럽습니다.<br>
- 공개된 커밋을 변경할 때는 다음 장에서 배울 revert 명령어를 사용합니다.

<br>

## **정리**
다수 개발자와 협업 시 병합과 충돌이 매우 자주 발생하기 때문에<br>
충돌 최소화하고 예방하려면 master 브랜치의 내용을<br>
자주 반영하여 병합하는 것이 좋습니다.<br>
