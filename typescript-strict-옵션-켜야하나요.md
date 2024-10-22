# `TypeScript(TS)`, strict 옵션 켜야하나요?

```
{
  "compilerOptions": {
    /* {...} */
    // "strict": true          // 엄격한 타입 검사 활성화
    /* {...} */
  },
  "include": ["src/**/*.js", "src/**/*.ts"], // 포함할 파일 경로
  "exclude": ["node_modules"]  // node_modules 폴더 제외
}
```

결론: **`"strict": true"`를 굳이 켤 필요는 없다.**
생산성이 올라간다면 켜도 되지만, 그렇지 않다면 필요는 없다.
