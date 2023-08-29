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