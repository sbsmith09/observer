# Prometheus: Add README for observer

## Project Overview

NFT Observer is a powerful tool designed to track and analyze NFT marketplace sales and metadata on the Solana blockchain. The project consists of two main components that work together to provide comprehensive NFT collection insights:

### Scraper
A specialized data collection tool that retrieves metadata for NFT collections using Solana's RPC methods. It can extract detailed information about NFT collections by:
- Querying metadata accounts using the Metaplex protocol
- Filtering collections by name or symbol
- Supporting flexible collection identification techniques

### Observer
An intelligent transaction monitoring system that:
- Periodically queries recent marketplace transactions
- Decodes and analyzes blockchain signatures
- Identifies different types of NFT market events (listings, sales, unlistings)

#### Key Features
- Support for multiple Solana NFT marketplaces (Solana Monkey Business, Digital Eyes, Solanart)
- Flexible metadata collection across different NFT projects
- Lightweight and adaptable design
- Open-source and community-driven

The project powers the Solana Observer Twitter bot, providing real-time insights into NFT market activities.

## Getting Started, Installation, and Setup

### Prerequisites

- .NET SDK (latest version recommended)
- Solana RPC endpoint (mainnet or devnet)

### Dependencies

The project uses .NET and relies on Solnet for Solana blockchain interactions. The main dependencies are managed through the project's `.csproj` files.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/MonkeDAO/observer.git
   cd observer
   ```

2. Restore .NET project dependencies:
   ```bash
   dotnet restore
   ```

### Configuration

#### Scraper Configuration

1. Edit the `_collections` dictionary in `Scraper/Program.cs` to specify the NFT collections you want to scrape.

2. Prepare to specify either:
   - Collection name (at offset 69)
   - Collection symbol (at offset 105)
   - Or both, for more precise metadata retrieval

#### Observer Configuration

1. Prepare dataset JSON files for the NFT collections
2. Place the datasets in the `Observer/Resources/` folder

### Running the Project

#### Running the Scraper

To run the scraper and retrieve NFT metadata:

```bash
dotnet run --project Scraper/Scraper.csproj --configuration Release
```

#### Running the Observer

To run the observer and track NFT marketplace activities:

```bash
dotnet run --project Observer/Observer.csproj --configuration Release
```

### Supported Marketplaces

The current implementation supports tracking sales for:
- Solana Monkey Business
- Digital Eyes
- Solanart

### Troubleshooting

- Ensure you have the latest .NET SDK installed
- Verify your Solana RPC endpoint is correct and accessible
- Check that dataset JSON files are correctly formatted and placed in the right directory

### Performance Notes

The scraper uses the powerful `getProgramAccounts` RPC method to retrieve metadata accounts efficiently. Depending on the collection, you might need to adjust filtering parameters.