---
title: Migrate from 2.0 to 2.5
summary: Using SKNEQY Database
authors: Wilson Loh
date: 2021-10-26
tag: 2.0, 3.0
---

## OpenUpgrade from OCA

Tools to upgrade Odoo instances from a major version to another
This OCA project aims to provide an Open Source upgrade path for Odoo from one major Odoo version to the next one.

<br />

As PerfectWORK is based on Odoo framework, table below shows the matching of Odoo version of PerfectWORK releases.

!!! note "PerfectWORK and Odoo version"

    | **PerfectWORK**     | **Odoo Community** |
    | :-----------: | :-----------: |
    | **2.0**     | 11.0       |
    | 2.5     | 12.0       |
    | **3.0**     | 13.0       |
    | 3.3     | 14.0       |
    | 3.6     | 15.0       |
    | _**4.0**_     | 16.0       |

### Introduction

Odoo is an open source business application suite and development platform. This project, OpenUpgrade, aims to provide an Open Source upgrade path for Odoo. This is a community initiative, as the open source version of Odoo does not support migrations from one major release to another. Instead, migrations are part of a support package sold by Odoo SA. Note that the name of the project refers to the old name of Odoo, OpenERP.

!!! info "The project is hosted as two separate GitHub projects"

    * https://github.com/OCA/openupgrade
        * The branches in the first project contain the framework, as well as the database analysis and the migration scripts.
    - https://github.com/OCA/openupgradelib
        * The second project contains a library with helper functions. It can be used in the migration of any Odoo module.
  
!!! note "Changes in OpenUpgrade for PW 3.3"
    
    Before Odoo 14.0, the branches in https://github.com/OCA/openupgrade contain copies (or forks in Git terminology) of the Odoo main project, but with extra commits that include the framework, and the analysis and the migration scripts for each module.

### Migrating your database

Check out the code manually and upgrade your database by calling odoo-bin, (or openerp-server) directly. You will want to do this when you are working on developing migration scripts for uncovered modules.

#### Get the code

##### OpenUpgrade

!!! info "PerfectWORK 3.3"
    Make the _**openupgrade_framework**_ and the _**openupgrade_scripts**_ modules available in the addons path in the Odoo instance of the new version.

Or, for older versions: check out the OpenUpgrade source code from Github for the branches you need. Each branch migrates to its version from the previous version, so branch 13.0 migrates from 12.0 to 13.0. If you are migrating across multiple versions, you need to run each version of OpenUpgrade in order. _Skipping versions is not supported_.

<br />

The OpenUpgrade repository includes both openupgrade_framework and openupgrade_scripts:

https://github.com/OCA/openupgrade

##### openupgradelib
When installing the openupgradelib make sure you check out the latest version from github to get the latest updates and fixes:

``` bash
pip install git+https://github.com/OCA/openupgradelib.git@master#egg=openupgradelib
```

#### Check migration scripts for installed modules
Check if there are migration scripts provided for the set of modules that are installed in your Odoo database. If there are modules for which no migration scripts have been developed yet, your migration may fail or the integrity of your database may be lacking. Check the module coverage in this documentation under Module coverage and refer to the Migration script development documentation to add the missing migration scripts.

The simplest way to do this by running the following command:
<br />
``` bash
./odoo-bin -c pw.conf -d [database] -u all
```

##### Remove modules not available
You may need to remove those modules, which are obselete in the next major version

- backend theme ( pw_backend_theme )
- OCA web_responsive module
- Flectra converted modules
- website and related modules

##### Clean up database

May need to install the following module for database cleanup

https://apps.odoo.com/apps/modules/11.0/database_cleanup/


##### OCA and SYC modules 

Please ensure all the addons for the database are located in the addons path ( PW_ADDONS.2.5 )

If the module is not available at the higher version, you need to remove the modules or you need to write your own migration scripts for the module.


#### Make a copy of the database
Decide which database you are going to upgrade. You absolutely must make a backup of your live database before you start this process!

#### Adjust the configuration for Odoo and OpenUpgrade
Edit the configuration files and command line parameters to point to the database you are going to upgrade. The recommended command line parameters are the **_--update all --stop-after-init --load=base,web,openupgrade_framework_** flags.

<br />

For versions earlier than 14.0 that are running the OpenUpgrade fork rather than Odoo itself, you _do not pass the load parameter_.

##### Configuration options
When migrating across several versions of Odoo, setting the target version as an environment variable allows OpenUpgrade to skip methods that are called in every version but really only need to run in the target version. Make the target version available to OpenUpgrade with:

export OPENUPGRADE_TARGET_VERSION=13.0
(when migrating up to 13.0)

##### Obsolete options in the Odoo configuration file¶
Versions of OpenUpgrade earlier than 14.0 allow for the following configuration options. Add these options to a separate stanza in the server configuration file under a header [openupgrade]

- **autoinstall** - A dictionary with module name keys and lists of module names as values. If a key module is installed on your database, the modules from the value (and their dependencies) are selected for installation as well.

- **force_deps** - A dictionary with module name keys and lists of module names as values. If a key module is installed on your database, the modules from the value will be treated as a module dependency. With this directive, you can manipulate the order in which the modules are migrated. If the modules from the value are not already installed on your database, they will be selected for installation (as will their dependencies). Be careful not to introduce a circular dependency using this directive.

#### Run the upgrade, fix data and repeat…
Run the upgrade and check for errors. You will probably learn a lot about your data and have to do some manual clean up before and after the upgrade. Expect to repeat the process several times as you encounter errors, clean up your data, and try again. If necessary, ask for help or report bugs on Github.

##### Write the missing migration scripts
At this stage, if some of your modules don’t have yet migration scripts, you might need to add them yourself. Read more about the development of migrations scripts in Migration script development