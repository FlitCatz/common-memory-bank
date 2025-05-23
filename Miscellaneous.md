# Miscellaneous
Other miscellany

## MCP

Our favorite MCPs to default to when it comes to development

### Taskmaster AI

- MCPs required by this repository
- Taskmaster AI site: [https://www.task-master.dev/](https://www.task-master.dev/)
- install 
```bash
npm install -g task-master-ai #Install globally
npm install task-master-ai #Local install
```

### browser-tools
- MCP to give access to Chrome Developer Tools (captures screenshots, console logs, network activity, Lighthouse, and DOM elements)
- Git repo: [https://github.com/AgentDeskAI/browser-tools-mcp](https://github.com/AgentDeskAI/browser-tools-mcp)
- In addition to MCP, you'll need to install the local server (Node.js) and Chrome Extension for this to work.
- Requires always running Command for server
```bash
npx @agentdeskai/browser-tools-server@latest
```
> **Example Queries:**
> - "Are there any accessibility issues on this page?"
> - "Run an accessibility audit."
> - "Check if this page meets WCAG standards."
> - "Why is this page loading so slowly?"
> - "Run an SEO audit."
> - "Run a NextJS audit."
> - "Enter debugger mode."
