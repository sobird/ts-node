# ts-node
通过`node`运行一个带有`tsconfig-paths`配置的 `TypeScript` 脚本。

[![npm][npm]][npm-url]
[![Build Status][build-status]][build-status-url]
[![Install Size][size]][size-url]

<!-- Badges -->

[npm]: https://img.shields.io/npm/v/@sobird/ts-node.svg
[npm-url]: https://www.npmjs.com/package/@sobird/ts-node
[build-status]: https://img.shields.io/github/actions/workflow/status/sobird/ts-node/release-please.yml?label=CI&logo=github
[build-status-url]: https://github.com/sobird/ts-node/actions
[size]: https://packagephobia.com/badge?p=@sobird/ts-node
[size-url]: https://packagephobia.com/result?p=@sobird/ts-node



## ts-node with tsconfig-paths

安装完本包后(建议安装到全局)，配置环境变量

```sh
npm i @sobird/ts-node
# 该路径为@sobird/ts-node实际安装路径
export NODE_OPTIONS="--import=/path/to/register.js"
```
注：此配置可能会影响某些库的运行比如(vitest)

或者配置vscode的launch.json
```json
{
  // 使用 IntelliSense 了解相关属性。 
  // 悬停以查看现有属性的描述。
  // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Node.js",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "program": "${file}",
      // "preLaunchTask": "tsc:build - tsconfig.json",
      "env": {
        "NODE_OPTIONS": "--import=./node_modules/@sobird/ts-node/register.js"
      }
    }
  ]
}
```

如上配置完成后，即可通过`node`执行运行`TypeScript`文件，比如：

```ts
// test.ts
import fs from 'fs';
// tsconfig-paths
import utils from '@/utils/local'

console.log(fs, utils);
```


```sh
npm run node test.ts
```

## How to publish

### 方式一

手动通过下面的命令，进行tag发布

```sh
yarn version --patch
yarn version --minor
yarn version --major
```

### 方式二

通过 `release-please` 这个自动化Action进行发布，详见 `.github/workflows/release-please.yml` 配置

## 参考

* [约定式提交](https://www.conventionalcommits.org/zh-hans/v1.0.0/)