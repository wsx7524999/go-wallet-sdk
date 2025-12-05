# Repository Metadata

## Repository Details

### Description
The OKX Web3 Go Wallet SDK is a comprehensive solution for building wallet applications with offline transaction capabilities across multiple blockchain networks. It provides a unified interface for account management, transaction creation, and signing across various mainstream public chains.

### Owner
**Repository Owner**: wsx7524999 (Fork)  
**Original Organization**: OKX  
**Current Repository**: [wsx7524999/go-wallet-sdk](https://github.com/wsx7524999/go-wallet-sdk)  
**Original Repository**: [okx/go-wallet-sdk](https://github.com/okx/go-wallet-sdk)  
**Go Module Path**: `github.com/okx/go-wallet-sdk` (uses original module path)

### Primary Language
**Go** (version 1.23+)

### Key Features
- **Multi-chain support**: Seamlessly interact with major blockchains
- **Offline transaction signing**: Ensure security with local signing
- **Account generation and management**: Derive addresses with ease
- **Customizable transaction creation**: Flexible parameters for all supported chains
- **BRC20/Atomical/Runes support**: Full Bitcoin token standard compatibility
- **Extensible architecture**: Modular design for future blockchain integration

## Module Documentation

### pkg.go.dev Integration
Access the complete Go module documentation, API references, and package details on pkg.go.dev:

**📦 Module Documentation**: [pkg.go.dev/github.com/okx/go-wallet-sdk](https://pkg.go.dev/github.com/okx/go-wallet-sdk)

The module is available on pkg.go.dev with comprehensive documentation for all exported types, functions, and methods across the supported blockchain implementations.

### Installation
```bash
# Install the entire SDK
# Note: Even though this is a fork, the module path remains github.com/okx/go-wallet-sdk
go get -u github.com/okx/go-wallet-sdk

# Or install specific blockchain modules
go get -u github.com/okx/go-wallet-sdk/coins/bitcoin
go get -u github.com/okx/go-wallet-sdk/coins/ethereum
go get -u github.com/okx/go-wallet-sdk/coins/solana
```

> **Note**: This repository is a fork of the original OKX SDK. The Go module path continues to use `github.com/okx/go-wallet-sdk` as defined in `go.mod` to maintain compatibility with existing projects.

## Cryptocurrency Wallet Integration

### Supported Blockchains
The SDK provides comprehensive wallet integration capabilities for the following blockchain networks:

| Blockchain | Generate Address | Sign Transaction | Sign Message | Token Standards |
|------------|------------------|------------------|--------------|-----------------|
| **Aptos** | ✅ | ✅ | ✅ | Native |
| **Bitcoin** | ✅ | ✅ | ✅ | BRC20, Atomicals, Runes |
| **Cardano** | ✅ | ✅ | ✅ | Native |
| **Cosmos** | ✅ | ✅ | ✅ | Native |
| **Ethereum** | ✅ | ✅ | ✅ | ERC20, ERC721, ERC1155 |
| **Kaspa** | ✅ | ✅ | ✅ | Native |
| **Near** | ✅ | ✅ | ✅ | Native |
| **Solana** | ✅ | ✅ | ✅ | SPL Tokens |
| **Starknet** | ✅ | ✅ | ✅ | Native |
| **Stacks** | ✅ | ✅ | ✅ | Native |
| **Sui** | ✅ | ✅ | ✅ | Native |
| **Ton** | ✅ | ✅ | ✅ | Native |
| **Tron** | ✅ | ✅ | ✅ | TRC20 |

*Note: EVM-compatible chains (BSC, Polygon, Arbitrum, Avalanche, etc.) can reuse the Ethereum implementation.*

### Wallet Integration Guidelines

#### 1. Basic Wallet Operations
The SDK provides core wallet functionality:
- **Address Generation**: Generate blockchain-specific addresses from private keys or mnemonic phrases
- **Transaction Creation**: Build transactions with customizable parameters for each blockchain
- **Transaction Signing**: Sign transactions offline for enhanced security
- **Message Signing**: Sign arbitrary messages for authentication and verification

#### 2. Key Management
```go
// Example: Generate a new wallet address
import "github.com/okx/go-wallet-sdk/coins/bitcoin"

// Generate address from private key
address, err := bitcoin.NewAddressFromPrivateKey(privateKey)

// Generate hierarchical deterministic addresses
address, err := bitcoin.NewAddressFromMnemonic(mnemonic, derivationPath)
```

#### 3. Transaction Workflow
```go
// Example: Create and sign a transaction
// 1. Create transaction
tx := blockchain.NewTransaction(params)

// 2. Sign transaction offline
signedTx, err := blockchain.SignTransaction(tx, privateKey)

// 3. Broadcast to network (via your chosen RPC provider)
txHash, err := rpcClient.BroadcastTransaction(signedTx)
```

#### 4. Multi-Chain Wallet Implementation
For wallets supporting multiple chains:
- Use the modular structure under `coins/` directory
- Each blockchain has its own implementation in `coins/{blockchain}/`
- Common cryptographic operations are available in the `crypto/` package
- Shared utilities are provided in the `util/` package

## Cryptocurrency API Integration

### RPC Integration
The SDK focuses on transaction creation and signing. For blockchain interaction, integrate with:

#### Ethereum & EVM Chains
- **Infura**: [https://infura.io/](https://infura.io/)
- **Alchemy**: [https://www.alchemy.com/](https://www.alchemy.com/)
- **QuickNode**: [https://www.quicknode.com/](https://www.quicknode.com/)

#### Bitcoin
- **Blockcypher**: [https://www.blockcypher.com/](https://www.blockcypher.com/)
- **Blockchain.com API**: [https://www.blockchain.com/api](https://www.blockchain.com/api)
- **Mempool.space**: [https://mempool.space/api](https://mempool.space/api)

#### Solana
- **Solana RPC**: [https://docs.solana.com/api/http](https://docs.solana.com/api/http)
- **Helius**: [https://helius.dev/](https://helius.dev/)

#### Cosmos Ecosystem
- **Cosmos RPC**: [https://docs.cosmos.network/](https://docs.cosmos.network/)
- **All That Node**: [https://www.allthatnode.com/](https://www.allthatnode.com/)

#### Other Chains
Each blockchain in the `coins/` directory includes specific integration recommendations in its README.

### OKX Web3 API Integration
This SDK is part of the OKX Web3 ecosystem. For comprehensive blockchain data and wallet services:

- **OKX Web3 API**: [https://www.okx.com/web3/build/docs](https://www.okx.com/web3/build/docs)
- **OKX Wallet**: [https://www.okx.com/web3](https://www.okx.com/web3)

### Price Feeds & Market Data
Integrate with cryptocurrency market data APIs:
- **CoinGecko**: [https://www.coingecko.com/en/api](https://www.coingecko.com/en/api)
- **CoinMarketCap**: [https://coinmarketcap.com/api/](https://coinmarketcap.com/api/)
- **OKX Market Data**: [https://www.okx.com/api](https://www.okx.com/api)

## Documentation Services

### API Documentation

#### Swagger/OpenAPI
While this SDK is a Go library without REST endpoints, you can generate API documentation for your wallet service that uses this SDK:

- **Swagger**: [https://swagger.io/](https://swagger.io/)
- **OpenAPI Generator**: [https://openapi-generator.tech/](https://openapi-generator.tech/)

If you're building a REST API using this SDK, consider:
```bash
# Use swag to generate Swagger documentation
go install github.com/swaggo/swag/cmd/swag@latest
swag init
```

#### GitBook Documentation
For comprehensive project documentation and user guides:

- **GitBook**: [https://www.gitbook.com/](https://www.gitbook.com/)
- Consider creating a GitBook space for:
  - Integration guides
  - Blockchain-specific tutorials
  - Best practices and security guidelines
  - Example implementations

### Additional Documentation Resources

#### Official SDK Documentation
- **Main README**: [README.md](./README.md)
- **Changelog**: [CHANGELOG.md](./CHANGELOG.md)
- **Security Policy**: [SECURITY.md](./SECURITY.md)
- **License**: [LICENSE](./LICENSE)

#### Per-Blockchain Documentation
Each blockchain implementation includes detailed documentation:
- Navigate to `coins/{blockchain}/` directory
- Each directory contains a README with specific usage examples
- Examples:
  - [Aptos Documentation](https://github.com/okx/go-wallet-sdk/tree/main/coins/aptos)
  - [Bitcoin Documentation](https://github.com/okx/go-wallet-sdk/tree/main/coins/bitcoin)
  - [Ethereum Documentation](https://github.com/okx/go-wallet-sdk/tree/main/coins/ethereum)

#### Related SDK Resources
- **JS SDK Demo**: [https://okx.github.io/wallet-sdk-demo/](https://okx.github.io/wallet-sdk-demo/)
- **JS SDK Documentation**: [https://okx.github.io/js-wallet-sdk/](https://okx.github.io/js-wallet-sdk/)

### Go Package Documentation Tools

#### godoc
Generate local documentation:
```bash
# Install godoc
go install golang.org/x/tools/cmd/godoc@latest

# Run documentation server
godoc -http=:6060

# Access at http://localhost:6060/pkg/github.com/okx/go-wallet-sdk/
```

#### go doc
View documentation in terminal:
```bash
# View package documentation
go doc github.com/okx/go-wallet-sdk/coins/bitcoin

# View specific function documentation
go doc github.com/okx/go-wallet-sdk/coins/bitcoin.NewTransaction
```

## Build and Test

### Building the SDK
```bash
# Build all modules
sh build.sh

# Or build specific modules
cd coins/bitcoin && go build ./...
```

### Running Tests
```bash
# Test all modules
sh build.sh

# Test specific module
cd coins/ethereum && go test -v ./...

# Test with coverage
cd coins/bitcoin && go test -v -cover ./...
```

## Security Considerations

### Best Practices
1. **Never expose private keys**: Always handle private keys securely
2. **Offline signing**: Use the SDK's offline signing capabilities
3. **Validate addresses**: Always validate generated addresses
4. **Test transactions**: Test with small amounts on testnets first
5. **Keep dependencies updated**: Regularly update the SDK to get security patches

### Security Reporting
If you discover security vulnerabilities:
- **HackerOne**: [https://hackerone.com/okg](https://hackerone.com/okg)
- **OKX Feedback**: [https://www.okx.com/feedback/submit](https://www.okx.com/feedback/submit)

## Contributing

### Feedback and Issues
- **GitHub Issues**: [https://github.com/wsx7524999/go-wallet-sdk/issues](https://github.com/wsx7524999/go-wallet-sdk/issues)
- Submit bug reports, feature requests, and questions

### Development
- Fork the repository
- Create feature branches
- Submit pull requests with comprehensive descriptions
- Follow Go coding standards and best practices

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.

---

**Last Updated**: December 2025  
**SDK Version**: Compatible with Go 1.23+  
**Repository**: [wsx7524999/go-wallet-sdk](https://github.com/wsx7524999/go-wallet-sdk)
