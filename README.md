coral_product [![Phovea][phovea-image]][phovea-url]
=====================

Coral is a web-based visual analysis tool for creating and characterizing cohorts.  
This repository described how to setup a Coral instance. Please have a look into the [Coral repository](https://github.com/Caleydo/coral) for more information on Coral.

---

Coral is based on the [Target Discovery Platform](https://github.com/datavisyn/tdp_core) and [Phovea framework](http://phovea.caleydo.org/), runs the backend with [Phovea Server](https://github.com/phovea/phovea_server), and uses multiple other plugins.
To ease the set up process, this repository describes all required components for the front and back end of Coral, as used by the public Coral instances:

| [Coral Branch](https://github.com/Caleydo/coral/branches)          | app                                          | status   |
|-----------------------|----------------------------------------------|----------|
| [main](https://github.com/Caleydo/coral)                | https://coral.caleydoapp.org                 | [![CircleCI](https://circleci.com/gh/Caleydo/coral_product.svg?style=svg)](https://circleci.com/gh/Caleydo/coral_product)  |
| [develop](https://github.com/Caleydo/coral/tree/develop)               | https://coral-daily.caleydoapp.org           | [![CircleCI](https://circleci.com/gh/Caleydo/coral_product/tree/develop.svg?style=svg)](https://circleci.com/gh/Caleydo/coral_product?branch=develop)  |

A running Coral instance consists of:

* **Frontend** = [Coral](https://github.com/Caleydo/coral) web app, using:
  * [tdp_core](https://github.com/datavisyn/tdp_core/), as framework with session management, data connectors, and more; see [TDP Documentation](https://wiki.datavisyn.io/tdp/tdp-documentation)
  * [phovea_clue](https://github.com/phovea/phovea_clue), to track interaction provenance; see [doi:10.1111/cgf.12925](https://dx.doi.org/10.1111/cgf.12925)
  * [phovea_ui](https://github.com/phovea/phovea_ui), for basic UI components
  * [phovea_security_flask](https://github.com/phovea/phovea_security_flask), for security and user handling
  * [phovea_security_store_generated](https://github.com/datavisyn/phovea_security_store_generated), to automatically create dummy users

* **Backend** = [Phovea Server](https://github.com/phovea/phovea_server), a python server using these plugins:
  * [coral](https://github.com/Caleydo/coral), server side plugin to create cohorts in the database and read their data
  * [tdp_core](https://github.com/datavisyn/tdp_core/), as framework for db communication
  * [tdp_publicdb](https://github.com/Caleydo/tdp_publicdb), connector to access the data used in the public Coral instance.
  * [phovea_security_flask](https://github.com/phovea/phovea_security_flask) and [phovea_security_store_generated](https://github.com/datavisyn/phovea_security_store_generated), again for user handling
  * [phovea_clue](https://github.com/phovea/phovea_clue), server side part for provenance tracking
  * [phovea_data_redis](https://github.com/phovea/phovea_data_redis/) and [phovea_data_mongo](https://github.com/phovea/phovea_data_mongo/), as connectors to respective db types
    * A redis databse  is used for [ID mapping](https://wiki.datavisyn.io/tdp/tdp-documentation#id-management-and-id-mapping)
    * A mongo database is used to store the provenance and session data

* **Database** = A Postgres database with the data to analyse and where the created cohorts get stored.

:wrench: Setup a Coral workspace
------------

Follow the steps below the set up a workspace with the above components.

1. Make sure that you meet all the prerequisites described in the [Wiki](https://wiki.datavisyn.io/phovea/development/workspace/general-prerequisites)
2. The [phovea generator](https://wiki.datavisyn.io/phovea/fundamentals/phovea-yeoman-generator) will check out repositories and setup a workspace for you. Check the [package.json](package.json) for the generator version compatible with this build.
3. To prepare the workpace, run:
  ```
  yo phovea:setup-workspace coral_product -b main
  ```
4. Follow the instructions of the generator and Coral will be ready to use.
5. The database credentials and location are not included in the repositories. Provde them via the `config.jon` file at the root of the workspace:

```json
 "tdp_publicdb" : {
   "dburl": "postgresql://read_user:password@postgres.db.url/database_name"
  },
  "coral": {
    "dburl": "postgresql://read_write_user:password@postgres.db.url/database_name"
  }
}
```

That's it! 🎉  
For any questions or problems, wirte us an email to coral@caleydo.org or [create an issue on GitHub](https://github.com/Caleydo/coral/issues).

:arrow_up_small: Update the Coral workspace
------------

Updating an exisiting workspace is a straight forward process:

1. Fetch the latest commits from the repositories in your workspace. There is a `forEach` script to ease the process. Run: `./forEach git pull`
2. Incorporate possible changes into the workspace: `yo phovea:update`
3. If necessary, update npm dependencies : `npm install`
4. Restart Docker and webpack builds.

***

This repository is part of **[Phovea](http://phovea.caleydo.org/)**, a platform for developing web-based visualization applications.

<a href="https://caleydo.org"><img src="http://caleydo.org/assets/images/logos/caleydo.svg" align="left" width="200px" hspace="10" vspace="6"></a>
For tutorials, API docs, and more information about the build and deployment process, see the [documentation page](http://phovea.caleydo.org).


[phovea-image]: https://img.shields.io/badge/Phovea-Product-FABC15.svg
[phovea-url]: https://phovea.caleydo.org
[npm-image]: https://badge.fury.io/js/coral_product.svg
[npm-url]: https://npmjs.org/package/coral_product
