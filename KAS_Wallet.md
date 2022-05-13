KAS Wallet API
=============
Wallet API 주소 --> https://refs.klaytnapi.com/ko/wallet/latest
1. Wallet API를 사용하기 위해서는 **Klaytn Account Pool**(계정 저장소)를 생성해야 한다. Service --> Wallet --> Account Pools에서 Account Pool 생성을 클릭한다. 그리고 Account Pool 이름을 입력해준다. <br>
<img src="./image/5. Wallet Account Pools.png" width="100%" height="100%" title="Wallet_Account_Pools" alt="Wallet_Account_Pools"></img> <br>
그러면 이와 같이 KRN(KAS Resource Name)과 Resource ID가 나온다. <br><br>
2. Dashboard에서 Account를 생성할 수 있다. Account 생성 버튼을 클릭한다. 그러면 아래와 같이 Address와 생성, 수정된 시각이 표시된다. <br>
<img src="./image/6. Account Pool Account Create.png" width="100%" height="100%" title="Account_Pool_Account_Create" alt="Account_Pool_Account_Create"></img> <br><br><br>


KAS 계정 목록 조회
=============
1. API를 이용해 생성한 계정을 조회해보자. 계정을 조회하는 API는 아래와 같다. <br>
<img src="./image/7. Wallet API Retrieve Account.png" width="100%" height="100%" title="Wallet_API_Retrieve_Account" alt="Wallet_API_Retrieve_Account"></img> <br>
사진에 나와있듯이 **basic**과 **x-chain-id**를 요구하고 있다. basic은 아래와 같이 **access key ID**와 **secret access key**를 요구한다. <br>
<img src="./image/8. Basic.png" width="100%" height="100%" title="Basic" alt="Basic"></img> <br><br>

2. 앞에서 AccessKey 다운로드를 했다면 JSON 형식의 파일이 있을 것이다. 해당 파일에는 아래와 같이 **accessKeyId**와 **secretAccessKey**가 들어있다. (뒤에 authorization이 있는데 지금은 신경쓸 필요 없다.)  <br>
<img src="./image/9. JSON File.png" width="100%" height="100%" title="JSON_File" alt="JSON_File"></img> <br>

3. **x-chain-id**는 Klaytn Chain 네트워크 ID로 **1001** 또는 **8217**을 입력한다. Baobab의 경우 1001, Cypress의 경우 8217을 입력하는데 여기에서는 테스트넷(즉, Baobab)을 사용하므로 1001을 입력한다.

4. 그렇다면 이를 이용해 계정 목록을 조회해보자. 우선 API 사용을 편리하게 하게 위해 **Stoplight Studio**를 설치하자. 그리고 Wallet API 주소로 들어가서 맨 처음에 Download OpenAPI specification 옆에 있는 Download 버튼을 클릭하여 **wallet-api.json**을 다운로드한다. 그리고 이 json 파일을 Stoplight Studio에서 오픈한다. <br>

5. 아래에 /v2/account에서 GET을 클릭해보면 아래와 같은 화면이 나온다.
<img src="./image/10. Use Wallet API 1.png" width="100%" height="100%" title="Use_Wallet_API_1" alt="Use_Wallet_API_1"></img> <br>
Username, Password, 그리고 x-chain-id를 입력할 수 있다. Username에는 accessKeyId, Password에는 secretAccessKey, 그리고 x-chain-id에는 1001을 입력한다. 다 입력했다면 아래에 있는 Send API Request를 클릭해보자. 그러면 아래와 같이 accessKeyId, secretAccessKey, x-chain-id에 해당하는 계정 목록이 출력되는 것을 확인할 수 있다. <br> 
<img src="./image/11. Use Wallet API 2.png" width="100%" height="100%" title="Use_Wallet_API_2" alt="Use_Wallet_API_2"></img> <br><br>

6. 이번에는 **Node.js**에서 API를 호출해보자. 오른쪽 아래에 있는 **Request/Sample**에서 Node --> Native를 클릭하면 그 아래에 sample code가 나온다.
<img src="./image/12. Use Wallet API 3.png" width="100%" height="100%" title="Use_Wallet_API_3" alt="Use_Wallet_API_3"></img> <br><br>
아래는 그 sample code이다.

```js
const http = require("https");

const options = {
  "method": "GET",
  "hostname": "wallet-api.klaytnapi.com",
  "port": null,
  "path": "/v2/account",
  "headers": {
    "Content-Type": "application/json",
    "x-chain-id": "1001",
    "Authorization": "Basic "
  }
};

const req = http.request(options, function (res) {
  const chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    const body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

sample code를 .js 파일에 입력하고 cmd 창에서 node (파일이름).js를 입력하면 앞과 마찬가지의 결과를 얻을 수 있다.
<img src="./image/13. cmd api.png" width="100%" height="100%" title="cmd_api" alt="cmd_api"></img> <br><br>

