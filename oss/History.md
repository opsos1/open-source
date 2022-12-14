# **오픈소스의 역사**

## **:seedling: 초기 오픈소스 (1950~1960)**
1950~60년대 소프트웨어는 사용하는 하드웨어에 따라 실행이 되지 않는 경우가 많고,<br>
각종 버그들의 수정, 기능 추가 등의 이유로 오픈소스를 사용하였습니다.

<br>

## **IBM (1950)**
IBM의 대부분의 소프트웨어들이 소스코드와 함께 배포되었고,<br>
사용자들이 SHARE, DECUS와 같은 그룹을 형성해 소프트웨어를 교환했습니다.
>※ 당시엔 소프트웨어의 **비용을 낮추고 더 많은 프로그램**을 제공하는 것이 하드웨어 회사들의 경쟁력이었습니다.<br>
>※ 1983년에 들어, IBM은 더 이상 소스코드를 배포하지 않겠다고 발표했습니다.

<kbd><a href="https://www.ibm.com/">
<img width="300" src="https://user-images.githubusercontent.com/45596014/193438499-1b58f81b-a84c-422a-b8b8-b03375fffb8c.jpg">
</a></kbd>

<br>

## **ADR (1965)**
- 1965년 ADR은 하드웨어 제조사와 **독립적으로 라이선스** 된 최초의 소프트웨어 **"제품"** 을 개발했습니다.
- 1968년에 그들의 소프트웨어에 대한 특허를 출원했습니다.
>※ 이때부터 소프트웨어를 **"프로그램 제품"** 으로 인식했습니다.<br>
>※ 제한된 라이선스로 판매되는 소프트웨어들이 증가했습니다.
    
<br>

## **:triangular_flag_on_post: 오픈소스/자유 소프트웨어 운동 (1983)**
### **1970년대 후반 ~ 1980년대 초 저작권 기술 및 독점 소프트웨어**에 대한 **대응**에서 시작되었습니다.
- ### 오픈소스(자유 소프트웨어) 운동의 시작
  - 당시 기술 및 소프트웨어는 매우 비쌌고, 이로인해 잠재적 사용자들을 고립시켰습니다.
  - 소프트웨어 저작권과 돈 때문에 분쟁에 시달리는 것을 본 리차드 스톨만은 이 현상을 지극히 잘못된 일이라고 주장했습니다.

<br>

## **GNU (1983)**
### **"모두가 공유할 수 있는 소프트웨어"** 를 목표로 한 프로젝트입니다.
  - 1983년 MIT 프로그래머인 **리차드 스톨만**에 의해 [GNU 프로젝트](https://www.gnu.org)가 시작되었습니다.
  - 소프트웨어 상업화에 반대하고, 소프트웨어 개발 초기의 **"상호협력적"** 인 문화로 돌아갈 것을 주장했습니다.<br> 
  - 누구나 GNU의 소프트웨어를 가져다 수정할 수 있고 재배포 할 수 있습니다.     
  - 1985년 [자유소프트웨어 재단 (FSF)](http://www.fsf.org)을 조직했습니다.<br>
      동시에 GNU 선언문을 재정했습니다. ( 4가지 자유 )
      ```properties
      1.  프로그램을 어떠한 목적을 위해서도 실행할 수 있는 자유
      2.  프로그램의 작동 원리를 연구하고 이를 자신의 필요에 맞게 변경시킬 수 있는 자유
      3.  이웃을 돕기 위해서 프로그램을 복제하고 배포할 수 있는 자유
      4.  프로그램을 향상시키고 이를 공동체 전체의 이익을 위해서 다시 환원시킬 수 있는 자유
      ```
      #[네 가지 자유에 대한 자료](https://www.gnu.org/philosophy/free-sw.html)

  - C 컴파일러([GCC](https://gcc.gnu.org/)), 텍스트 에디터([GNU Emacs](https://www.gnu.org/software/emacs/))와 같은 뛰어난 소프트웨어들을 만들었습니다.

  <kbd><a href="https://www.gnu.org/">
  <img width="200" src="https://user-images.githubusercontent.com/45596014/193442844-69c7f91b-48ca-4d26-b124-c12f1d544548.png">
  </a></kbd>
    
<br>
<br>

## **GPL (1989)**
### [GPL](https://www.gnu.org/licenses/gpl-3.0.html)은 GNU 일반 공용 라이선스라고도 하며, [네 가지 자유](https://www.gnu.org/philosophy/free-sw.html)를 보장하는 무료 소프트웨어 라이선스 입니다.
- GNU 프로젝트를 위해 리차드 스톨만이 작성했습니다.
- GPL 라이선스를 가진 대표적인 프로그램으로 Linux 커널과 GCC가 있습니다.
- GPL의 약화된 버전으로 1991년 [LGPL](https://www.gnu.org/licenses/lgpl-3.0.html)이 생겼습니다.
- GPL에는 3가지 버전이 있고, 각 버전에 따라 대표적인 제약이 존재합니다.
    - GPL_v1 (1989)
      1. 소스코드를 공개하지 않은 채 배포하는 것을 막기 위해, 이해하기 쉬운 코드를 같이 배포해야 합니다.<br>
      2. 프로그램에 추가적인 제약을 거는 것을 막기 위해, GPL v1 프로그램을 수정한 프로그램도 마찬가지로 GPL v1을 따라야 합니다.
      
    - GPL_v2 (1991)
      3. GPL_v1 과 다르게 소스 코드 공개가 불가능 하다면, 실행 바이너리 프로그램 조차 배포할 수 없습니다.
   
    - GPL_v3 (2007)
      4. 소프트웨어 특허에 대처<br>
      5. 다른 라이선스와의 호환성<br>
      6. 어떤 부분의 소스 코드와 무엇이 GPL이 포함되어야 하는 소스 코드를 구성하는지<br>
      7. 디지털 제한 관리
<br>

## **Linux (1991)**
  - 1991년 리누스 토발즈가 개발한 커널(OS)입니다.
  - 이태까지 커널이 개발되지 않았던 GNU에게 있어 Linux는 GNU 소프트웨어들에게 매우 인기 있었습니다.
  - Linux 와 GNU를 합쳐 Lignux라는 단어를 사용했지만, 이후 GNU/Linux로 대체되었습니다.<br>

  <kbd><a href="https://www.linux.org/">
  <img width="200" src="https://user-images.githubusercontent.com/45596014/193441162-dcfc7a26-e27d-4878-a3f2-641beb4a1baa.svg">
  </a></kbd>

<br>
<br>

## **오픈소스의 탄생 (1998)**
1998 1월 [넷스케이프](https://isp.netscape.com/)의 네비게이터에 관한 소스코드 배포에 관해<br>
자유 소프트웨어 재단은 전략 회의를 열었습니다.

이 회의에서 에릭 레이먼드 외 6명이 제안한 오픈소스라는 단어를 채택하였고,<br>
자유 소프트웨어 운동의 개척자인 리차드 스톨만도 이 단어를 쓰기로 결정했습니다.
>레이먼드와 다른 사람들은 자유소프트웨어가 가지고있던 공짜(free)같은<br>
>부정적인 의미를 벗어날수 있는 기회로 여기고 이 단어를 널리 알리는데 힘썼습니다.

<kbd><a href="https://opensource.org/">
<img width="200" src="https://opensource.org/sites/default/files/public/osi_keyhole_300X300_90ppi_0.png">
</a></kbd>

<br>

## **GIT**
Git은 2005년에 리누스 토발즈에 의해 만들어진 가장 인기있는 DVCS 입니다.
>Distributed Version Control Systems - 분산 버전 관리 시스템

Git이 개발되기 전, 일부 리눅스 커널 개발자는 [BitKeeper](https://www.bitkeeper.org/)라는 사유 DVCS를 사용했었는데,<br>
비트 키퍼를 개발한 BitMover 회사가 2005년에 특정 커널 개발자에게 부여한 무료 라이선스를 취소했습니다.

비트 키퍼 라이선스가 없어진 후 리누스 토발즈는 그 만의 DVCS를 만들기로 했습니다.(Git)<br>
이후 여러 개발자의 도움으로 Git이 성장했고, 현재는 Junio Hamano에 의해 유지되고 있습니다.

추후 DVCS 호스팅 사이트(Github)들로 인해 자유 소프트웨어 프로젝트 참여의 장벽을 점차 허물었습니다.<br>

<kbd>
<img width="200" src="https://user-images.githubusercontent.com/45596014/193445177-8c35e21e-d7df-46a7-a824-48176bcb97be.png">
<img width="200" src="https://user-images.githubusercontent.com/45596014/193445230-a7d0b836-9ca4-4ffc-81c2-d73889916e1e.png">
</kbd>

<br><br>

[다음 - 오픈소스 소프트웨어 현황](Current.md)

<br>

[목차](README.md)
