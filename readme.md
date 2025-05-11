# DiversiFi AI Systems

An intelligent, wallet-aware system that analyzes any public cryptocurrency wallet address and provides personalized portfolio diversification suggestions.

![banner](https://i.imgur.com/7P2yZQo.jpeg)

## Overview

DiversiFi AI Systems is a TypeScript-based framework for creating autonomous AI driven agents who use on-chain data, market trends along with AI driven sentiment and utility analysis, the system identifies underexposed sectors, over-concentrated risks, and highlights undervalued tokens with long-term growth potential. Designed for both novice and seasoned investors, it acts as an automated crypto strategist—balancing risk, spotting emerging narratives, and recommending optimized allocations tailored to each wallet’s current holdings and market conditions.

### Key Features

- **On-Chain Data Scraping**: All on chain data is parsed and stored for the AI agents to use.
- **Evolving Persona System**: Agents can develop and adapt their knowledge over time to provide a tailored experience.
- **Utility Analysis**: Built-in analysis to help filter through whats good and what isn't! 
- **User Friendly**: Support for both novice and seasoned investors, all within your fingertips.
- **Comprehensive Logging**: Detailed ASCII art logging system with state transition tracking

## Getting Started

### Prerequisites

```bash
# Node.js v18+ required
node -v

# Install dependencies
npm install
```

### Environment Setup

Create a `.env` file with:

```env
CLAUDE_API_KEY=xxxx
IPFS_KEY=xxxx
POSTGRES_URL=xxxx
RAGIE_API_KEY=xxxx
RAGIE_API_KEY=xxxx
HELIS_SOLANA_URL=xxxx
HELIS_SOLANA_API_KEY=xxxx
```

### Basic Usage

```typescript
// Create a new persona agent
const agent = new PersonaSubAgent(
    "agent_id",
    "session_id",
    privateKeyHex
);

// Initialize with default persona
await agent.start(defaultPersona);

// Monitor state transitions
agent.getCurrentState();
agent.getEvolutionHistory();
```

### Running a Swarm

```typescript
import { startSwarm } from './swarm';

// Start multiple agents
await startSwarm(
    privateKeyHex,
    initialPersona,
    numAgents,
    "SWARM_PREFIX"
);
```

## Data Scraping

The system uses Data Scraping - with proof of state & parsing:

```typescript
interface Proof {
    stateHash: string;     // Hash of current state
    prevHash: string;      // Hash of previous state
    merkleRoot: string;    // Root of Merkle tree
    merkleProof: string[]; // Proof path
    signature: string;     // Cryptographic signature
    timestamp: number;     // Proof generation time
}
```

## Agent Evolution

Agents evolve based on a tree-based structure:

```typescript
interface PersonaStateData {
    personalityTraits: string[];
    goals: string[];
    interests: string[];
    background: string[];
    skills: string[];
    lore: string[];
    memories: string[];
    learnings: string[];
    patterns: string[];
    values: string[];
    prompt: string;
}
```

## API Endpoints

### Swarm Management

```
POST /start
{
    "privateKeyHex": string,
    "initialPersona": PersonaStateData,
    "numAgents": number,
    "agentPrefix": string
}

POST /end
```

## Database Schema

The system requires PostgreSQL with the following tables:

- `agent_personas`: Stores agent data & evolutions.
- `execution_logs`: Stores state transition logs and proofs.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Testing

```bash
npm test
```

## License

MIT License - see LICENSE file for details

## Credits

This project uses several key technologies:

- [Anthropic Claude API](https://www.anthropic.com/claude) for LLM integration
- [MerkleTreeJS](https://github.com/miguelmota/merkletreejs) for cryptographic proofs
- [Express](https://expressjs.com/) for API endpoints
- [PostgreSQL](https://www.postgresql.org/) for state storage

## Contact

For questions and support, please open an issue on GitHub.
