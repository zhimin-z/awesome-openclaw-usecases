# arXiv Paper Reader

Reading arXiv papers means downloading PDFs, losing context when switching between papers, and struggling to parse dense LaTeX notation. You want to read, analyze, and compare papers conversationally without leaving your workspace.

This workflow turns your agent into a research reading assistant:

- Fetch any arXiv paper by ID and get clean, readable text (LaTeX flattened automatically)
- Browse paper structure first — list sections to decide what to read before committing to the full text
- Quick-scan abstracts across multiple papers to triage a reading list
- Ask the agent to summarize, compare, or critique specific sections
- Results are cached locally — revisiting a paper is instant

## Skills you Need

- [arxiv-reader](https://github.com/Prismer-AI/Prismer/tree/main/skills/arxiv-reader) skill (3 tools: `arxiv_fetch`, `arxiv_sections`, `arxiv_abstract`)
- Prismer workspace container (runs the arXiv server on port 8082)

## How to Set it Up

1. Clone and deploy [Prismer](https://github.com/Prismer-AI/Prismer) with Docker (the arXiv server starts automatically):
```bash
git clone https://github.com/Prismer-AI/Prismer.git && cd Prismer
docker compose -f docker/docker-compose.dev.yml up
```

2. The `arxiv-reader` skill is built-in — no installation needed. Prompt OpenClaw:
```text
I'm researching [topic]. Here's my workflow:

1. When I give you an arXiv ID (like 2301.00001):
   - First fetch the abstract so I can decide if it's relevant
   - If I say "read it", fetch the full paper (remove appendix by default)
   - Summarize the key contributions, methodology, and results

2. When I give you multiple IDs:
   - Fetch all abstracts and give me a comparison table
   - Rank them by relevance to my research topic

3. When I ask about a specific section:
   - List the paper's sections first
   - Then fetch and explain the relevant section in detail

Keep a running list of papers I've read and their key takeaways.
```

3. Try it: "Read 2401.04088 — what's the main contribution?"
