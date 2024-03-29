# cosm-cli
Command-line-interface to `cosm`, a package manager for `lua` and `terra`.


## get status of a package or registry
```
cosm status                             (not implemented)
```
*Gives an overview of a package or registry when evaluated in the root of a package or registry, respectively.*

## instantiate a new package
```
cosm init <name>                        (implemented)
cosm init <name> -l <language>          (not implemented)
cosm init <name> --language <language>  (not implemented)
```
*Evaluate in parent folder of a new package. Adds a new package with name <name> according to a template (in .cosm/templates) of specified language <language>.*

## instantiate a new registry
```
cosm registry add <name> <giturl>       (implemented)
```
*Adds a new package registry (in .cosm/registries) with remote located at <giturl>.*

## add/remove/upgrade/downgrade project dependencies
```
cosm dependency add <name>              (not implemented)
cosm dependency add <name> <version>    (implemented)
<!-- cosm dependency add <name> -v <version> -->
<!-- cosm dependency add <name> --version <version> -->
<!-- cosm dependency add <name> -r <registry> -->
<!-- cosm dependency add <name> --registry <registry> -->
```
*Evaluate in a package root. Add a dependency to a project. Project <name> with version <version> will be looked up in any of the available local registries. If a package with the same name exists in multiple registries then the user will be prompted to choose the registry from the available listed registries. If no version is specified it will add the newest available version that is compatible with other package dependencies. The registry to look can also be provided as an option.*

```
cosm dependency rm <name>               (not implemented)
```
*Evaluate in a package root. Removes a project dependency.*

```
cosm dependency upgrade <name>                          (not implemented)
cosm dependency upgrade <name> -v <version>             (not implemented)
cosm dependency upgrade <name> --version <version>      (not implemented)
```
*Evaluate in a package root. Upgrades a project dependency to a new specified or unspecied (newest possible) version.*

```
cosm dependency downgrade <name> -v <version>           (not implemented)
cosm dependency downgrade <name> --version <version>    (not implemented)
```
*Evaluate in a package root. Downgrade a project dependency to a new specified or unspecied (newest possible) version.*

## register a project to a registry
```
cosm release add <registry>     (implemented)
```
*Evaluate in a package root. Release a package to <registry> (in .cosm/registries). An error is thrwon if the package does not have a git remote repository. An error is thrown if the current version already exists in the registry. The remote is updated automatically.*
```
cosm release add <registry> --patch     (not implemented)
cosm release add <registry> --minor     (not implemented)
cosm release add <registry> --major     (not implemented)
```
*Evaluate in a package root. Release a package to <registry> (in .cosm/registries) and bump the existing `patch`, `minor`, or `major` version. An error is thrown if the current version already exists in the registry. The remote is updated automatically.*
```
cosm release add <registry> -v <version>            (not implemented)
cosm release add <registry> --version <version>     (not implemented)
```
*Evaluate in a package root. Release a package to <registry> (in .cosm/registries) according to the provided version. The version name needs to adhere to the semantic versioning listed below. An error is thrown if the current version already exists in the registry. The remote is updated automatically.*