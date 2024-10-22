# CommonJS-모듈-TypeScript-적용-방법
## 부제: `lodash` 모듈 사용 시 생기는 문제에 대한 또 다른 해결 방법

### 개인적으로 알아낸 방법
```
"esModuleInterop": true,
"allowSyntheticDefaultImports": true
```
`tsconfig.json`파일에 `"compilerOptions"`안에 위 코드를 넣은 후, 사용하고자 하는 파일에

```
import _ from 'lodash'
```
적절한 공간에 위 코드를 써주시면 정상적인 `lodash` 사용이 가능합니다.

문제 발생 이유: `lodash`와 같은 CommonJS 모듈을 TypeScript 프로젝트에서 사용하려 할 때 이 문제가 발생합니다.

### 수업 중 해결 방법
```
import * as _ from 'lodash'
```
번거로운 설정이 없어 간단해서 매력적인 방법입니다.
