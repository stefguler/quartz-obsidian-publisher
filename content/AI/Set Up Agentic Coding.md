
This is a quick guide to how to set up a AI for agentic coding:

## 1. Install the AI Tool

Examples are:

- Claude Code by Anthropic: https://claude.com/product/claude-code 
- Codex by OpenAi: https://openai.com/codex/
- Gemini CLI: https://geminicli.com/
- Cursor: https://cursor.com/

All of them require a paid license, but some can be tested for a couple of days.

## 2.  Setting up your MCP's

To connect your AI with desired MCP's, you have to set them up in the config file of your AI (globally) or project. For the simplicity of this, lets look at the global:

config files of your ai are located in your C:\Users\<username>\ 
eg `C:\Users\username\.codex\config.toml` 

The problem here, is that it is not standardized, so every AI tool does it a differently. Some use `.toml` and others `.json` filetype. So just put the respective MCP configuration from the provider to your AI Tool config file. 

### 3. Configure the MCP Tools

In the context of MCP (Model Context Protocol), **tools** are structured, externally implemented capabilities that a model can invoke to perform actions beyond text generation. They are exposed by an MCP server and defined with a clear name, description, and input schema, allowing the model to call them in a standardized way. Tools typically execute operations such as querying APIs, accessing files, or interacting with external systems, and return structured results back to the model. Because they can trigger real side effects or access sensitive data, tools can be enabled or disabled depending on the environment, security requirements, or project scope. This allows controlled capability exposure and follows the principle of least privilege.

They usually can be enabled or disabled in the mcp configration itself via the "enabled_tools" property. Put the tools that should be allowed by their name in an array.

e.g.: `enabled_tools = ["search_all", "get_page", "create_new", "get_issue"]` (`.toml`)

### 4. Run your AI

Run the AI (CLI) and check whether your MCP's are connected and correctly configured. 
Usually this command inside the AI is `/mcp`. I would especially pay attention to the enabled tools here again.

### 5. Test your MCP

Now it's time to put it to practise and test your mcp's :)

