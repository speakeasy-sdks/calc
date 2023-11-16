# SimpleCalculator
(*SimpleCalculator*)

### Available Operations

* [Calculate](#calculate) - Calculate

## Calculate

Calculates the expression using the specified operation.

### Example Usage

```go
package main

import(
	"github.com/speakeasy-sdks/calc"
	"context"
	"github.com/speakeasy-sdks/calc/pkg/models/shared"
	"github.com/speakeasy-sdks/calc/pkg/models/operations"
	"log"
)

func main() {
    s := calc.New()

    ctx := context.Background()
    res, err := s.SimpleCalculator.Calculate(ctx, operations.CalculateRequest{
        Operation: shared.OperationTypeSubtract,
        X: 3946.69,
        Y: 6431.33,
    })
    if err != nil {
        log.Fatal(err)
    }

    if res.Res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [operations.CalculateRequest](../../pkg/models/operations/calculaterequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |


### Response

**[*operations.CalculateResponse](../../pkg/models/operations/calculateresponse.md), error**
| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 400-600            | */*                |
