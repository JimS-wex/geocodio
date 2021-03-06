# geocodio

[![GoDoc](https://godoc.org/github.com/stevepartridge/geocodio?status.svg)](https://godoc.org/github.com/stevepartridge/geocodio) [![Go Report Card](https://goreportcard.com/badge/github.com/stevepartridge/geocodio)](https://goreportcard.com/report/github.com/stevepartridge/geocodio)

Go client for [Geocodio](http://geocod.io) API v1

## Usage

### Geocode

```go
import(
  "github.com/stevepartridge/geocodio"
  "fmt"
)

func main() {
  gc, err := geocodio.NewGeocodio("YOUR_API_KEY")
	if err != nil {
		panic(err)
	}
	result, err := gc.Geocode("42370 Bob Hope Dr, Rancho Mirage, CA")
	if err != nil {
		panic(err)
	}
	fmt.Printf("Geocode Result %v", result)
	
  result, err = Geocodio.GeocodeByComponents("42370 Bob Hope Dr", "Rancho Mirage", "CA", "", "USA", "1")
	if err != nil {
		panic(err)
	}
	fmt.Printf("Geocode Result %v", result)
}
```

### Reverse Geocode

```go
import(
  "github.com/stevepartridge/geocodio"
  "fmt"
)

func main() {
  gc, err := geocodio.NewGeocodio("YOUR_API_KEY")
	if err != nil {
		panic(err)
	}
	result, err := gc.ReverseGeocode(38.9002898, -76.9990361)
	if err != nil {
		panic(err)
	}
	fmt.Printf("Reverse Geocode Result %v", result)
}
```

## Tests

You can run the tests leveraging your API key as an enviroment variable from terminal (\*nix).

```
API_KEY=<YOUR_API_KEY> go test -v -cover
```

TODO
-------
Fix breaking changes (see https://www.geocod.io/docs/#changelog):
  - The census append now supports vintage years, data is keyed by year instead of just returning a single year
  - Name property has been renamed to abbreviation
  - Name is now the full timezone name in a tzdb-compatible format
