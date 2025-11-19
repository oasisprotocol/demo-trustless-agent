# Oasis Trustless Agent Demo

This is a demo of a trustless AI agent built on ElisaOS. It extends
functionality with privacy features powered by [Oasis ROFL] such as key
derivation and submission of ROFL-authenticated transactions to [Sapphire].

[Oasis ROFL]: https://docs.oasis.io/build/rofl
[Sapphire]: https://docs.oasis.io/build/sapphire

# Test the Agent Locally

This will spin up an agent locally without TEE:

```shell
elizaos start
```

# Verify Current Deployment

To check whether the source code in front of you is the one currently registered
on-chain and running on the nodes, run:

```shell
oasis rofl build --verify
```

# Deploy your own instance

To build your own instance of a trustless agent, run:

```shell
oasis rofl init --reset
```

Then create a new ROFL, set secrets and deploy it.

```shell
oasis rofl create --network testnet
oasis rofl build
echo -n "<your-openai-key-here>" | oasis rofl secret set OPENAI_API_KEY -
echo -n "https://sepolia.infura.io/v3/<YOUR_KEY>" | oasis rofl secret set RPC_URL -
echo -n "<your-pinata-key-here>" | oasis rofl secret set PINATA_JWT -
oasis rofl update
oasis rofl deploy
```

# Testing it out

Obtain the URL of your agent by invoking

```shell
oasis rofl machine show
```

Look for the `Proxy:` section, for example:

```
Proxy:
  Domain: m1058.opf-testnet-rofl-25.rofl.app
  Ports from compose file:
    3000 (rofl-eliza): https://p3000.m1058.opf-testnet-rofl-25.rofl.app
```

In the setup above the agent is available on
https://p3000.m1058.opf-testnet-rofl-25.rofl.app
