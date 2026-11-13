# AgentGuard

Trust and conformance checker for the Open Agentic Web. Paste any agentic site's network URL; AgentGuard reads its public `agent-manifest.json` and network file as data (never runs them), checks them against the MVP spec 0.2, scans agent instructions for prompt injection, and gives a trust score with fixes and an embeddable badge.

## Setup
1. Clone this repo (the nsDeploy browser runtime from https://github.com/cognizant-ai-labs/agentic-web is already included in `runtime/`)
2. Serve locally: `python -m http.server 8080` then open http://127.0.0.1:8080/
3. Open "AI model settings", paste your Otari key (model `alibaba/qwen-3.5-35b-a3b`), Save and start.
4. Test: scan `http://127.0.0.1:8081/pizza_restaurant_website_assistant` after serving the repo's `examples/pizza_restaurant_agentified` on port 8081.

## Files
- `agent-manifest.json`, `agentguard.network.json`: the published agent network (3 agents)
- `guard-core.js`: deterministic checks + injection heuristics
- `guard-actions.js`: site actions `scan_site`, `get_last_report` for the agents
- `index.html`, `site.js`, `ui.js`, `style.css`: the interface

## Deploy
GitHub Pages or Netlify (HTTPS). Add a `_headers` file on Netlify:
```
/*.json
  Access-Control-Allow-Origin: *
```
