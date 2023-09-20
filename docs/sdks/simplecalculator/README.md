# SimpleCalculator

### Available Operations

* [Calculate](#calculate) - Calculate

## Calculate

Calculates the expression using the specified operation.

### Example Usage

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
    s := calc.New()

    ctx := context.Background()
    res, err := s.SimpleCalculator.Calculate(ctx, operations.CalculateRequest{
        Operation: shared.OperationTypeDivide,
        X: 6027.63,
        Y: 8579.46,
    })
    if err != nil {
        log.Fatal(err)
    }

    if res.Calculate200TextPlainNumber != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `ctx`                                                                      | [context.Context](https://pkg.go.dev/context#Context)                      | :heavy_check_mark:                                                         | The context to use for the request.                                        |
| `request`                                                                  | [operations.CalculateRequest](../../models/operations/calculaterequest.md) | :heavy_check_mark:                                                         | The request object to use for the request.                                 |


### Response

**[*operations.CalculateResponse](../../models/operations/calculateresponse.md), error**

