# jordan 0.1.1

## New features

* adds `fizzbuzz()`
* adds data.frame functions
  * adds `quick_df()` to turn a list into a data.frame (used internally, too)
  * adds `complete_cases()` to select rows without `NA` values
  * removes `show_NA` parameter from `vector2df()` and `list2df()`
    * for vectors this will now produce an NA value for the first column
    * for lists `make.unique()` is utilized for empty name named to retain the position of the list element
* adds listing wrapper:
  * `ls_object()` to list all `is.object()`s 
  * `ls_dataframe()` to list all `is.data.frame()`s 
  * `ls_function()` to list all `is.function()`s 
* adds `counts()` and `props()` for counting unique elements in vectors and data.frames

## Changes

Some exported functions and names have been changed to prevent conflicts with other popular packages

* `%||%` is no longer exported; it is exported in `rlang` (and reexported in `purrr`) and is a relatively simply function anyway
* `collapse()` is now `collapse0()` to avoid conflicts with `glue`; although `glue::collapse()` is meant to be deprecated, `collapse0()` is mostly a wrapper for `paste0()`, so this may be a better name
* `set_names()` is now `set_names0()` to avoid conflicts with `rlang` (reexported from `purrr`) and `magrittr`

## Fixes/updates

* `do_paste_combine()` (used inside `paste_combine()`) simplified to remove use of `outer()`
* improves version bumping/updating
  * added `get_version()` to retrieve the current package version (assuming you're in the directory)
  * `utils::menu()` is called to confirm that version should be updated
  * can update by either adding a number to the version (`bump_version()` or by date `bump_date_version()`)
* implements an improved non-exported `string_extract()` function inside `str_extract_date()` and `str_extract_datettime()`

# jordan 0.1.0

Major cleanup for documenting, reviewing, removing, relocating, and testing functions.

* Added a `NEWS.md` file to track changes to the package
* Files renamed and reorganized
* Various tests included
* Added aliases to muffle messages and warnings (`muffle()` and `wuffle()`)
* Added `limit()`
* `match_param()` now returns correct errors messages for calls
* `write_clipboard()` formats vectors as characters
* `read_clipboard()` tries to correctly format vectors and data.frames
* removed `str_close_enough()` because this didn't make much sense anyway

## New functions

* `%colons%`: A substitute for `::` and `:::`
* `%||%`: Virtually identical to [rlang's version](https://github.com/r-lib/rlang/blob/0bce15a1e0ade47347c776cdbd823c4dbf2a527b/R/operators.R)
* `.CharacterIndex()`: Quick visual of indexes in character strings
* `bump_date_version`: Updated DESCRIPTION versions that are saved as dates
* `chr_split()`: Essentially an alias for `strsplit(., "")[[1]]`
* Error and warning handlers: `get_error()`, `get_warning()`, `has_error()`, `has_warning()`, `muffle()` and `wuffle()` (aliases for `suppressMessages()` and `suppressWarnings()`)
* File/directory utilities: `is_dir()`, `is_file()`, `list_dirs()`
* `is_na_cols()`: previously not exported, inside `select_na_cols()` and `remove_na_cols()`
* `limit()`: Limits a numeric vector by an upper and lower bound
* `match_param()`: Alternative to `match.arg()` without partial matching and more detailed error message
* Functions for calls: `outer_call()`, `outer_fun()`, `within_call()`, `within_fun()`
* `quiet_stop()`: calls `stop()` without throwing an error
* Functions for names: `set_names()`, `remove_names()`
* `require_namespace()`: Mostly a wrapper for `require()` with a more detailed error message
* `vap_*()`: Wrappers for `vapply()`, must like [purrr's map_*](https://github.com/tidyverse/purrr/blob/761a2224c437067c5d07beeeba06cde65a3e08a6/R/map.R)

## Moved to `jordanExtra`

Some miscellaneous, less controlled functions have been moved to [jordanExtra](https://github.com/jmbarbone/jordanExtra).

* Functions for Rust `set_rust_engine()`, `engine_rust()`
* Functions for [openxlsx](https://github.com/ycphs/openxlsx): `add_data_sheet()`, `add_image_sheet()`
* Functions for [pROC](https://github.com/xrobin/pROC): `pROC_optimal_threshold()`, `pROC_quick_plot()`
* Effect sizes: `cohen2odds()`, `cohend2r()`, `odds_ratio()`, `odds2d()`, `odds2r()`, `r2cohend()`
* Statistical functions: `fishers_method()`, `iqrs()`, `p_round()`, `p_value_sig()`, `percentile_rank()`, `proportion()`, `sd_pooled()`, `sterr()`, `tukey_coef()`, `z_score()`
* Others: `add_euclidean()`, `add_malahanobis()`, `%=+`, `filter_combine()`, `reverse_log_trans()`, 

# Prior development

* Initial commits of functions
* Quite a mess with no versions