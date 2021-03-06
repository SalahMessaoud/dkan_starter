# Change log

## [1.12.10.3]
### Changed
- Remake dkan (#146)
- Fix data_config deployment issue (#146)
- Change CircleCI settings (#146)

## [1.12.10.3]
### Changed
- Add "lt" environment map #144
- Update nucivic-ahoy #143

## [1.12.10.2]
### Changed
- Disabled clamav by default. REF #140
### Added
- New config/config.yml param: `default: clamav`

## [1.12.10.1]
### Changed
- Set cron_safe_threshold to 0 so it only runs from Jenkins

## [1.12.10.0]
### Changed
- Remove new relic automatic settings #97
- Allow multiple tests via `ahoy dkan test` #126, nucivic/dkan#1351
- Remove .ahoy unnecessary deploy steps: nucivic/nucivic-ahoy#92
- Update dkan to version 1.12.10
  - Fix broken dkan update: nucivic/dkan#1283

## [1.12.9.0]
### Changed
- Updated dkan version to 1.12.9
- Added fast_file configuration setup via 'fast_file' config/config.yml
- Added 'https_everywhere' configuration
- Added stage_file_proxy configuration

## [1.12.8.0]
### Added
- Add new id for search servers

### Changed
- Remake dkan at 1.12.8 with release-1-12 patch
- Added securepages configuration

### Fixed
- Acquia solr search not using correct server.

## [1.12.7.0]
### Added
- config.yml (root level to store ata_starter specific metadata/and defaults)

### Changed
- Remake dkan at 1.12.7 with release-1-12 patch
- Versioning scheme (drop 7.x)

### Removed
- Unnecessary custom_config deps and info section

### Fixed
- `ahoy build custom` breaks if invalid custom.make

## [7.x-1.12.6.9]

### Fixed
- `ahoy build custom` breaks if invalid custom.make

## [7.x-1.12.6.8]

### Changed
- Skip more custom tests. 

## [7.x-1.12.6.7]

### Fixed
- Patches broken panalizer update. 

## [7.x-1.12.6.6]

### Fixed
- Updated DKAN to fix topics issue.

### Changed
- Updated settings.acquia.php to include correct solr server name.
- Updated ahoy tools.

### Removed
- assets/.htacess
- Symlink from docroot/.htacess to config/.htaccess

## [7.x-1.12.6.5]

### Added
- added default `config/.htaccess`

### Fixed
- Fixed more failing tests in DKAN.

### Changed
- Updated ahoy tools. `ahoy build new` does not throw ambiguous error when no
  argument is passed. 

### Deprecated

### Removed

### Security

## [7.x-1.12.6.4]

### Added

### Fixed
- Fixed upgraded hooks. 


### Changed
- Updated ahoy tools. `ahoy site config` now does not clobber custom .htaccess.

### Deprecated

### Removed

### Security

## [7.x-1.12.6.2]

### Added

### Fixed
- Patches `dkan 7.x-1.12.6`, skips custom tests.
- Patches `dkan 7.x-1.12.6`, fix tests break because configured not installed.


### Changed
- `ahoy site setup` now builds dynamic drush alias using `ahoy site name`

### Deprecated

### Removed

### Security

## [7.x-1.12.3.1] 2016-07-11
## [Unreleased]

### Added

### Fixed

### Changed
- `site rebuild` now uses `site update-data-starter`
- `site remake` only does a full remake if it runs within a Data Starter working copy
- `custom.make` no longer included from `build.make`
- `site custom` recipe to run drush make against `custom.make`
- `site new` now is only available if it runs within a Data Starter working copy
- `site dkan` only updates dkan if it runs within a Data Starter working copy
- `site update-data-starter` now places a working copy at `.data_starter_private` to speed up the update process (.gitignore is updated to ignore the folder)
- `site update-data-starter` prunes the working copy in `.data_starter_private` in advance to simplify the rsync copy

### Deprecated

### Removed

### Security

## [7.x-1.12.3.1] 2016-07-11
### Added
- `ahoy site config` takes configuration in `config/config.yml` and generates `config/config.php`
- Sample `config/config.yml` added:
```yaml
default:
  hostname: localhost
  https_everywhere: FALSE
acquia:
  subscription: 'professional'
  dev:
    base_url: http://devurl
    core_id: changeme
    derived_key: changeme
  test:
    base_url: http://testurl
    core_id: changeme
    derived_key: changeme
  ra:
    base_url: http://testurl
    core_id: changeme
    derived_key: changeme
  prod:
    base_url: http://produrl
    core_id: changeme
    derived_key: changeme
```
- A symlink has been added from `hooks/common/post-code-deploy/deploy.sh -> drush-env-switch.sh` for backwards compatibility.

### Changed
- `drush/aliases.local.php` now defines an alias for data_starter that's used on cirle ci
- `ahoy site setup` creates a symlink to `/var/www/docroot` if it's run on circle
- `config/config.php` is now part of the data_starter codebase
- `devinci_custom_environment_switch` function has been moved from `settins.php` to `settings.nucivic.php`
- `drush-env-switch.sh` deployment hook script now uses passed in `site` and `env` variables to run deployment.
- `ahoy custom setup/deploy` now call `ahoy ci setup/deploy` oob.
- `ahoy ci deploy` now calls the acquia hook deployment script and the deployment script runs a environment force switch
- `ahoy site update-data-starter` has been modified so that it excludes any changes to `projects/modules/custom` or to `assets/sites/default/settings.php`
- `ahoy site config` will trigger not just the config.php generation but potentially any site specific changes that can be applied via the templates `config/template` do to `config.yml` 

## [7.x-1.12.3.0] 2016-07-05
### Changed
- Updates dkan to 7.x-1.12.3.0

## [7.x-1.12.2.4] 2016-06-18
### Changed
- `ahoy custom setup` and `ahoy custom deploy` now trigger ci commands
### Fixed
- `ahoy site setup` to fix `find: unknown predicate -exec=cp'`
- Only makes acquia solr available in solr environments

## [7.x-1.12.2.3] 2016-06-17
### Changed
- Updates ahoy tools

## [7.x-1.12.2.2] 2016-06-16
### Added
- Adds dkan health status module to codebase
### Fixed
- Features master array related errors
### Changed
- Better Solr handled logic

## [7.x-1.12.2.1] 2016-06-10
### Added
- Better memcache integration handling in `assets/sites/default/settings.php`

## [7.x-1.12.2.0] 2016-06-10
### Changed
- Updates dkan to 7.x-1.12.2
