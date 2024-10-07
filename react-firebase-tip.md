# react FE app hosting 시 firebase 설정

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
