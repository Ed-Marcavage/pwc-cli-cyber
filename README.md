# Papers With Code Cyber — CLI and MCP

Search cybersecurity papers, code, and benchmarks through CLI or MCP. Find AI pentesting tools and security agent harnesses for code audit, vulnerability discovery, fuzzing, and reverse engineering in the Papers With Code Cyber catalog.

Connect an AI assistant to the read-only MCP server or query from your terminal, with links to original papers and repositories.

[Browse the website](https://paperswithcode-cyber.com) ·
[MCP setup](https://paperswithcode-cyber.com/mcp) ·
[Website source](https://github.com/Ed-Marcavage/paperswithcode-cyber) ·
[Report an issue](https://github.com/Ed-Marcavage/pwc-cli-cyber/issues)

[![Browse cybersecurity papers, code, and benchmarks in Papers With Code Cyber](https://raw.githubusercontent.com/Ed-Marcavage/paperswithcode-cyber/d9d7467dc8be7ed72c769da85bc832727212a094/docs/media/catalog-preview.gif)](https://paperswithcode-cyber.com)

- Prefer the web UI? [Explore Papers With Code Cyber](https://paperswithcode-cyber.com) to browse and filter the same catalog available through CLI and MCP.

This is the Cyber fork of [Hugging Face's pwc-cli](https://github.com/huggingface/pwc-cli).
The hosted Cyber catalog and MCP are public and read-only; neither requires an
account or API key.

## Connect your agent

Use the Streamable HTTP endpoint:

```text
https://paperswithcode-cyber.com/mcp
```

For clients that accept an `mcpServers` configuration:

```json
{
  "mcpServers": {
    "paperswithcode-cyber": {
      "url": "https://paperswithcode-cyber.com/mcp"
    }
  }
}
```

Search by title or topic, browse the catalog's taxonomy, inspect original code
links, and read cached paper text when available. See the
[setup page](https://paperswithcode-cyber.com/mcp) for client-specific instructions
and the [personal-agent prompt](https://paperswithcode-cyber.com/personal-agents)
for a daily research pick.

## Use the CLI

Install from this fork with Python 3.10+ and `uv`, then explicitly select the
Cyber API. The shared CLI retains its upstream default when `PWC_API_URL` is unset.

```bash
uv tool install 'git+https://github.com/Ed-Marcavage/pwc-cli-cyber.git#subdirectory=standalone_cli'
export PWC_API_URL=https://paperswithcode-cyber.com/api/v1
pwc search EVMbench --mode keyword --limit 5
pwc paper info 2603.04915 --include-resources
pwc paper read 2603.04915
pwc organization list --featured-only
```

Use keyword search with the Cyber catalog. Add `--json` for structured output.
The command remains `pwc`. Source installation is documented here because this
fork does not currently publish its own prebuilt binaries.

## Source and local development

- [`standalone_cli`](standalone_cli): the shared API client and command reference.
- [`mcp_server`](mcp_server): the base read-only MCP server.
- [Cyber MCP build](https://github.com/Ed-Marcavage/paperswithcode-cyber/blob/main/local-dev/README.md): the reproducible hosted profile, including the catalog/developer tools, site links, and optional analytics. Its reviewed changes live in `local-dev/mcp.patch` and `local-dev/mcp_analytics.py` in the website repository.

The website's Compose build pins this repository to a specific revision before
applying the Cyber profile. Running the base server alone is not the full hosted
Cyber configuration. Upstream paper-editing commands are not enabled on the
public Cyber API.

## Feedback

For CLI or MCP issues, [open an issue here](https://github.com/Ed-Marcavage/pwc-cli-cyber/issues).
For website issues or catalog features, use
[the website repository](https://github.com/Ed-Marcavage/paperswithcode-cyber/issues).

## License

Apache-2.0, as declared in the package metadata. Original upstream attribution is preserved.
