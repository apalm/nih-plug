# Breaking changes

Since there is no stable release yet, there is also no proper changelog yet. But
since not everyone might want to dive through commit messages to find out what's
new and what's changed, this document lists all breaking changes in reverse
chronological order. If a new feature did not require any changes to existing
code then it will not be listed here.

## [2022-06-01]

- The `ClapPlugin::CLAP_FEATURES` field now uses an array of `ClapFeature`
  values instead of `&'static str`s. CLAP 0.26 contains many new predefined
  features, and the existing ones now use dashes instead of underscores. Custom
  features are still possible using `ClapFeature::Custom`.

## [2022-05-27]

- The `Plugin::initialize()` method now takes a `&mut impl InitContext` instead
  of a `&mut impl ProcessContext`.
- `Plugin::process()` now takes a new `aux: &mut AuxiliaryBuffers` parameter.
  This was needed to allow auxiliary (sidechain) inputs and outputs.

## [2022-05-22]

- Previously calling `param.non_automatable()` when constructing a parameter
  also made the parameter hidden. Hiding a parameter is now done through
  `param.hide()`, while `param.non_automatable()` simply makes it so that the
  parameter can only be changed manually and not through automation or
  modulation.
- The current processing mode is now stored in `BufferConfig`. Previously this
  could be fetched through a function on the `ProcessContext`, but this makes
  more sense as it remains constant until a plugin is deactivated. The
  `BufferConfig` now contains a field for the minimum buffer size that may or
  may not be set depending on the plugin API.

## ...

Who knows what happened at this point!
