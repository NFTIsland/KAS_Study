KAS Intro
=============
**Klaytn**(클레이튼)은 카카오에서 개발한 암호화폐이다. 거래할 때는 **KLAY**(클레이)를 사용한다. <br>
**KAS**는 **Klaytn API Service**의 약자이다. KAS에서는 여러가지 API를 제공한다. <br>
1. Klaytn 계정 관리
    * 계정 주소 정보 조회 --> KAS Wallet API
    * 계정 밸런스(잔액) 정보 조회 --> KAS Node API
2. KLAY 토큰 관리
    * KLAY 전송 --> KAS Wallet API
    * KLAY 전송 내역 조회 --> KAS Token History API <br><br><br> 


KAS 시작해보기
=============
1. KAS 회원가입 <br> 
KAS 홈페이지 --> https://console.klaytnapi.com/ko/auth/login <br><br>
2. KAS Dashboard 모습 <br> 
<img src="./image/1. KAS Dashboard.png" width="100%" height="100%" title="KAS_Dashboard" alt="KAS_Dashboard"></img> <br><br>
3. 우선 KAS를 이용하기 위해서는 **Access Key**가 있어야 한다. Security --> Credential에서 AccessKey 생성을 클릭한다. <br> 
<img src="./image/2. Access Key Create.png" width="100%" height="100%" title="KAS_Dashboard" alt="KAS_Dashboard"></img> <br>
Access Key는 한번 잊어버리면 **복구가 불가능**하기 때문에 AccessKey 다운로드를 클릭하여 보관해두자. (JSON 형식의 파일이다.)
<img src="./image/3. Access Key Created.png" width="100%" height="100%" title="KAS_Dashboard" alt="KAS_Dashboard"></img> <br><br><br>

KAS Wallet API
=============
1. Wallet API를 사용하기 위해서는 **Klaytn Account Pool**(계정 저장소)를 생성해야 한다. Service --> Wallet --> Account Pools에서 Account Pool 생성을 클릭한다. 그리고 Account Pool 이름을 입력해준다. <br>
<img src="./image/4. Wallet Account Pools.png" width="100%" height="100%" title="KAS_Dashboard" alt="KAS_Dashboard"></img> <br>
그러면 이와 같이 KRN(KAS Resource Name)과 Resource ID가 나온다. <br><br>
2. Dashboard에서 Account를 생성할 수 있다. Account 생성 버튼을 클릭한다. 그러면 아래와 같이 Address와 생성, 수정된 시각이 표시된다. <br>
<img src="./image/5. Account Pool Account Create.png" width="100%" height="100%" title="KAS_Dashboard" alt="KAS_Dashboard"></img> <br><br>



