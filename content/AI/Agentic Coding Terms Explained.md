## Agentic Coding

**Agentic coding** is a development approach in which an AI agent does more than generate code snippets — it actively plans, executes, verifies, and iterates to achieve a defined goal. Instead of responding once to a prompt, the agent can break a task into steps and work through them autonomously.

An agentic coding system can:
- Analyze an existing codebase  
- Modify multiple files  
- Run builds or tests  
- Detect errors  
- Apply fixes iteratively  

Unlike traditional code completion, agentic coding operates in a continuous loop of reasoning and action, making it more autonomous and workflow-oriented.

### Common Tools Involved  
  
Agentic coding typically combines multiple layers of tooling:  
  
- **AI Coding Interfaces**  
- CLI-based agents (e.g., Codex CLI, Gemini CLI)  
- IDE-integrated agents (VS Code extensions, JetBrains plugins)  
  
- **MCP Servers**  
- Filesystem access  
- Git / repository integration  
- Issue tracker integrations (e.g., Bitbucket, Jira)  
- Shell execution  
- Documentation or knowledge-base connectors  
  
- **Execution & Validation Tools**  
- Test runners (e.g., `dotnet test`, `npm test`)  
- Linters and formatters  
- Build systems  
- Static analysis tools  
  
### Workflow / Methodology Approaches 

- **Spec-driven development (Spec Kit)**: define structured requirements before execution  
- **BMAD-style loops** (Break down → Make → Analyze → Decide): structured iteration cycles  
- “Ralph Wiggum” exploratory approach: fast prototyping + iterative correction  
- Test-driven prompting (define expected output before generation)  
- Plan-and-execute architectures  
  
### Key Characteristics  
  
Modern agentic coding systems emphasize:  
  
- Iterative reasoning + action loops  
- Tool orchestration via MCP or similar protocols  
- Least-privilege tool scoping  
- Automated verification (tests/build checks)  
- Clear separation between planning, execution, and validation  
  
The current state of the art combines structured planning, controlled tool access, automated validation, and iterative refinement to create semi-autonomous development workflows.

### Skills

In AI systems, **skills** are higher-level capability bundles that package prompts, tool access, and behavioral rules into a reusable unit. A skill defines _what an agent is good at_ (e.g., “code reviewer,” “ticket triage,” “deployment assistant”) and may internally use one or more tools to perform its job. While tools are low-level execution functions (e.g., call API, read file), skills orchestrate reasoning + tool usage toward a specific goal. Assigning skills to an agent constrains and specializes its behavior, improving reliability and reducing unnecessary tool access. This allows agents to be purpose-built and scoped according to project requirements.
#### Agent Configuration

Skills are typically defined at the **agent configuration layer**, not inside the model itself.  
They are declared in configuration files (e.g., YAML, JSON, TOML) or in the application’s orchestration code.

A skill assignment usually specifies which capabilities an agent is allowed to use.

#### Example

```yaml
agent:
  name: CodeReviewer
  skills:
    - repo_search
    - diff_analysis
    - comment_generator
```
      

---
## Model Context Protocol (MCP)

**MCP (Model Context Protocol)** is a standard interface that lets an AI model interact with external capabilities (e.g., APIs, files, internal services) through **MCP servers**. MCP defines how these servers expose **tools** (callable actions) and other context in a structured way, while the model focuses on reasoning and decision-making. This separation makes integrations modular, easier to maintain, and safer to control. MCP servers can be enabled or disabled to scope access, reduce risk, and follow least-privilege principles.

#### Example: MCP Configuration (TOML)

```toml
# ~/.codex/config.toml (example)
[mcp_servers.bitbucket]
command = "npx"
args = ["-y", "@nexus2520/bitbucket-mcp-server"]
env = { 
  BITBUCKET_URL = "https://bitbucket.example.com",
  BITBUCKET_TOKEN = "..."
}

[mcp_servers.obsidian]
command = "npx"
args = ["-y", "obsidian-mcp-server"]
env = {
  VAULT_PATH = "C:/Users/you/Documents/ObsidianVault"
}
```

### MCP Tools

In the context of MCP, **tools** are structured capabilities exposed by an MCP server that a model can invoke to perform concrete actions. Each tool is defined with a name, description, and input schema, allowing the model to call it in a standardized and type-safe way. Tools typically execute operations such as querying APIs, reading files, running commands, or interacting with external systems, and return structured results. Because tools can produce real side effects or access sensitive resources, they can be enabled or disabled depending on environment, security requirements, or project scope.

#### Example: Tool Definition (Conceptual JSON)

```json
{
  "name": "searchRepositories",
  "description": "Search repositories by name or keyword",
  "inputSchema": {
    "type": "object",
    "properties": {
      "query": { "type": "string" },
      "limit": { "type": "number" }
    },
    "required": ["query"]
  }
}
```

### Enabling and Disabling Specific Tools

In MCP-based setups, tools are exposed by an MCP server, but you can often **restrict which of those tools are available to the model**. Instead of disabling the entire server, you explicitly whitelist specific tools. This allows fine-grained capability control while still using the same MCP backend.

Only the tools listed in `enabled_tools` (or similar configuration fields, depending on the client) are visible and callable by the model. All other tools exposed by the server remain inaccessible.

It is considered good practice to disable **destructive tools** (e.g., delete operations, force pushes, database mutations) unless they are explicitly required. Limiting access to non-destructive or read-only tools reduces security risks and follows the principle of least privilege.

#### Example: Enable Specific Tools (TOML)

```toml
[mcp_servers.bitbucket]
command = "npx"
args = ["-y", "@nexus2520/bitbucket-mcp-server"]

enabled_tools = [
  "searchRepositories",
  "getPullRequest"
]
```

---