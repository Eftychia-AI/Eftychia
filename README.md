<div align="center">

# Eftychia - Oracle Layer

![image](https://github.com/user-attachments/assets/ceb95c7b-1b5b-4565-a05c-c2b93d922129)


## Treasury Wallet

SOL Address:

</div>

An open-source oracle for connecting AI agents to Social Media and Solana

- Scale Datasets
- Constant Datafeed
- Deploy Datasets
- **Market Data Integration**
  - CoinGecko Pro API integration
  - Real-time token price data
  - Trending tokens and pools
  - Top gainers analysis
  - Token information lookup
  - Latest pool tracking

## 🤖 AI Integration Features

- **LangChain Integration**
  - Ready-to-use LangChain tools for blockchain operations
  - Autonomous agent support with React framework
  - Memory management for persistent interactions
  - Streaming responses for real-time feedback

- **Vercel AI SDK Integration**
  - Vercel AI SDK for AI agent integration
  - Framework agnostic support
  - Quick and easy toolkit setup

- **Autonomous Modes**
  - Interactive chat mode for guided operations
  - Autonomous mode for independent agent actions
  - Configurable action intervals
  - Built-in error handling and recovery

- **AI Tools**
  - DALL-E integration for NFT artwork generation
  - Natural language processing for blockchain commands
  - Price feed integration for market analysis
  - Automated decision-making capabilities

## 📃 Documentation


## 📦 Core Installation

```bash
npm install eftychia
```

## Quick Start

Initializing the wallet interface and agent with plugins:

```typescript
import { SolanaAgentKit, createVercelAITools, PhantomWallet } 
import MiscPlugin from "@solana-agent-kit/plugin-misc";
import BlinksPlugin from "@solana-agent-kit/plugin-blinks";

const keyPair = Keypair.fromSecretKey(bs58.decode("YOUR_SECRET_KEY"))
const wallet = new KeypairWallet(keyPair)

// Initialize with private key and optional RPC URL
const agent = new SolanaAgentKit(
  wallet,
  "YOUR_RPC_URL",
  {
    OPENAI_API_KEY: "YOUR_OPENAI_API_KEY",
  }
) // Add the plugins you would like to use
  .use(TokenPlugin)
  .use(NFTPlugin)
  .use(DefiPlugin)
  .use(MiscPlugin)
  .use(BlinksPlugin);

// Create LangChain tools
const tools = createVercelAITools(agent, agent.actions);
```


### Fetch Price Data from Pyth

```typescript

const priceFeedID = await agent.methods.fetchPythPriceFeedID("SOL");

const price = await agent.methods.fetchPythPrice(priceFeedID);

console.log("Price of SOL/USD:", price);
```


### Get a Solana asset by its ID

```typescript
const asset = await agent.methods.getAsset(agent, "41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU")
```

### Get a price inference from Allora

Get the price for a given token and timeframe from Allora's API

```typescript
const sol5mPrice = await agent.methods.getPriceInference("SOL", "5m");
console.log("5m price inference of SOL/USD:", sol5mPrice);
```

### List all topics from Allora

```typescript
const topics = await agent.methods.getAllTopics();
console.log("Allora topics:", topics);
```

### Get an inference for an specific topic from Allora

```typescript
const inference = await agent.methods.getInferenceByTopicId(42);
console.log("Allora inference for topic 42:", inference);
```

### Simulate a Switchboard feed

Simulate a given Switchboard feed. Find or create feeds [here](https://ondemand.switchboard.xyz/solana/mainnet).

```typescript
const value = await agent.methods.simulateSwitchboardFeed(
      "9wcBMATS8bGLQ2UcRuYjsRAD7TPqB1CMhqfueBx78Uj2", // TRUMP/USD
      "http://crossbar.switchboard.xyz");;
console.log("Simulation resulted in the following value:", value);

### Cross-Chain Bridge via deBridge

The Solana Agent Kit supports cross-chain token transfers using deBridge's DLN protocol. Here's how to use it:

1. Check supported chains:
```typescript
const chains = await agent.methods.getDebridgeSupportedChains();
console.log("Available chains:", chains);
// Example output: { chains: [{ chainId: "1", chainName: "Ethereum" }, { chainId: "7565164", chainName: "Solana" }] }
```


### Get Token Price Data from CoinGecko

```typescript
const priceData = await agent.methods.getTokenPriceData([
  "So11111111111111111111111111111111111111112", // SOL
  "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v"  // USDC
]);
console.log("Token prices:", priceData);
```

### Get Trending Tokens

```typescript
const trendingTokens = await agent.methods.getTrendingTokens();
console.log("Trending tokens:", trendingTokens);
```

### Get Latest Pools

```typescript
const latestPools = await agent.methods.getLatestPools();
console.log("Latest pools:", latestPools);
```

### Get Token Information

```typescript
const tokenInfo = await agent.methods.getTokenInfo("EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v");
console.log("Token info:", tokenInfo);
```

### Get Top Gainers

```typescript
const topGainers = await agent.methods.getTopGainers("24h", "all");
console.log("Top gainers:", topGainers);
```

### Get Trending Pools

```typescript
const trendingPools = await agent.methods.getTrendingPools("24h");
console.log("Trending pools:", trendingPools);
```

### Parse Instruction Data

```typescript
const parsedData = await agent.methods.parseInstruction(
  "<programId>",
  "<instructionData>" // base64
)

console.log("parsed data:", parsedData)
```

### Parse Instruction Data

```typescript
const parsedData = await agent.methods.parseAccount(
  "<programId>",
  "<accountData>" // base64
)

console.log("parsed data:", parsedData)
```

### Get Sanctum LST Price

```typescript
const prices = await agent.methods.getSanctumLSTPrice([
  "bSo13r4TkiE4KumL71LsHTPpL2euBYLFx6h9HP3piy1",
  "7Q2afV64in6N6SeZsAAB81TJzwDoD6zpqmHkzi9Dcavn"
  ])

console.log('prices', prices)
```

### Get Sanctum LST APY

```typescript
const apys = await agent.methods.getSanctumLSTAPY([
  "bSo13r4TkiE4KumL71LsHTPpL2euBYLFx6h9HP3piy1",
  "7Q2afV64in6N6SeZsAAB81TJzwDoD6zpqmHkzi9Dcavn"
  ])

console.log('apys', apys)
```

### Get Sanctum LST TVL

```typescript
const tvls = await agent.methods.getSanctumLSTTVL([
  "bSo13r4TkiE4KumL71LsHTPpL2euBYLFx6h9HP3piy1",
  "7Q2afV64in6N6SeZsAAB81TJzwDoD6zpqmHkzi9Dcavn"
  ])

console.log('tvls', tvls)
```

### Get Sanctum Owend LST

```typescript
const lsts = await agent.methods.getSanctumOwnedLST()

console.log('lsts', lsts)
```

### Add Liquidity to Sanctum Infinite Pool

```typescript
const txId = await agent.methods.addSanctumLiquidity(
  "So11111111111111111111111111111111111111112",
  "1000000000",
  "1100000000",
  5000
)

console.log('txId', txId)
```

### Remove Liquidity from Sanctum Infinite Pool

```typescript
const txId = await agent.methods.removeSanctumLiquidity(
  "So11111111111111111111111111111111111111112",
  "1000000000",
  "1100000000",
  5000
)

console.log('txId', txId)
```

### Swap Sanctum LST

```typescript
const txId = await agent.methods.swapSanctumLST(
  "So11111111111111111111111111111111111111112",
  "1000000000",
  "1100000000",
  5000,
  "7Q2afV64in6N6SeZsAAB81TJzwDoD6zpqmHkzi9Dcavn"
)

console.log('txId', txId)
```


### Get Chain Data

Note: To use OKX DEX integration, you need to set up the following environment variables: Get OKX API keys from the [OKX Developer Portal] (https://www.okx.com/web3/build/dev-portal)
- `OKX_API_KEY`
- `OKX_SECRET_KEY`
- `OKX_API_PASSPHRASE`
- `OKX_PROJECT_ID`
- `RPC_URL`
- `SOLANA_PRIVATE_KEY`
- `SOLANA_WALLET_ADDRESS`

## Examples

### LangGraph Multi-Agent System

The repository includes an advanced example of building a multi-agent system using LangGraph and Solana Agent Kit. Located in `examples/agent-kit-langgraph`, this example demonstrates:

- Multi-agent architecture using LangGraph's StateGraph
- Specialized agents for different tasks:
  - General purpose agent for basic queries
  - Transfer/Swap agent for transaction operations
  - Read agent for blockchain data queries
  - Manager agent for routing and orchestration
- Fully typed TypeScript implementation
- Environment-based configuration

Check out the [LangGraph example](examples/agent-kit-langgraph) for a complete implementation of an advanced Solana agent system.

## Dependencies

The toolkit relies on several key Solana and Metaplex libraries:

- @solana/web3.js
- @metaplex-foundation/digital-asset-standard-api
- @coingecko/sdk

## Contributing

Contributions are completely optional! Please submit a Pull Request.


