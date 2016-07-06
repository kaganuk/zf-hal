# Changelog

All notable changes to this project will be documented in this file, in reverse chronological order by release.

## 1.4.0 - TBD

### Added

- [#99](https://github.com/zfcampus/zf-hal/pull/99) adds accessors for the
  `$entity` and `$id` properties of `ZF\Hal\Entity`.
- [#124](https://github.com/zfcampus/zf-hal/pull/124) adds a new interface
  `ZF\Hal\Link\SelfLinkInjectorInterface` and default implementation
  `ZF\Hal\Link\SelfLinkInjector`; these are now used as collaborators to the
  `Hal` plugin to simplify internal logic, and allow users to provide alternate
  strategies for generating the `self` relational link.
- [#125](https://github.com/zfcampus/zf-hal/pull/125) adds a new service,
  `ZF\Hal\Link\LinkUrlBuilder`. This class composes the `ServerUrl` and `Url`
  view helpers in order to provide the functionality required to build a
  route-based link URL. The `Hal` plugin now consumes this instead of
  implementing the logic internally.

  The upshot is: you can replace the URL generation semantics for your
  application entirely by pointing the service to your own implementation.
- [#125](https://github.com/zfcampus/zf-hal/pull/125) adds service factories for
  each of the `LinkExtractor` and `LinkCollectionExtractor`, which now allows
  users to provide substitutions for their functionality. (Extractors pull links
  and link collections in order to generate the relational links for a HAL-JSON
  payload.)

### Deprecated

- [#99](https://github.com/zfcampus/zf-hal/pull/99) deprecates usage of property
  access on `ZF\Hal\Entity` to retrieve the identifier and underlying entity
  instance.
- [#125](https://github.com/zfcampus/zf-hal/pull/125) deprecates the usage of
  `Hal::setServerUrlHelper()` and `Hal::setUrlHelper()`; these will each now
  raise an exception indicating the user should use a `LinkUrlBuilder` for URL
  generation instead.
- [#125](https://github.com/zfcampus/zf-hal/pull/125) deprecates passing a
  `ServerUrlHelper` and `UrlHelper` to the constructor of
  `ZF\Hal\Exctractor\LinkExtractor`; it now expects a `LinkUrlBuilder` instance
  instead. (This class is primarily an internal detail of the `Hal` plugin.)

### Removed

- Nothing.

### Fixed

- Nothing.

## 1.3.1 - TBD

### Added

- Nothing.

### Deprecated

- Nothing.

### Removed

- Nothing.

### Fixed

- [#111](https://github.com/zfcampus/zf-hal/pull/111) removes some code errantly
  left in a comment from a previous merge conflict.
- [#112](https://github.com/zfcampus/zf-hal/pull/112) conditionals based on PHP
  5.4, as the minimum version is now 5.5.

## 1.3.0 - 2015-09-22

### Added

- [#123](https://github.com/zfcampus/zf-hal/pull/123) updates the component
  to use zend-hydrator for hydrator functionality; this provides forward
  compatibility with zend-hydrator, and backwards compatibility with
  hydrators from older versions of zend-stdlib.

### Deprecated

- Nothing.

### Removed

- Nothing.

### Fixed

- Nothing.

## 1.2.1 - 2015-09-22

### Added

- Nothing.

### Deprecated

- Nothing.

### Removed

- Nothing.

### Fixed

- [#122](https://github.com/zfcampus/zf-hal/pull/122) updates the
  zend-stdlib dependency to reference `>=2.5.0,<2.7.0` to ensure hydrators
  will work as expected following extraction of hydrators to the zend-hydrator
  repository.