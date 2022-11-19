[목록][목록] | [이전][이전] | [다음][다음]

[목록]: README.md "목록"
[다음]: 03-3way.md "다음"

### 목차
1. Fast-Foward 병합
2. 브랜치 생성과 수정 작업
3. 병합 위치
4. Fast-Foward 병합 적용

# **:hourglass: Fast-Foward 병합**
Fast-Foward란 깃의 가장 간단한 브랜치 병합 방식임<br>
브랜치가 분기되지만 전체 커밋 그림으로 보면 모든 변경 사항은 순자척으로 진행됨<br>
이러한 순차적 커밋에 맞추어 병합을 처리하는 방법이 **Fast-Foward병합**임

## **:pencil2: 브랜치 생성과 수정 작업**
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git branch feature  # 브랜치 생성
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout feature  # 브랜치 이동
  
Switched to branch 'feature'<p>
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
```
포인터를 확인 할 수 있는 rev-parse 명렁어를 확인해 보면 첫번째 커밋 값(f123d5c)이 동일함<br>
![image](https://user-images.githubusercontent.com/105197487/200282071-2055c5cc-16c7-44e7-b6ab-a8da770be627.jpg)<br>
소스트리에서 브랜치 위치 확인 후 생성한 feature 브랜치 안에 있는 index.htm 파일을 수정함<br>
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ code index.htm  # VS Code 실행
```
```html         
<!DOCTYPE html>
  <html>
  <head>
    <meta charset="utf-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Page Title</title>
</head>
```
위 코드에 <header></header> 태그를 삽입하고 저장함 . 기존 코드를 수정했기 때문에 파일 상태는 modified로 변경됨<br>
다음과 같이 수정할 파일을 커밋<br>
```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git commit -am "add header"
[feature 3f7799f] add header
 1 file changed, 2 insertions(+)
```
몇번의 수정과 커밋을 하고 난 후 소스트리에서 브랜치를 확인하게 되면 브랜치가 일직선으로 1개만 있음.<br>
서로 다른 브랜치이지만 순차적으로 커밋을 했기 때문에 일직선으로 보이는것인데 이러한 모양의 브랜치에서 병합 작업을 할 때는 **Fast-Foward 방식의 알고리즘**이 적용됨.
### **:compass: 병합 위치**
깃의 merge 명렁어는 브랜치를 병합함.<br>
merge 명렁어는 현재 브랜치를 기준으로 다른 브랜치의 모든 커밋을 병합함.<br>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git checkout master  # 기준 브랜치로 이동
> Switched to branch 'master'
> infoh@DESKTOP MINGW64 /e/gitstudy08 (master) 
```

병합을 할 수 있게 기준 브랜치로 이동<br>
master 브랜치로 체크아웃한 상태에서 파일(코드)을 확인해보면 feature 브랜치에서 작업한 내용이 사라짐<br>
### Fast-Foward 병합적용<br>
커밋 작업은 분기된 feature 브랜치에서 모두 수행함. 그러나 아직 master 브랜치에서는 추가된 커밋이 없음.<br>
이러한 상태에서 두 브랜치를 병합함.<br>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git merge feature  # feature 브랜치를 병함
> Updating f123d5c..7caf5f0<p>
> Fast-forward  # 병합 방식 표시
> index.htm | 6 ++++++
> 1 file changed, 6 insertions(+)
```
    
feature 브랜치의 커밋을 master 브랜치에 병함함.<br>
병합 메시지를 확인해보면 Fast-Foward 방식을 사용하여 병합했다고 출력이 됨<br>
Fast-Foward 병합은 작업한 브랜치를 원본 브랜치에 병합할 때 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가르킴.<br>
또 Fast-Foward 병합은 병합할 하나의 브랜치 파일을 기준 브랜치로 복사하여 수정된 파일을 원본에 그대로 적용한 것과 같다.<br>
이는 단순히 커밋 위치를 최신으로 옮기는 것과 비슷함.<br>

<br><br>

[다음 - 3way 병합](03-3way.md)

<br>

[목록](README.md)