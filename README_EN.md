# Mie Prefecture COVID-19 Task Force website

[![Mie Prefecture COVID-19 Task Force website](https://user-images.githubusercontent.com/47916753/76599982-6f25fd00-6549-11ea-9fcb-87034c0b68a5.png)](https://mie.stopcovid19.jp)

### [日本語](./README.md) | English | [Spanish](./README_ES.md) | [Korean](./README_KO.md) | [Chinese (Taiwan)](./README_ZH_TW.md) | [Chinese (Simplified)](./README_ZH_CN.md)

## How to Contribute

All contributions are welcome!
Please check [How to contribute](./.github/CONTRIBUTING_EN.md) for details.

## Code of Conduct

Please check [Code of conduct for developers](./.github/CODE_OF_CONDUCT_EN.md) for details.

## License
This software is released under [the MIT License](./LICENSE.txt).

## For Developers

### How to Set Up Environments

- Required Node.js version: 10.19.0 or higher

**Use yarn**
``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev
```

**Use docker**
```bash
# serve with hot reload at localhost:3000
$ docker-compose up --build
```

### Deployment to Staging & Production Environments

When `master` branch is updated, the HTML files will be automatically built onto `production` branch,
and then the production site (https://mie.stopcovid19.jp) will be also updated.  
When `develop` branch is updated, the HTML files will be automatically built onto `dev_pages` branch,
and then the production site (https://covid19-mie-dev.netlify.com/) will be also updated.  

