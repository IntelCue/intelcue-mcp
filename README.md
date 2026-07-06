# IntelCue MCP Server

**Live market & competitor intelligence inside Claude and any MCP-compatible AI assistant.**

[IntelCue](https://www.intelcue.ai) is an AI-first competitive and market intelligence
platform. It continuously monitors your sources — newsletters, blogs, LinkedIn profiles,
news, YouTube, websites, Google Ads, patents, and SEC filings — then analyzes everything for
trending topics, competitive moves, keywords, and influencer activity. This repository
documents the **IntelCue MCP server**, which exposes that intelligence to AI assistants via
the [Model Context Protocol](https://modelcontextprotocol.io).

> Ask your AI assistant about your market and competitors, and it pulls from your live,
> continuously-updated IntelCue data automatically. Learn more at
> **[www.intelcue.ai](https://www.intelcue.ai)**.

## What is the IntelCue MCP server?

A hosted, remote MCP server (Streamable HTTP) that gives AI assistants read-only access to
your IntelCue workspace. It scopes every response to your authenticated workspace, so your
data stays private to you.

- **Endpoint:** `https://api.intelcue.ai/v1/mcp/sse`
- **Transport:** Streamable HTTP (official MCP SDK)
- **Auth:** your IntelCue API key (`ic_sk_…`) — via OAuth, `Authorization: Bearer`, or the
  `x-api-key` header

## Connect

### Option 1 — Smithery (easiest)

Install from the [Smithery listing](https://smithery.ai) and paste your IntelCue API key when
prompted.

### Option 2 — Claude Desktop

```json
{
  "mcpServers": {
    "intelcue": {
      "type": "url",
      "url": "https://api.intelcue.ai/v1/mcp/sse",
      "name": "IntelCue",
      "authorization": "Bearer ic_sk_your_api_key_here"
    }
  }
}
```

### Option 3 — Any MCP client (header auth)

Send your key in the `x-api-key` header to `https://api.intelcue.ai/v1/mcp/sse`.

**Get your API key** on the Connect page in your [IntelCue dashboard](https://www.intelcue.ai).

## Tools

All tools are read-only and automatically scoped to your workspace.

| Tool | What it returns |
|------|-----------------|
| `get_trending_topics` | Trending topics with momentum scores, change deltas, and examples |
| `get_competitive_insights` | Competitive alerts ranked by severity |
| `get_keywords` | Keywords & hashtags with volume and trend direction |
| `get_influencer_insights` | Activity analysis for monitored LinkedIn profiles |
| `get_newsletter_content` | Recent newsletter content from subscribed sources |
| `get_blog_updates` | Latest posts from monitored blogs |
| `get_linkedin_posts` | Recent posts from monitored LinkedIn profiles |
| `get_patent_filings` | Recent patent filings and grants from monitored companies |
| `get_front_page_brief` | The latest AI-generated weekly Front Page brief for your workspace |

## Example questions to ask your assistant

- "What are the top trending topics in my market this week?"
- "Any high-severity competitive moves in the last 7 days?"
- "Which keywords are surging right now, with hashtags?"
- "Summarize the latest newsletters and blog posts from my competitors."
- "Have any tracked companies filed patents recently?"
- "Pull my latest Front Page brief and summarize it."

## Learn more

- **Product:** [www.intelcue.ai](https://www.intelcue.ai)
- **Competitive intelligence:** [intelcue.ai/solutions/competitive-intelligence](https://www.intelcue.ai/solutions/competitive-intelligence)
- **Google Ads transparency:** [intelcue.ai/solutions/google-ads-transparency](https://www.intelcue.ai/solutions/google-ads-transparency)
- **Newsletter tracking:** [intelcue.ai/solutions/newsletter-tracker](https://www.intelcue.ai/solutions/newsletter-tracker)
- **Website change tracking:** [intelcue.ai/solutions/website-change-tracker](https://www.intelcue.ai/solutions/website-change-tracker)
- **Blog:** [intelcue.ai/blog](https://www.intelcue.ai/blog)

## FAQ

**What is IntelCue?**
An AI-first market and competitive intelligence platform that monitors your sources and
delivers insights into Claude or any AI assistant via MCP. See [www.intelcue.ai](https://www.intelcue.ai).

**Do I need an account?**
Yes. The MCP server returns data scoped to your IntelCue workspace, so you need an IntelCue
account and API key (`ic_sk_…`) from the Connect page.

**Which AI assistants are supported?**
Any MCP-compatible client — Claude Desktop, Claude.ai, and others via the
[Model Context Protocol](https://modelcontextprotocol.io).

**Is my data shared?**
No. Every tool call is scoped to your own workspace.

---

© IntelCue. Website: [https://www.intelcue.ai](https://www.intelcue.ai)
