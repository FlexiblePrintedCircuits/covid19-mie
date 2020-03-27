# 三重県 新型冠狀病毒疫情中心


[![三重縣 新型冠狀病毒疫情中心](https://user-images.githubusercontent.com/47916753/76599982-6f25fd00-6549-11ea-9fcb-87034c0b68a5.png)](https://mie.stopcovid19.jp)

### [日本語](./README.md) | [English](./README_EN.md) | [Spanish](./README_ES.md) | [Korean](./README_KO.md) | Chinese (Taiwan) | [Chinese (Simplified)](./README_ZH_CN.md)

## 如何貢獻
如果您能對 Issus 中做出各式各樣的修正協助，我們將不勝感激。

詳情請洽[如何貢獻](./.github/CONTRIBUTING_ZH_TW.md)。


## 行動原則
詳情請洽[建立網站的行動原則](./.github/CODE_OF_CONDUCT_ZH_TW.md)。

## 授權
本軟體採[MIT授權條款](./LICENSE.txt)釋出。

## 給開發者的資訊

### 開發環境建置

- Node.js 版本最低需求: 10.19.0以上

**使用 yarn 的做法**
``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev
```

**使用 docker compose 的做法**
```bash
# serve with hot reload at localhost:3000
$ docker-compose up --build
```

### Deploy 到 Staging環境以及正式環境的方法

當 `master` 分支被更新時，HTML 檔案將會在 `production` 分支中被組建 (build)起來。然後正式版網站 https://mie.stopcovid19.jp 會被更新。  
當 `develop` 分支被更新時，HTML 檔案將會在 `dev_pages` 分支中被組建 (build)起來。然後正式版網站 https://covid19-mie-dev.netlify.com/ 會被更新。

