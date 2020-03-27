# Sitio web del Grupo de trabajo COVID-19 de Mie

[![Mie COVID-19 Task Force website](https://user-images.githubusercontent.com/47916753/76599982-6f25fd00-6549-11ea-9fcb-87034c0b68a5.png)](https://mie.stopcovid19.jp)

### [日本語](./README.md) | [English](./README_EN.md) | Spanish | [Korean](./README_KO.md) | [Chinese (Taiwan)](./README_ZH_TW.md) | [Chinese (Simplified)](./README_ZH_CN.md)

## Cómo Contribuir

Todas las contribuciones son bienvenidas.!
Por favor, consulte [Cómo contribuir](./.github/CONTRIBUTING_ES.md) para obtener más detalles.

## Código de Conducta

Por favor, consulte el [Código de conducta para desarrolladores](./.github/CODE_OF_CONDUCT_ES.md) para más detalles.

## Licencia
Este software se publica bajo la [licencia MIT](./LICENSE.txt).

## Para Desarrolladoras

### Cómo Configurar Entornos

- Versión requerida de Node.js: 10.19.0 o superior

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

### Implementación en entornos de preparación y producción

Cuando se actualiza la rama `master`, los archivos HTML se construirán automáticamente en la rama de `production`,
y luego el sitio de producción (https://mie.stopcovid19.jp) también se actualizará.  
Cuando se actualiza la rama `develop`, los archivos HTML se construirán automáticamente en la rama de `dev_pages`,
y luego el sitio de producción (https://covid19-mie-dev.netlify.com/ ) también se actualizará.
