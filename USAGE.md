<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	"github.com/speakeasy-sdks/calc"
	"github.com/speakeasy-sdks/calc/pkg/models/operations"
	"github.com/speakeasy-sdks/calc/pkg/models/shared"
	"log"
)

func main() {
	s := calc.New()

	ctx := context.Background()
	res, err := s.SimpleCalculator.Calculate(ctx, operations.CalculateRequest{
		Operation: shared.OperationTypeSubtract,
		X:         3946.69,
		Y:         6431.33,
	})
	if err != nil {
		log.Fatal(err)
	}

	if res.Res != nil {
		// handle response
	}
}

```
<!-- End SDK Example Usage [usage] -->