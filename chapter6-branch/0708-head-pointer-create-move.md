[목록][목록] | [이전][이전] | [다음][다음]

[목록]: README.md "목록"
[이전]: 0506-move-space.md "이전"
[다음]: 09-remote-branch.md "다음"

# **:star: HEAD 포인터**

깃은 객체의 포인터 개념을 사용하는데 대표적인 객체 포인터로 HEAD가 있다.

<br>

## **:leaves: 마지막 커밋**

 - 깃은 마지막 커밋 정보가 중요하며, 마지막 커밋 정보를 기반으로 새로운 커밋을 생성한다.
 - 깃은 마지맛 커밋을 쉽게 확인할 수 있도록 특수한 포인터를 제공하며, 이는 HEAD이다.
 - HEAD는 작업중인 브랜치의 마지막 커밋 ID를 가리키는 참조 포인터다.
 - 마지막 커밋을 가리키는 HEAD 포인터를 **부모** 커밋으로 대체하여 사용하며 HEAD를 사용하여 빠르게 스냅샷을 생성할 수 있다.
```bash
$ git log --graph --all
* commit dcdb1c1 fa4ef78bedd8dc13bc267e99391cc9782 (master)
| Author: hojin <infohojin@gmail.com>
| Date:    Sat May 11 18:45:35 2019 +0900
|       master working...
|
* commit d84766c 7f87b1d9d234050949c48681ba4e35da8 (HEAD -> footer, feature) # HAED 위치
   Author: hojin <infohojin@gmail.com>
   Date:    Sat May 11 17:10:02 2019 +0900
         first
```


<br>

## **:tophat: 브랜치 HEAD**

- **브랜치를 이동하면 HEAD 포인트로 이동된다.**
- 각각의 브랜치마다 마지막 커밋이 다르기 때문에 브랜치마다 마지막 커밋 ID를 가리키는 HEAD 포인터가 하나씩 있다.

<br>

## **:evergreen_tree: 소스트리 HEAD**

- 소스트리에서도 HEAD 포인트 상태를 쉽게 확인할 수 있다.
- 각 브랜치의 마지막 위치를 **브랜치 아이콘**으로 표시한다.
- HEAD 위치는 각 브랜드의 커밋 개수에 따라 서로 다르게 표시한다.
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194885194-1e643952-aace-4534-85ec-40ce3fd9ccfb.png">
</kbd>

<br><br>

## **:triangular_flag_on_post: 상대적 위치**

- 깃의 HEAD 포인터는 내부적으로 커밋을 생성하고 브랜치를 관리하는 데 매우 유용하다.
- 깃의 다양한 명령어를 입력할 때도 **기준점**으로 사용한다.
- 마지막 커밋 위치인 HEAD를 기준으로 상대적 커밋 위치도 지정할 수 있다.

- 상태적 커밋 위치를 지정할 때는 **캐럿(^)과 물결(~) 기호**를 같이 사용한다.

  > 예) HEAD 포인터 바로 이전의 커밋을 가리킨다면 HEAD^ 또는 HEAD~처럼 사용한다.

- HEAD를 기준으로 이전 3개 위치를 지정하고 싶다면 HEAD^^^, HEAD~~~ 처럼 사용한다.
- 하지만 더 먼 상대적 위치를 지정할 때는 기호보다는 숫자를 사용하면 더 편하다.

  > 예) HEAD^3, HEAD~4 처럼 표현한다.

<br>

## **:crown: AHEAD, BHEAD**

- 원격 저장소와 연동하여 깃을 관리한다면 브랜치마다 HEAD가 2개 있다.
- 로컬 저장소 브랜치의 HEAD 포인터와 원격 저장소 브랜치의 HEAD 포인터입니다.
- 원격 저장소와 로컬 저장소는 물리적으로 서로 다른 저장소이다.
- 따라서 두 저장소의 마지막 커밋 위치가 일치하지 않을 수 있으며 이는 서로 다른 커밋을 가리키는 HEAD 포인터를 가진다는 의미이다.
- AHEAD와 BHEAD는 서로 다른 저장소 간 HEAD 포인터의 위치 차이를 의미한다.
- 깃은 항상 원격 저장소의 HEAD와 로컬 저장소의 HEAD를 비교한다.
- 브랜치를 여러 개 운영한다면 다수의 AHEAD와 BHEAD가 생길 수 있다.
<kbd>
AHEAD<br>
<img src="https://user-images.githubusercontent.com/45596014/194892509-43371686-abc6-4c55-b093-0f674e0fbb74.jpg"><br>
BHEAD<br>
<img src="https://user-images.githubusercontent.com/45596014/194892615-86fda92c-3e14-4c4f-aa7d-1c71b0dd8d13.jpg">
</kbd>


<br>

### AHEAD

- AHEAD는 **서버로 전송되지 않은 로컬 커밋**이 있다.
- 로컬 저장소의 HEAD 포인터를 기준으로 **로컬 브랜치에 있는 커밋이 서버의 커밋 개수보다 많은 경우**이다

<br>

### BHEAD

- BHEAD는 **로컬 저장소로 내려받지 않은 커밋이 있는 것**이다.

<br>

# **:hammer: 생성과 이동**

- 깃의 브랜치를 생성하는 동작과 이동하는 동작은 별개이다.
- 브랜치 생성은 branch 명령어를 사용하고, 브랜치 이동은 checkout 명령어를 사용한다.
- 브랜치를 생성하면서 동시헤 생성된 브랜치로 이동하려면 병도의 명령을 실행해야 한다.

<br>

## **:taxi: 자동 이동 옵션**

- 깃은 브랜치 생성과 이동 명령을 한 번에 처리하는 **옵션**(-b)을 제공한다.
- 다음과 같이 체크아웃할 때 **-b 옵션**을 같이 사용하면 브랜치 생성과 이동을 한 번에 할 수 있다.

```bash
$ git checkout -b 브랜치이름
```

<br>

## **:arrow_right: 커밋 이동**

- 브랜치는 특정한 커밋에 별명을 부여한 것과 같다. 
- 일반적으로 브랜치를 생성할 때는 마지막 커밋을 기준으로 한다.
- 그리고 커밋 해시 값을 지정한 별칭으로 브랜치 목록에 등록한다.
- 이러한 동작 원리로 볼 때 **[브랜치 이름]은 [커밋 해시키]와 동일**하다.

```
$ git checkout 커밋해시키
```

<br>

## **:left_right_arrow: HEAD를 활용한 이동**

-간편하게 HEAD 포인터를 사용하여 체크아웃을 할 수도 있다.

예를 들어 바로 이전 커밋으로 체크아웃하고 싶을 때는 다음 명령을 실행한다.

```
$ git checkout HEAD~1
```
<kbd>
<img src="https://user-images.githubusercontent.com/45596014/194893129-d81cb479-7583-41c2-991c-9412583c8482.jpg">
</kbd>

<br>

## **:leftwards_arrow_with_hook: 돌아오기**

- 커밋 해시키 또는 HEAD를 사용하여 과거의 커밋으로 체크아웃했다면 다시 현재 시점으로 돌아와야 한다.
- 간단하게 돌아오는 방법은 대시(-)를 사용하는 것이다.

```
$ git checkout -
```

- 특정 브랜치로 복귀하려면

```
$ git checkout main # main 브랜치로 복귀
```

<br><br>

[이전 - 브랜치 이동 및 공간](0506-move-space.md)

<br>

[다음 - 원격 브랜치](09-remote-branch.md)

<br>

[목록](README.md)
