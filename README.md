
# MolgenisAuth

<!-- badges: start -->
[![Travis build status](https://travis-ci.org/molgenis/molgenis-r-auth.svg?branch=master)](https://travis-ci.org/molgenis/molgenis-r-auth)
[![CRAN status](https://www.r-pkg.org/badges/version/MolgenisAuth)](https://CRAN.R-project.org/package=MolgenisAuth)
[![codecov](https://codecov.io/gh/molgenis/molgenis-r-auth/branch/master/graph/badge.svg)](https://codecov.io/gh/molgenis/molgenis-r-auth)
<!-- badges: end -->

The goal of MolgenisAuth is to discover and authenticate against an OpenID
Connect server. We have tested it using [fusionauth](https://fusionauth.io/).

## Installation

You can install the released version of MolgenisAuth from [CRAN](https://CRAN.R-project.org) with:


```r
install.packages("MolgenisAuth")
```

And the development version from [GitHub](https://github.com/) with:


```r
# install.packages("devtools")
devtools::install_github("molgenis/molgenis-r-auth")
```
## Usage

To discover endpoint URLs on an OpenID Connect authentication server:


```r
library(MolgenisAuth)
endpoint <- discover("https://auth.molgenis.org")
endpoint
#> <oauth_endpoint>
#>  authorize: https://auth.molgenis.org/oauth2/authorize
#>  access:    https://auth.molgenis.org/oauth2/token
#>  user:      https://auth.molgenis.org/oauth2/userinfo
#>  device:    https://auth.molgenis.org/oauth2/device_authorize
#>  logout:    https://auth.molgenis.org/oauth2/logout
```

Using this endpoint, you can then authenticate using the device flow.
This will open a browser window so you can authenticate with the
authentication server.

```r
credentials <- device_flow_auth(endpoint, "b396233b-cdb2-449e-ac5c-a0d28b38f791")
#> [1] "We're opening a browser so you can log in with code WB7R2K"
credentials$id_token
#> [1] "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlcwbmltejhpYU9DLW16OXNaTVRiVzRfbFdMMCJ9.eyJhdWQiOiJiMzk2MjMzYi1jZGIyLTQ0OWUtYWM1Yy1hMGQyOGIzOGY3OTEiLCJleHAiOjE2MDQxNjY0MjksImlhdCI6MTYwNDE2MjgyOSwiaXNzIjoiaHR0cHM6Ly9hdXRoLm1vbGdlbmlzLm9yZyIsInN1YiI6ImQ4OTk1OTc2LWU4ZDgtNDM5MC04MzliLTAwN2EzODJmYzEyYiIsImp0aSI6ImE2OTlkMmQyLWQ1YWQtNGY3Ny1iMjAwLTcyZDA5NTA0YmY2YSIsImF1dGhlbnRpY2F0aW9uVHlwZSI6IlBBU1NXT1JEIiwiZW1haWwiOiJmLmtlbHBpbkB1bWNnLm5sIiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImF0X2hhc2giOiIyRzJObkxFT3VDWHcxZFpiZWZuRDJ3IiwiYXBwbGljYXRpb25JZCI6ImIzOTYyMzNiLWNkYjItNDQ5ZS1hYzVjLWEwZDI4YjM4Zjc5MSIsInJvbGVzIjpbIlNVIl0sInBvbGljeSI6InJlYWR3cml0ZSJ9.azOOYuCQQhdyMCW-8kBe_z3dgtPUbews8vkcaNzB2rHZZLVXU4LbmR-p2Dx6hqVaRK5vunU2tIWT07cq5sqnxHM7a9AepYW5sKOwOut2BUqUzJMkGi6AICwTip-xavEVXpnjlx09qLHDKdKeCYG87ODVnp5Ta7_p7hlbMu3eelkp1zfGgH7Q43XgYM8ZwAeIVGtR5nY_diA4v1yRBNlRpmqSjNHnqeWFso0LhMtkFLhloTs1-gFcoOQhAQFF0UNpHYWPmoivP1_lujSwAvWXx6UCg7sVSy9hP6-qZQkQsBuQWbzk8Iln8L1-eaPU2fq1ulRMjEJO2BcL0vjTlok8oQ"
```

## Support
We appreciate help, so do not be shy and file pull-requests for things that are
broken or file a bug report.
