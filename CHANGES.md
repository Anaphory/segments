# Changelog

This project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased]


## [2.0.1] - 2018-08-02

### Bug fixes

- Fixed a bug where NULL values in orthography profiles could not be read when
  the profile was initialized with Unicode normalization.


## [2.0.0] - 2018-08-01

### Added

`segments` now supports orthography profiles described by CSVW metadata.


### Backward Incompatibilities

Orthography profiles and the input of `Tokenizer.__call__` is no longer Unicode normalized
by default. I.e. the user is responsible for making sure profiles and tokenization
input are normalized correspondingly. Alternatively, profile data can be normalized
by passing a `form` keyword argument when initializing a `Profile` instance. But
also in this case, tokenization input must be normalized by the user.

While this results in a more cumbersome API, it gives the user in full control, e.g.
to avoid incorrect segmentation when parts of decomposed graphemes are appended to
preseding grapheme clusters. 
