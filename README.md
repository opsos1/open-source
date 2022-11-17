# **오픈소스소프트웨어(Open Source Software)**
오픈 소스 소프트웨어의 역사와 현황
```
공개적으로 엑세스할 수 있게 설계되어, 누구나 자유롭게 확인/수정/배포가 가능한 코드입니다.
다양한 방식으로 오픈소스를 제어하는 라이선스들이 존재합니다.
```

### [**01. 오픈소스 역사**](History.md)

<br>

### [**02. 오픈소스 현행**](Current.md)

<br>

### [**03. 자료 출처**](source.md)

<br>

## **:bookmark_tabs: 오픈소스 라이선스 종류**
<details>
<summary><h4>1. Apache</h4></summary>

   아파치 소프트웨어 재단 자체적으로 만든 라이선스입니다.<br>
   - 소스코드에 대한 공개 의무 등의 의무사항은 없지만 아파치 라이선스의 소스코드를 수정하여 배포하는 경우<br>
    아파치 라이선스, 버전 2.0을 꼭 포함시켜야 하며 아파치 재단에서 만든 소프트웨어임을 밝혀야 합니다.<br>
    - 안드로이드 (v2.0) | 하둡 (v2.0)

</details>
<details>
<summary><h4>2.  GPL (GNU GPL)</h4></summary>

   자유 소프트웨어 재단(FSF)에서 만든 라이선스 입니다.<br>
   - 가장 강한 제약 조건을 포함하고 있는 카피레프트(Copyleft) 조항이 있습니다.<br>
   - GPL 프로그램은 어떤 목적으로, 어떤 형태로든 사용할 수 있지만<br>
    사용하거나 변경된 프로그램을 배포하는 경우 무조건 동일한 라이선스 즉,<br>
    GPL로 공개해야 한다는 강력한 조항이 담겨있습니다.<br>
    - Mozilla Firefox (v2.0) | Linux 커널 (v2.0) | Git (v2.0) | MariaDB (v2.0) | Wordpress (v2.0) | Drupal (v2.0)

</details>
<details>

<summary><h4>3. AGPL (GNU Affero GPL)</h4></summary>
   GPL을 기반으로 만들어진 라이선스로 자유 소프트웨어 재단(FSF)에서 만든 라이선스 입니다.<br>
   - 서버에서 프로그램을 실행하여 다른 사용자들과 통신하게 된다면,<br>
    실행되고 있는 프로그램의 소스 코드를 사용자들이 다운로드 받을 수 있게 해야 한다는 독특한 조항이 담겨있습니다.<br>
    - MongoDB

</details>
<details>
<summary><h4>4. LGPL (GNU Lesser GPL)</h4></summary>
   자유 소프트웨어 재단(FSF)의 강력한 철학이 담긴, GPL의 카피레프트 조항을 보완하기 위해 만든 라이선스입니다.<br>
   - 소라이브러리/모듈 링크를 허용한 라이선스입니다.<br>
   - Mozzilla Firefox(v2.1)
</details>
<details>
<summary><h4>5. MIT</he></summary>
   미국 매사추세츠 공과대학교(MIT)에서 해당 대학의 소프트웨어 공학도들을 돕기 위해 개발한 라이선스입니다.<br>
   - 라이선스와 저작권 관련 명시만 지켜주면 되는 조건을 가진 라이선스 입니다.<br>
   - Bootstrap | Angular.js | Backbone.js | jQurey
</details>
<details>
<summary><h4>6. Artistic</h4></summary>
   Perl 프로그래밍 언어를 사용하던 Larry Wall이 표준 펄(Perl) 기능을 위해 개발한 라이선스입니다.<br>
   - NPM(Node Pacakge Manager) (v2.0)
</details>
<details>
<summary><h4>7. Eclpse</h4></summary>
   이클립스사에서 비즈니스 환경에 적합하도록 만든 기업 친화적인 라이선스 입니다.<br>
   - 강력한 카피레프트 조항이 담긴 GPL 보다 제약 조건이 완화된 라이선스입니다.<br>
   - Eclipse (v1.0)
</details>
<details>
<summary><h4>8. BSD (Berkeley Software Distribution)</h4></summary>
   버클리의 캘리포니아 대학에서 배포하는 공개 소프트웨어의 라이선스입니다.<br>
   - 저작권 표시 조건 외 아무런 제한 없이 누구나 자신의 용도로 사용할 수 있도록 만들어 졌습니다.<br>
   - Nginx (The BSD 2-Clause License)
</details>
<details>
<summary><h4>9. MPL (Mozilla Pulbic License)</h4></summary>
   과거 넷스케이프(Netscape) 브라우저의 소스코드를 공개하기 위해 개발된 라이선스입니다.<br>
   - 소스코드와 실행파일의 저작권을 분리함으로써<br>
      수정한 소스코드의 경우 MPL로 공개하고 원저작자에게 수정한 부분에 대해 알려야 하지만<br>
      실행파일은 독점 라이선스로 배포가 가능합니다.<br>
   - Mozilla Firefox (v1.1) | Mozilla Thunderbird (v1.1)
</details>

<br>

## **:first_quarter_moon: Open Source Software VS Free Software**
### 여기서 **"오픈 소스"** 개념과 **"자유 소프트웨어"** 개념을 완전히 다른 개념입니다.
### Richard Stallman은 **"오픈 소스"** 개념보다 **"자유 소프트웨어"** 개념에 더 관심을 가졌습니다.

<br>

- ### **개념이 나뉜 이유**<br>
    Richard Stallman은 소프트웨어를 실행해서, 연구하고 변경한 후, 변경 유무에 관계 없이 재배포를 할 수 있는 것에 대해<br>
    **"가격"** 의 문제가 아닌 **"자유"** 의 문제라고 생각했기 때문입니다.

<br>


  - ### **자유 소프트웨어**<br>
      - **"독점 소프트웨어"** 를 문제로 인식합니다.<br>
      - 소프트웨어를 **"상품"** 으로 생각하지 않습니다.
        >※ 자유 소프트웨어를 지향하는 사람들에겐 [4가지 자유(Rule)](/02_History.md/#1985년-자유소프트웨어-재단-fsfhttpwwwfsforg을-조직했습니다br)가 존재합니다.<br>
    
<br>

  - ### **오픈 소스**<br>
      - 무료 뿐 아니라 **"유료"** 라는 대안이 있습니다.<br>
      - 무료 소프트웨어는 누구나 사용 가능
      - 오픈소스 프로그램은 **상업적**으로 사용 가능
      - 예로 들면 Linux 운영체제는 오픈소스와 프리(FOSS)를 모두 지원하므로 커스터마이즈 할 수 있습니다.
          >※ FOSS - 자유 및 오픈 소스 소프트웨어를 모두 일컫는 말
