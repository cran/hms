
# hms <a href='https:/hms.tidyverse.org'><img src='man/figures/logo.png' align="right" height="139" /></a>

<!-- badges: start -->

[![Lifecycle:
maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
[![Travis-CI Build
Status](https://travis-ci.org/tidyverse/hms.svg?branch=master)](https://travis-ci.org/tidyverse/hms)
[![AppVeyor Build
Status](https://ci.appveyor.com/api/projects/status/github/tidyverse/hms?branch=master&svg=true)](https://ci.appveyor.com/project/tidyverse/hms)
[![codecov](https://codecov.io/gh/tidyverse/hms/branch/master/graph/badge.svg)](https://codecov.io/gh/tidyverse/hms)
[![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/hms)](https://cran.r-project.org/package=hms)
<!-- badges: end -->

## Overview

The hms package provides a simple class for storing durations or
time-of-day values and displaying them in the hh:mm:ss format. This
class is intended to simplify data exchange with databases,
spreadsheets, and other data sources:

  - Stores values as a numeric vector that contains the number of
    seconds since midnight
  - Supports construction from explicit hour, minute, or second values
  - Supports coercion to and from various data types, including `POSIXt`
  - Can be used as column in a data frame
  - Based on the `difftime` class
  - Values can exceed the 24-hour boundary or be negative
  - By default, fractional seconds up to a microsecond are displayed,
    regardless of the value of the `"digits.secs"` option

## Installation

``` r
# The easiest way to get hms is to install the whole tidyverse:
install.packages("tidyverse")

# Alternatively, install just hms:
install.packages("hms")

# Or the the development version from GitHub:
# install.packages("devtools")
devtools::install_github("tidyverse/hms")
```

## Usage

The following example showcases ways of using the `hms` class standalone
or as a data frame column.

``` r
library(hms)

hms(56, 34, 12)
#> 12:34:56
as_hms(1)
#> 00:00:01
as_hms("12:34:56")
#> 12:34:56
as_hms(Sys.time())
#> 11:18:52.496955
as.POSIXct(hms(1))
#> [1] "1970-01-01 00:00:01 UTC"

data.frame(hours = 1:3, hms = hms(hours = 1:3))
#>   hours      hms
#> 1     1 01:00:00
#> 2     2 02:00:00
#> 3     3 03:00:00
```

-----

Please note that the ‘hms’ project is released with a [Contributor Code
of
Conduct](https://github.com/tidyverse/hms/blob/master/CODE_OF_CONDUCT.md).
By contributing to this project, you agree to abide by its terms.
