[목록][목록] | [이전][이전] | [다음][다음]

[목록]: README.md "목록"
[이전]: 0708-head-pointer-create-move.md "이전"
[다음]: 10-branch-push.md "다음"

# **:iphone: 원격 브랜치**
```PROPERTIES
협업을 위해서는 로컬 저장소에서 작업하고 원격 저장소에도 공유합니다.
```

## **:question: 리모트 브랜치란?**
원격 저장소에 생성한 브랜치를 **리모트 브랜치**라고 합니다.<br>
생성한 브랜치는 서버로 공유할 수 있습니다.<br>
- ### 브랜치를 새로 생성한 경우 저장소를 동기화해야 합니다.
    - 로컬저장소에서 새로운 브랜치를 생성한다고, 연결된 원격 저장소에 자동으로 브랜치가 생성되지 않습니다.<br>
    - 반대로 원격저장소에 등록된 브랜치가 자동으로 로컬저장소를 만들지 않습니다.
- ### 원격 및 로컬저장소의 이름은 보통 같습니다.
    - 서로 다른 이름으로 브랜치를 연결할 수 있습니다.
    - 두 저장소는 서로 다른 브랜치로 운영 • 관리할 수 있습니다.
- ### 리모트 브랜치는 보통 `[별칭/브랜치]` 이름 형태입니다.

<br>

## **:wrench: 원격 브랜치 준비단계**

### **1. 실습 저장소를 생성해서 저장소 주소를 확인합니다.**<br>
반드시 본인의 계정으로 로그인합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193051781-80b82c60-1940-45fb-9419-ce0c5b57860e.jpg">
</kbd>
<kbd>
<img width="800" alt="image" src="https://user-images.githubusercontent.com/45596014/194218700-61f8d275-4e1a-491b-b656-4faaf8f85ea5.jpg">
</kbd>

<br>

### **2. 로컬저장소와 원격저장소를 연결합니다.**
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194697497-74f62d65-e3e4-496d-9b49-18ba3d5920f1.jpg">
</kbd>

<br><br>

## **:compass: 브랜치 추적**
깃의 브랜치는 특정 커밋 해시 값을 가리키는 `포인터`입니다.<br>
>※ 리모트 브랜치를 원격 브랜치라고 합니다.<br>
>※ 트래킹 브랜치를 추적 브랜치라고 합니다.
1. 원격저장소의 브랜치를 가리키는 것을 브랜치 추적이라고 합니다.<br>
2. 추적 브랜치는 원격 브랜치의 마지막 커밋 해시 값을 가리킵니다.<br>
    >※ 로컬저장소는 마지막으로 연결된 리모트 브랜치의 커밋 해시 값을 항상 가지고 있습니다.
3. 이 포인터 정보는 .git/refs 폴더 안에 저장되어 있습니다.<br>
4. 트래킹 브랜치는 원격 브랜치를 가리키는 북마크와 같습니다.<br>
5. 로컬저장소가 원격저장소와 연결될 때, 원격 브랜치의 트래킹 정보는 자동으로 갱신됩니다.<br>


<br>

## **:outbox_tray: 브랜치 업로드**
로컬저장소에만 브랜치를 생성했고, 이 브랜치는 원격저장소에 자동 등록되지 않습니다.
>※ 원격 저장소를 `등록`만 했기 때문에 아직 리모트 브랜치는 없습니다.<br>
>※ 리모트 브랜치는 서버 간에 통신한 후에 생성됩니다.
### **1. 원격저장소 리모트 브랜치 확인**
```bash
$ git remote show origin # origin은 원격 브랜치명
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194697582-415551ff-3904-486a-9998-6eec36d51f8d.jpg">
</kbd>

<br>

### **2. 원격저장소 동기화**
push를 하게 되면 원격저장소는 로컬저장소와 동일한 branch를 생성하게 됩니다.
>※ 원격저장소는 첫 생성 시 브랜치가 없는 상태입니다.
```bash
$ git push origin main # origin은 원격저장소 별칭, main은 브랜치 이름
```
<img src="https://user-images.githubusercontent.com/45596014/194697605-2918999e-daf2-4fb0-8aa3-203941daac06.jpg">

### **3. 브랜치 확인**
3-1. 깃허브에서 해당 저장소의 브랜치를 확인합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194325158-aafa553a-4ac8-453e-b514-d4ed248a9665.jpg">
</kbd>

<br><br>

3-2. 다시 현재 로컬저장소의 브랜치를 확인합니다.
>※ 실습을 위해 main 브랜치 외 3개 브랜치가 생성된 상태입니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194698116-3d7418f5-680e-44b0-ac01-f48a8d866c1c.jpg">
</kbd>

<br>

### **3. 브랜치 업로드**
원격저장소에 새로운 브랜치를 생성하려면 로컬저장소에서 브랜치 전송 명령을 실행해주어야 합니다.<br>
>※ [2번](#2-원격저장소-동기화)과 동일하며, 브랜치 이름만 변경합니다.

<kbd>
<img height="230" src="https://user-images.githubusercontent.com/45596014/194698253-0a067b1d-8977-4b10-8ff9-99d33a8696bf.jpg">
<img height="230" src="https://user-images.githubusercontent.com/45596014/194335536-47480706-3a05-47fb-bb89-c5c7ac388bf3.jpg">
</kbd>

<br><br>

## **:bookmark: 이름이 다른 브랜치**
로컬저장소와 원격저장소의 브랜치 이름을 동일하게 사용하기 어려울 때가 있습니다.<br>
>※ 다른 개발자가 만든 원격 서버의 브랜치를 테스트할 때<br>
>&nbsp;&nbsp;&nbsp;&nbsp;자신의 브랜치 이름과 동일하면 충돌이 생기게 됩니다.

### 브랜치를 수동으로 지정할 때, 콜론(:)으로 구분합니다.
```bash
$ git push origin 브랜치이름:새로운브랜치 # "현재브랜치"를 서버(origin)의 "새로운브랜치" 이름으로 전송
```

<kbd>
<img height="230" src="https://user-images.githubusercontent.com/45596014/194698329-a0698858-5c0c-4bc0-be94-db7bd2220bda.jpg">
<img height="230" src="https://user-images.githubusercontent.com/45596014/194715583-8dc43a10-e2cc-46f4-9a97-8f922b213bc1.jpg">
</kbd>

<br><br>

## **:metro: 업스트림 트래킹**
로컬저장소의 브랜치와 원격장소의 브랜치는 업로드할 수 있도록 `매칭`되어있습니다.<br>
이러한 `매칭을 업스트림 트래킹`이라고 합니다.
>※ 업스트림(upstream)은 브랜치 추적을 다르게 표현한 것입니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194715633-84da9ee4-cc2f-44b7-89ab-40bf990826a1.jpg">
</kbd>

### **실습하기**
리모트 브랜치와 로컬 브랜치를 연결해주는 중간 다리 역할을 합니다.<br>
clone 명령어를 통해 저장소를 복제할 때 원격 저장소에 등록된 트래킹 브랜치들을 자동으로 함께 설정합니다.<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194715681-05ec8dc3-085e-4418-bdf8-aa80182f9d0e.jpg">
</kbd>

### 1. 원격저장소를 복제 저장소로 clone 합니다.<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194691886-802e1dfa-eee6-4e71-a8a1-427f4006e117.jpg">
</kbd>

### 2. 복사된 저장소의 브랜치를 확인하기
clone은 원격 저장소의 모든 브랜치 정보를 한 번에 다 가져오지 않습니다.<br>
>※ 복제 시 하나의 트래킹 브랜치만 가져옵니다.<br>
>※ 그 이유는 불필요한 브랜치를 한 번에 가져오는 것이 효율성에서 떨어지기 때문입니다.
```bash
$ git branch -v # 로컬저장소의 브랜치 목록 확인
$ git branch -r # 원격저장소의 브랜치 목록 확인
$ git branch -a # 모든 브랜치 목록 확인
$ git branch -vv # vv 속성 - 트래킹 브랜치 정보 확인
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194714635-d05a96cc-5c26-4ea9-8772-819a0eb2cc88.jpg">
</kbd>

<br>

### 3. 복제된 저장소에 새로운 업스트림 만들기<br>
다른 브랜치를 pull 받아 트래킹 브랜치를 활성화하거나, 직접 트래킹 브랜치를 지정할 수 있습니다.
- 업스트림 동작을 위한 트래킹 브랜치는 직접 명령어를 실행하여 생성할 수 있습니다.
    >※ [이전](#bookmark-이름이-다른-브랜치)에 feature 브랜치를 function 브랜치로 등록했습니다.
```bash
$ git checkout --track origin/브랜치이름 # 업스트림 브랜치 생성
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194698703-1656dffc-4ee0-4e8c-ac0c-106a68f7385d.jpg">
</kbd>

<br>

### 4. 커밋 후 트래킹 브랜치 확인<br>
브랜치 정보에 ahead 1이 표시되는데, 원격 저장소로 전송되지 않은 커밋을 의미합니다.
```bash
$ echo test > README.md # test.md에 test내용 덮어쓰기
$ git commit -am "copy commit" # 커밋
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194698931-5a422fb3-bd7a-4f33-833d-4f95608d8d3a.jpg">
</kbd>

### 5. 커밋 전송<br>
```bash
$ git push
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194699031-b0c8c226-80bc-4c2e-b319-57249d947428.jpg">
</kbd>

### 6.  원본 저장소로 이동 후 확인
원본저장소의 브랜치를 feature로 바꾸고 pull을 하게 되면,<br>
원본저장소의 트래킹 브랜치에 따라 `원격저장소의 function 브랜치`가<br>
`원본저장소의 feature 브랜치`로 pull 됩니다.
```bash
$ cd ../study # 원본 저장소로 이동
$ git checkout feature # 브랜치 변경
$ git pull # 원격 저장소에서 내려받기
$ cat test.md # 내용 확인
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194699136-baebee16-ae1a-4bfe-bea6-3269ec989034.jpg">
</kbd>

<br>

## **:clipboard: 원격 브랜치 복사**
원격저장소의 리모트 브랜치를 통해 로컬 저장소에도 새로운 브랜치를 생성해 동기화할 수 있습니다.<br>
>※ 로컬저장소와 원격저장소의 브랜치 목록은 서로 다를 수 있습니다.
```bash
$ git checkout -b [새 이름] origin/브랜치이름
```

### 1. 브랜치 생성<br>
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194694836-e44ed6e5-1b1e-493b-b15c-66a3b007cd8e.jpg">
<img src="https://user-images.githubusercontent.com/45596014/194694906-acb13f92-6dbe-44f5-87c2-3d823fbcd276.jpg">
</kbd>

### 2. 원격저장소의 브랜치 정보 로컬저장소로 가져오기
```bash
$ git fetch # 브랜치 커밋 가져오기
$ git branch -r # 원격 브랜치 확인
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194699534-022b56cb-9c56-4c4a-9b50-e8604859ec20.jpg">
<img src="https://user-images.githubusercontent.com/45596014/194695331-a929673a-7ad8-4547-87d6-dbfddd092a2f.png">
</kbd>
    
### 3. 원격 브랜치 기반으로 로컬 브랜치 생성<br>
origin/aaa 리모트 브랜치를 기반으로 로컬저장소에 aaa 브랜치를 생성합니다.
```bash
$ git checkout -b aaa origin/aaa # 브랜치 생성 및 이동
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194715314-7430295e-87c7-43be-b05f-3303fd809acc.jpg">
</kbd>

### 4. 파일 수정 후 commit & push
파일을 수정하고, push를 통해 해당 커밋을 원격저장소의 aaa 브랜치로 저장합니다. 
```bash
$ echo 'test aaa' > README.md
$ git commit -am "test aaa"
$ git branch -vv
$ git push
```

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194715401-45e85d1f-37a5-45af-9ce3-a7ab3b7847f3.jpg">
<img src="https://user-images.githubusercontent.com/45596014/194701513-45d8c899-2f62-4854-8448-8313cabc32e7.jpg">
</kbd>

<br><br>

## **:link: 업스트림 연결**
기존 브랜치를 업스트림으로 직접 설정이 가능합니다.
>※ 업스트림을 직접 설정하면 원격 저장소로 트래킹 브랜치가 설정됩니다.
```bash
$ git branch -u origin/브랜치이름 # u 옵션 - [--set-upstream-to]의 약자
```

1. 브랜치 생성
    bbb라는 이름의 브랜치를 생성합니다.

    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/194700238-04eede0d-2c6b-452e-b4c7-a24ad8a6e7d3.png">
    </kbd>

2. 서버의 브랜치 정보 갱신
    원격저장소에서 새로 추가된 브랜치를 로컬 저장소에 갱신합니다.
    ```bash
    $ git fetch # 브랜치 갱신
    $ git branch -r # 원격 브랜치 조회
    ```
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/194700426-f9b9edce-fb2d-47a6-9793-2b6c23ddc827.jpg">
    </kbd>

3. bbb 브랜치와 연결할 수 있는 새 브랜치 생성

    ```bash
    $ git checkout -b bug # bug 브랜치 생성
    $ git branch -vv # 리모트 브랜치 조회
    ```
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/194715048-19b37209-7da4-451c-9442-ca9896247944.jpg">
    </kbd>
4. bbb에 대한 bug 업스트림 설정
    로컬저장소의 bug 브랜치가 원격저장소의 bbb 리모트 브랜치의 트래킹 브랜치로 업스트림 되었습니다.
    ```bash
    $ git branch -u origin/bbb # 업스트림 연결
    $ git branch -vv # 리모트 브랜치 조회
    ```
    
    <kbd>
    <img src="https://user-images.githubusercontent.com/45596014/194715214-4e955dd4-79f5-4c99-a952-6db7e83650aa.jpg">
    </kbd>

<br><br>

[이전 - HEAD 포인터 & 생성과 이동](0708-head-pointer-create-move.md)

<br>

[다음 - 브랜치 전송](10-branch-push.md)

<br>

[목록](README.md)
