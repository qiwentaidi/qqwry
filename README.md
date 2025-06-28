# qqwry

A Go library for querying IP location information using QQWry database format.

## Features

- Parse QQWry database files
- Query IP location information (country and area)
- Support for GBK encoding
- Lightweight and efficient

## Installation

```bash
go get github.com/qiwentaidi/qqwry
```

## Usage

```go
package main

import (
    "fmt"
    "log"
    "os"
    
    "github.com/qiwentaidi/qqwry"
)

func main() {
    // Open QQWry database file
    file, err := os.Open("qqwry.dat")
    if err != nil {
        log.Fatal(err)
    }
    defer file.Close()
    
    // Create QQWry instance
    qq, err := qqwry.NewQQwryFS(file)
    if err != nil {
        log.Fatal(err)
    }
    
    // Query IP address
    result, err := qq.Find("8.8.8.8")
    if err != nil {
        log.Fatal(err)
    }
    
    fmt.Println(result.String())
}
```

## API

### NewQQwryFS(fs *os.File) (*QQwry, error)
Creates a new QQWry instance from a file.

### Find(query string) (fmt.Stringer, error)
Queries the location information for an IP address.

## License

[Add your license here]

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.