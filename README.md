# github.com/speakeasy-sdks/calc

<!-- Start SDK Installation -->
## SDK Installation

```bash
go get github.com/speakeasy-sdks/calc
```
<!-- End SDK Installation -->

## SDK Example Usage
<!-- Start SDK Example Usage -->


```go
package main

import(
	"context"
	"log"
	"github.com/speakeasy-sdks/calc"
	"github.com/speakeasy-sdks/calc/pkg/models/operations"
	"github.com/speakeasy-sdks/calc/pkg/models/shared"
)

func main() {
    s := calculator.New()

    ctx := context.Background()
    res, err := s.SimpleCalculator.Calculate(ctx, operations.CalculateRequest{
        Operation: shared.OperationTypeMultiply,
        X: 5928.45,
        Y: 7151.9,
    })
    if err != nil {
        log.Fatal(err)
    }

    if res.Calculate200TextPlainNumber != nil {
        // handle response
    }
}
```
<!-- End SDK Example Usage -->

<!-- Start SDK Available Operations -->
## Available Resources and Operations


### [SimpleCalculator](docs/sdks/simplecalculator/README.md)

* [Calculate](docs/sdks/simplecalculator/README.md#calculate) - Calculate
<!-- End SDK Available Operations -->

### Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

### Contributions

While we value open-source contributions to this SDK, this library is generated programmatically.
Feel free to open a PR or a Github issue as a proof of concept and we'll do our best to include it in a future release!

### SDK Created by [Speakeasy](https://docs.speakeasyapi.dev/docs/using-speakeasy/client-sdks)
