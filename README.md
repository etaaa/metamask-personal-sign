# MetaMask personal_sign in Golang

[![Go Reference](https://pkg.go.dev/badge/github.com/etaaa/Golang-Ethereum-Personal-Sign.svg)](https://pkg.go.dev/github.com/etaaa/Golang-Ethereum-Personal-Sign)
[![Go Report Card](https://goreportcard.com/badge/github.com/etaaa/Golang-Ethereum-Personal-Sign)](https://goreportcard.com/report/github.com/etaaa/Golang-Ethereum-Personal-Sign)

A simple Golang solution for MetaMasks personal_sign method (<https://docs.metamask.io/wallet/how-to/sign-data/#use-personal_sign>).
Create a MetaMask signature for comparison: https://app.mycrypto.com/sign-message

## Usage

Install:
```bash
go get https://github.com/etaaa/metamask-personal-sign
```
Usage:
```go
package main

import (
	"fmt"
	"log"
	"os"
	"testing"

	"github.com/ethereum/go-ethereum/crypto"
	"github.com/joho/godotenv"

	ps "https://github.com/etaaa/metamask-personal-sign"
)

func main() {
	// Load private key from .env file
	err := godotenv.Load()
	if err != nil {
		log.Fatal(err)
	}
	privateKeyString := os.Getenv("PRIVATE_KEY")
	// Parse private key
	privateKey, err := crypto.HexToECDSA(privateKeyString)
	if err != nil {
		log.Fatal(err)
	}
	// Sign message
	signature, err := ps.PersonalSign("Hello World.", privateKey)
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println(signature)
}
```

## Questions
For any questions feel free to DM me on Discord (@itseta).

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change. Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
