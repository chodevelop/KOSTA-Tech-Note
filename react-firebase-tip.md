# React FE app hosting 시 firebase 설정

### firebase에는 build 파일을 올려야 합니다.

```
npm run build
```
react App에 이거 돌려주면 build 파일 나오는데 이거에 연동을 해야 정상 작동합니다.

### firebase.json
```
{
  "hosting": {
    "public": "build",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```
이걸로 덮어쓰기 하세요.

### Firebase API Key 값 관리 방법
`src/index.js`에 apikey 값을 복붙해주는 게 정배입니다(실질적으로 APP의 엔트리포인트이기 때문임!)
```
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "뭉탱이",
  authDomain: "뭉탱이.com",
  projectId: "뭉탱이",
  storageBucket: "뭉탱이.com",
  messagingSenderId: "뭉탱2(연속숫자)",
  appId: "뭉탱:app:이"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```
대충 이런 내용일텐데

```
const firebaseConfig = {
  apiKey: "뭉탱이",
  authDomain: "뭉탱이.com",
  projectId: "뭉탱이",
  storageBucket: "뭉탱이.com",
  messagingSenderId: "뭉탱2(연속숫자)",
  appId: "뭉탱:app:이"
};
```
이 내용은 민감한 정보이기에 따로 환경변수로 관리해 줄 필요가 있음.
`src`에 `.env` 생성한 다음, react app 상위 디렉터리 어딘가 있는 `.gitignore` 찾아서,
```
.env
```
입력해서 API KEY가 github에 올라가는 불상사를 막고 그 다음에는 `.env`로 들어가서
```
REACT_APP_apiKey="뭉탱이"
REACT_APP_authDomain="뭉탱이.com"
REACT_APP_projectId="뭉탱이"
REACT_APP_storageBucket="뭉탱이.com"
REACT_APP_messagingSenderId="뭉탱2(연속숫자)"
REACT_APP_appId="뭉탱:app:이"
```
이런식으로 바꿔준 다음에 `src/index.js`로 돌아가서

```
const firebaseConfig = {
  apiKey: "뭉탱이",
  authDomain: "뭉탱이.com",
  projectId: "뭉탱이",
  storageBucket: "뭉탱이.com",
  messagingSenderId: "뭉탱2(연속숫자)",
  appId: "뭉탱:app:이"
};
```
위 코드를
```
const firebaseConfig = {
  apiKey: process.env.REACT_APP_apiKey,
  authDomain: process.env.REACT_APP_authDomain,
  projectId: process.env.REACT_APP_projectId,
  storageBucket: process.env.REACT_APP_storageBucket,
  messagingSenderId: process.env.REACT_APP_messagingSenderId,
  appId: process.env.REACT_APP_appId
};
```
로 환경변수를 137퍼 싹싹김치로 활용하는 코드로 탈바꿈 야무지게 조져주면 된다. 여하튼 코드 다 쌌으면 아래 코드로 빌드해주는 거 잊지 말고.
```
npm run build
```
그 다음에는 바로 deploy 조@져주면 그만 끝이라 이 말이다.
```
firebase deploy --only hosting
```
