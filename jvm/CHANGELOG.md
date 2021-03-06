# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/).

## Next release

## [0.3.0] - 2017-08-31

### Added

* Marshalling lists of refs to a Java array.
* Implement push and pop family of functions for managing local
  references. This makes it possible to perform semi-automatic
  reclaiming of local references, by pushing new frames and
  deallocating whole groups of references at once when popping the
  frames.
* Benchmarks to quantify the cost of references.
* `newArray`, a polymorphic way to create new arrays on top of the raw
  newXXXArray JNI functions.
* `getStaticField`, to get the values of fields using any of the
  `getStaticXXXField` JNI functions.
* `CChar` instance for `Reify`.
* Expose `jobject` to get Java references from Haskell values with a
  Coercible instance with a reference type.

### Changed

* Simplify the `Reify` and `Reflect` machinery. These type classes now
  each take a single argument. The `Uncurry` type class, to avoid
  overlapping instances in `sparkle`, has been removed.
* `callStatic` takes a `JNI.String` instead of a singleton.
* `classOf` returns a JNI.String instead of a singleton.

### Removed

* The Uncurry type family.
* `Reify` and `Reflect` instances for `J ty`.
* Second parameter of Reflect/Reify.
* TH convenience function to produce Coercible and Reify instances for
  newtype wrappers of Java references. This is less useful now that
  we don't provide `Reify` and `Reflect` instances for `J ty`.

### Fixed

* Tests in conditional compilation for ghc-8.0.1.
* Use global refs in finalizers associated to IOVectors.

## [0.2.2] - 2017-05-03

### Added

* Added TH convenience function to produce Coercible and Reify
  instances for newtype wrappers of Java references.
* Made Choice Coercible to a Java boolean.

## [0.2.0] - 2017-02-21
