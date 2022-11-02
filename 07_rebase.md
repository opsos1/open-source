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
4. **소스트리를 통한 결과 확인**
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
> 커밋 위치가 변경될 때 해시 값 중복을 방지하려고 새로운 커밋 해시를 생성합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/199490265-b329be1a-900a-4de7-b0f3-00a08decfd58.jpg">
</kbd>