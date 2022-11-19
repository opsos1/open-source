[목록][목록] | [이전][이전] | [다음][다음]

[목록]: README.md "목록"
[이전]: 05-crash.md "이전"
[다음]: 07-rebase.md "다음"

# **:bulb: 브랜치 병합 여부 확인**
다수의 브랜치가 있을 때는 어렵기에 병합된 브랜치를 바로 삭제한다면 혼동을 줄일 수 있습니다. <br>

깃은 병합한 브랜치와 병합하지 않은 브랜치를 구분하는 옵션을 제공합니다. 

<br>

```bash
$ git branch --merged
```

<br>

master 브랜치에서 이 명령을 실행해 봅시다.

<br>

```bash
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git branch --merged  # 브랜치 목록
>   feature 
>   footer
> * master
```

<br>

병합한 브랜치는 별표(*) 기호로 표시됩니다. <br>
병합을 완료한 브랜치는 **-d 옵션**을 활용하여 삭제할 수 있습니다. <br>

> 8.4 브랜치 삭제에서 배운 내용 

<br> 

병합하지 않은 브랜치는 **--no-merged** 옵션으로 확인 할 수 있습니다. <br>

```bash
$ git branch --no-merged
```

<br>

> 병합하지 않은 브랜치는 -d옵션으로 삭제되지 않으므로 **-D**를 사용해서 삭제해야합니다.

<br><br>

[이전 - 충돌](05-crash.md)

<br>

[다음 - 리베이스](07-rebase.md)

<br>

[목록](README.md)
