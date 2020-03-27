# 三重县 新型冠状病毒对策网


[![三重县 新型冠状病毒对策网](https://user-images.githubusercontent.com/47916753/76599982-6f25fd00-6549-11ea-9fcb-87034c0b68a5.png)](https://mie.stopcovid19.jp)

### [日本語](./README.md) | [English](./README_EN.md) | [Spanish](./README_ES.md) | [Korean](./README_KO.md) | [Chinese (Taiwan)](./README_ZH_TW.md) | Chinese (Simplified)

## 如何贡献
如果您能对 Issus 中做出各式各样的修改协助，我们将不胜感激。

详细请参照[如何贡献](./.github/CONTRIBUTING_ZH_CN.md)。


## 行动准则
详细请参照[建站行动原则](./.github/CODE_OF_CONDUCT_ZH_CN.md)。

## 授权
本软件采用[MIT授权条款](./LICENSE.txt)。

## 面向开发者信息

### 开发环境搭建

- Node.js 版本最低需求: 10.19.0以上

**使用 yarn 时**
``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev
```

**使用 docker compose 时**
```bash
# serve with hot reload at localhost:3000
$ docker-compose up --build
```

### 发布到 Staging环境以及正式环境的方法

`master` 分支更新時，自动将 `production` 分支中的HTML类(build)后发布到正式版 https://mie.stopcovid19.jp  
`develop` 分支更新時，自动将 `dev_pages` 分支中的HTML类(build)后发布到正式版 https://covid19-mie-dev.netlify.com/ 

