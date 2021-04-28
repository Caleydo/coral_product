coral_product [![Phovea][phovea-image]][phovea-url] [![CircleCI](https://circleci.com/gh/Caleydo/coral_product.svg?style=svg)](https://circleci.com/gh/Caleydo/coral_product)
=====================

This repository describes the following deployments:

| branch          | app                                          |
|-----------------|----------------------------------------------|
| master          | https://coral.caleydoapp.org                 |
| develop         | https://coral-daily.caleydoapp.org           |




Use product to setup a workspace
------------

1. Make sure that you meet all the prerequisites: https://wiki.datavisyn.io/phovea/development/workspace/general-prerequisites
2. To Setup a workspace you will need the [phovea generator](https://wiki.datavisyn.io/phovea/fundamentals/phovea-yeoman-generator):
```
npm install -g yo generator-phovea
```

3. Afterwards you can use the generator to prepare the workpace for you:
```
yo phovea:setup-workspace coral_product
```



***

<a href="https://caleydo.org"><img src="http://caleydo.org/assets/images/logos/caleydo.svg" align="left" width="200px" hspace="10" vspace="6"></a>
This repository is part of **[Phovea](http://phovea.caleydo.org/)**, a platform for developing web-based visualization applications. For tutorials, API docs, and more information about the build and deployment process, see the [documentation page](http://phovea.caleydo.org).


[phovea-image]: https://img.shields.io/badge/Phovea-Product-FABC15.svg
[phovea-url]: https://phovea.caleydo.org
[npm-image]: https://badge.fury.io/js/coral_product.svg
[npm-url]: https://npmjs.org/package/coral_product
