# :electric_plug:**자동으로 내려받기**
    push와 반대로 원격저장소에서 로컬저장소로 받아오는 방식입니다.
1. [복제(clone)](#clone-복제)
2. [내려받기(pull)](#pull-서버에서-내려받기)
>※ clone 및 pull 시 파일을 받을 로컬 주소에 위치해 있어야 하고,<br>
>해당 로컬 주소가 git과 연결되어 있어야 합니다. (git init)

<br>

## **자동 병합**
- ### 내려받은 커밋은 임시 영역에 저장합니다.
    >스테이지 영역이 아닌 원격저장소를 위한 전용 임시 브랜치가 있습니다.
- ### 내려받은 최신 커밋들은 현재 브랜치로 자동 병합 처리합니다.
- ### 자동 병합에는 pull이 있습니다.
>※ 혼자 개발하는 경우 자동 병합이 좋습니다.<br>
>※ 협업 시 자동 병합을 할 경우 가끔씩 문제가 생기기에 이때 fetch 방식을 사용합니다.

<br>

## **clone: 복제**
### 원격저장소 파일을 그대로 가져오는 방식입니다.
### **1. clone 받을 폴더로 이동**
```bash
$ cd [폴더명] # clone 파일을 보관할 폴더로 이동
$ mkdir [폴더명] # clone 받을 폴더를 생성
$ cd [폴더명] # 생성한 폴더로 이동
```
### **2. clone 받기**
```bash
$ git clone [원격저장소 주소] [로컬저장소 위치] # 저장소 파일이 한 폴더에 묶여서 저장
```
>※ clone으로 받은 파일이 자동으로 원격저장소와 연결됩니다.<br>
>※ 처음으로 서버에서 코드를 내려받을 때 사용합니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193399450-3d9c6f05-ec20-44df-81e1-70bc8ceb2d0f.jpg">
</kbd>

## **pull: 서버에서 내려받기**
### 로컬저장소에 원격저장소 파일이 있지만, 원격저장소에 최신 코드가 존재할 때<br>
### 로컬저장소로 내려받아(병합) 최신 코드 상태에서 바로 작업할 수 있습니다.

<br>

### **1. 복제 폴더 생성**
```bash
$ cd [원본 폴더 주소] # 원본 폴더가 있는 위치로 이동
$ cp -r [원본 폴더명] [복제 폴더명] # r 속성은 폴더 내부까지 복사
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193397314-02238d7c-be5f-4a96-85d5-9da1eb2cca78.jpg">
</kbd>

<br>

### **2. 원본 로컬저장소로 이동**
```bash
$ cd [원본 폴더명] # 원격저장소에 대한 파일이 저장된 로컬저장소로 이동
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193397839-475cd26a-2dbb-4e50-86cb-13dc5f76af5f.jpg">
</kbd>

<br>

### **3. 내부 파일 실행 후 수정**
```bash
$ code README.md # [README.md] 파일 [vscode]로 실행 후 파일 수정
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193397466-2c07a6ec-5228-4672-a3a4-c9c2ce4c5c88.png">
</kbd>

<br>

### **4. 수정된 파일 add & commit & push**
```bash
$ git commit -am "commit" # add 및 commit 동시 진행
$ git push origin main # origin(별칭) -> main(브랜치)
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193399066-ef9447d8-0ecc-4cb9-89a6-e960d275d2cf.jpg">
</kbd>

<br>

### **5. 복제 폴더로 이동 후 로그 확인**
```bash
$ cd ../[복제 폴더명]
$ git log # 복제 폴더에서는 4번에서 커밋한 기록이 보이지 않음
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193398918-447932e6-9220-4ba7-a494-6a0bed5bd120.jpg">
</kbd>

<br>

### **7. pull 내려받기**
```bash
$ git pull # 연결된 원격저장소 파일을 내 파일과 자동으로 병합
```
>※ pull은 원격저장소와 로컬저장소 간 커밋을 반영할 수 있습니다.<br>
>즉, 원격저장소는 로컬저장소와 원격저장소의 커밋 기록을 동기화합니다. 

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193399137-07a1cc7f-3f58-44ad-8141-f2e9e51a6096.jpg">
</kbd>

<br>

### **8. 복제 폴더 로그 다시확인**
```bash
$ git pull # 연결된 원격저장소 파일을 내 파일과 자동으로 병합
```
>※ 정상적으로 커밋이 병합된 것을 확인할 수 있습니다.

<kbd>
<img src="https://user-images.githubusercontent.com/45596014/193399256-1f6bce1e-37d9-445d-9f05-c2e68e81573b.jpg">
</kbd>

<br>

[이전으로 이동](/index/04_push.md)

<br>

[다음으로 이동](/index/06_manual-fetch.md)

<br>

[목차로 이동](/README.md)
