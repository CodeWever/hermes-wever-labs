# Wever Labs for Hermes Agent

Check whether an agent is ready for a job, review its oversight evidence, look up job records, and run treasury checks from Hermes Agent. One install connects both Wever Labs catalogs.

| Server | Hosted endpoint | Tools | Price |
| --- | --- | ---: | --- |
| `wever-labs` | [weverlabs.com/mcp](https://weverlabs.com/mcp) | 226 | Paid tools cost 0.10 USDC per call on Base via x402 |
| `wever-labs-free` | [weverlabs.com/mcp-free](https://weverlabs.com/mcp-free) | 30 | Free |

## Install

```sh
hermes plugins install CodeWever/hermes-wever-labs --no-enable
hermes plugins enable wever-labs
```

Start a new Hermes session or run `/reload-mcp` in an open session. Both catalogs support tool discovery without payment. Ask Hermes to list the available Wever Labs tools or start by comparing expected and available evidence with the free catalog.

## Connections and payments

Hermes sends tool requests and their inputs to the two Wever Labs endpoints over Streamable HTTP. Wever Labs serves the tool definitions at runtime. The two declarative JSON manifests connect both servers without local credentials. Individual tools use the permissions described in their tool definitions. Both connections use Hermes's `untrusted` setting, which prompts before write-capable tool calls.

For a paid tool, Wever Labs returns an x402 payment challenge in the MCP result. To complete payment, use an x402-capable MCP client that reads the full result, authorizes the payment in USDC on Base and retries with a `PAYMENT-SIGNATURE` header.

## License

MIT
