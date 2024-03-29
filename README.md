# github.com/speakeasy-sdks/calc

<!-- Start SDK Installation [installation] -->
## SDK Installation

```bash
go get github.com/speakeasy-sdks/calc
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

### [SimpleCalculator](docs/sdks/simplecalculator/README.md)

* [Calculate](docs/sdks/simplecalculator/README.md#calculate) - Calculate
<!-- End Available Resources and Operations [operations] -->







<!-- Start Special Types [types] -->
## Special Types


<!-- End Special Types [types] -->



<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations.  All operations return a response object or an error, they will never return both.  When specified by the OpenAPI spec document, the SDK will return the appropriate subclass.

| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 4xx-5xx            | */*                |

### Example

```go
package main

import (
	"context"
	"errors"
	"github.com/speakeasy-sdks/calc"
	"github.com/speakeasy-sdks/calc/pkg/models/operations"
	"github.com/speakeasy-sdks/calc/pkg/models/sdkerrors"
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

		var e *sdkerrors.SDKError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->



<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"
	"github.com/myorg/your-go-sdk"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = sdk.New(sdk.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->



<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally using the `WithServerIndex` option when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| # | Server | Variables |
| - | ------ | --------- |
| 0 | `https://examples.apimatic.io/apps/calculator` | None |

#### Example

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
	s := calc.New(
		calc.WithServerIndex(0),
	)

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


### Override Server URL Per-Client

The default server can also be overridden globally using the `WithServerURL` option when initializing the SDK client instance. For example:
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
	s := calc.New(
		calc.WithServerURL("https://examples.apimatic.io/apps/calculator"),
	)

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
<!-- End Server Selection [server] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->



### Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

### Contributions

While we value open-source contributions to this SDK, this library is generated programmatically.
Feel free to open a PR or a Github issue as a proof of concept and we'll do our best to include it in a future release!

### SDK Created by [Speakeasy](https://docs.speakeasyapi.dev/docs/using-speakeasy/client-sdks)
