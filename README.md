<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

<style>
    .ul{
        text-decoration: underline;
    }
    .gray{
        color: gray;
    }
</style>
# server_summary
Git 교과서 5장 서버 내용 요약 정리
<hr>

# **서버 저장소란?**
    다른 말로는 원격 저장소라고도 하며, 로컬 즉, 사용자의 개인 pc와 같은 개인 저장소에 코드를 복제한 복제본이라고 할 수 있습니다.

### **협업 저장소란?**
깃은 규모가 큰 프로젝트들을 효율적이고, 높은 품질로 개발하기 위해 여러 개발자들이 <mark>협업할 수 있도록 만들어진 도구</mark>이고, 그렇기 때문에 협업을 위해 만들어진 <mark>깃 서버 저장소</mark>를 협업 저장소라고 합니다.<br>
><span class="gray">※ 원활한 협업을 위해 깃에서는 각 개발자들이 네트워크로부터  자유로운 환경에서 프로젝트를 이어나갈 수 있도록 <span class="ul">로컬 저장소</span>와 <span class="ul">서버 저장소</span>를 분리하는 방식을 채택하였습니다.</span>

<br>

### **연속된 작업**
사무실 PC의 로컬 저장소에서 작업한 데이터를 서버 저장소에 저장하면, 개인PC 로컬 저장소에 다운로드 받아 연속적으로 작업을 이어갈 수 있습니다.
> <span class="gray"> ※ 깃은 분산된 여러 로컬 저장소들에서 작업한 자료를 하나의 서버 저장소에 <span class="ul">하나로 통합</span>할 수 있고, 반대로 서버 저장소의 자료를 여러 로컬 저장소에 <span class="ul">복제</span>할 수 있습니다.</span><br>
<img width="450px" src="https://wac-cdn.atlassian.com/dam/jcr:e5228129-76b1-4b2c-8f10-af789f2ea6c0/03.svg?cdnVersion=540">

### **새 멤버**
기존 프로젝트에 새 멤버가 추가될 경우 <mark>해당 시점까지 작업한 소스코드의 최종 버전</mark>을 공유해야 하는데 이때, 깃의 <mark>원격 저장소 주소</mark>만 새 멤버에게 알려주면 별도로 파일을 보내줄 필요 없이 프로젝트의 이전 버전부터 최신 버전까지의 소스코드를 확인할 수 있습니다.
><span class="gray">※ 깃 서버 저장소를 통해 프로젝트에 참여한 모든 구성원에게 코드의 최종 결과물을 동기화할 수 있습니다.</span>

<br>

# **깃허브 서버 준비**
    깃 호스팅(깃허브)을 통해 직접 서버 관리할 필요 없이 쉽게 원격 저장소를 운영할 수 있습니다.

### **깃허브**
- 깃허브는 대표적인 깃 호스팅 서비스 입니다.
- 깃허브 계정만 있으면 모든 서비스는 무료로 사용할 수 있습니다.
- 개인 깃허브 계정은 깃허브 주소 뒤 /사용자이름 을 붙여주시면 됩니다.<br>
( github.com/사용자이름 )
- [깃허브 (https://github.com)](https://github.com)

### **저장소 생성**
