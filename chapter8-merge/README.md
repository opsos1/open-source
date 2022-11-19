# **:sparkles: 병합**

브랜치를 생성하여 원본 코드에 영향을 주지 않고 분리하여 개발을 하는데, 독립된 브랜치에서 <br>
개발 작업이 끝나면 분리된 브랜치를 한 브랜치로 합치는 작업을 **병합**(합치기)이라고 합니다. <br>
두 코드를 하나씩 직접 비교하는 **수동 병합**, 도구를 이용한 **자동 병합**이 있습니다.

## **:bookmark: 목차**
### [01. Fast-Forward](02-fast-forward.md)
### [02. 3way](03-3way.md)
### [03. 브랜치삭제](04-remove-branch.md)
### [04. 충돌](05-crash.md)
### [05. 병합확인](06-merge-or-not.md)
### [06. rebase](07-rebase.md)


<br>

## :wrench: 하나씩 직접 비교하는 **수동 병합**
2개의 파일을 비교하는 것도 매우 힘들고, 사람의 기억력에는 한계가 있어 <br>
며칠 동안 작업한 내용을 일일이 옮겨 적는 것은 힘든 작업입니다. <br>

하지만, 2개이상이라면 어떻게 될까요?

<kbd>
<img src="https://user-images.githubusercontent.com/105197541/199939079-753d6e75-25ee-4f80-9a61-ebfc5fdaa292.png">
</kbd>

<br>

> ※ B의 수정이 끝나면 A에 수정하고, C또한 B를 반영하여 A에 다시 수정을 반영해야하는 번거로움이 있습니다.<br>
> ※ 병합 처리를 조금 더 쉽게 하기 위해 변경된 시점을 잘 기억해 순서를 따르지 않고 병합을 한다면 코드가 엉켜 잘못 동작할 위험이 있습니다.<br>

## :bookmark: 깃으로 **자동 병합**
깃의 자동 병합은 원본을 기준으로 두 파일의 변경 이력을 비교합니다.<br>
깃의 병합은 브랜치를 기준으로, 분리된 각각의 브랜치에서 하나의 브랜치로 수정된 사항을 하나의 브랜치로 병합합니다. <br>
> ※ 단, 병합하고자 하는 브랜치는 같은 로컬 저장소에 있어야 합니다.<br>
> ※ 수동 병합 작업을 깃이 대신 처리하지만, 모든 코드를 완벽하게 처리할 수는 없습니다. <br> &nbsp; &nbsp;&nbsp;이를 **충돌**이라고 합니다.<br>

## :bow: **병합 방식**
깃의 병합은 브랜치를 기반으로 실행하며, 각 브랜치를 비교하여 자동 병합하는 형태입니다. <br>
따라서 병합을 하려면 브랜치를 만들어 브랜치 안에서 수정 작업을 해야합니다. <br><br>
깃은 병합을 위해 두 가지 기본적인 알고리즘 방식을 제공하며, 충돌 없이 병합하려면 이 두 가지 병합 방식의 차이를 알아야 합니다.<br>

- Fast-Forward 병합
- 3-Way 병합 <br>

두 방식을 실행하기 전 저장소를 생성하겠습니다.

```bash
$ cd 실습폴더
$ mkdir gitstudt08  # 새 폴더 만들기
$ cd gitstudt08  # 만든 폴더로 이동

infoh@DESKTOP MINGW64 /e/gitstudy08
$ git init  # 저장소 초기화
Initialized empty Git repository in E:/gitstudy08/.git/
```
그리고 index.htm 파일을 만들어 코드를 입력하고 저장합니다.
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ code index.htm  # VS code(Visual Studio Code) 실행
```
<kbd>
<img src="https://user-images.githubusercontent.com/105197541/199958866-186af7f7-f345-4503-8331-b6c0efe2e804.png">
</kbd>

<br>
파일을 등록하고 첫 번째 커밋을 합니다.

<br>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git add .  # 전체 파일을 등록. 추적 상태

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git commit -m "first"  # 커밋
[master (root-commit) f123d5c] first
 1 file changed, 11 insertions(+)
 create mode 100644 index.htm
```
이 과정을 그림으로 표현하면 다음과 같습니다. <br>

<img src="https://user-images.githubusercontent.com/105197541/199966331-ef2c3a82-8e52-46a2-a967-f208399d89f2.png">
</kbd>

<br>

저장소를 생성하고, 파일에 코드를 등록한 후 커밋을 한 결과입니다. <br>
> ※ 병합을 하려면 모든 브랜치는 단일 저장소에 있어야 하고, 같은 저장소에서만 병합을 할 수 있습니다.<br>
