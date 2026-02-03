# Intentional YouTube

**Search YouTube with your own algorithm. No thumbnails. No recommendations. Just intent.**

## What It Does

Instead of accepting YouTube's black-box recommendation algorithm, this tool lets you:

1. **Describe what you're looking for** in natural language (be verbose!)
2. **Your own LLM translates** your intent into an optimized search query
3. **Fetches 50 results** from YouTube (not just 12)
4. **Your LLM evaluates** all 50 for quality, relevance, and absence of engagement farming
5. **Shows you the top 3-5** with explanations of WHY they match your intent

## The Pipeline

```
Your verbose query
    ↓
[Stage 1] LLM extracts key concepts → optimized YouTube query
    ↓
[Stage 2] Fetch 50 results from YouTube API (100 units)
    ↓
[Stage 3] LLM scores all 50 (negative signals, positive signals, relevance)
    ↓
[Stage 4] LLM ranks & summarizes top matches
    ↓
Top 3-5 results with reasoning + option to see all 50
```

**Cost per search:** ~$0.003-0.005 (under half a penny)

## Setup

### Requirements

- YouTube Data API v3 key ([get one here](https://console.cloud.google.com/))
- OpenAI API key ([get one here](https://platform.openai.com/api-keys))

### Quick Start

1. **Clone the repo:**
   ```bash
   git clone https://github.com/janfrijtersgroup-afk/intentional-youtube.git
   cd intentional-youtube
   ```

2. **Run locally:**
   ```bash
   python3 -m http.server 8080
   ```

3. **Open in browser:**
   ```
   http://localhost:8080
   ```

4. **Add your API keys** in the footer (stored locally in browser)

5. **Search!** Describe what you're looking for in detail.

## How It's Different

| YouTube's Algorithm | Your Algorithm |
|-------------------|---------------|
| Black box | Transparent (read the prompts) |
| Optimized for engagement | Optimized for YOUR criteria |
| Serves you 12 results | Evaluates 50, shows best 3-5 |
| No explanation | Explains WHY each video matches |
| Can't be changed | Edit the prompts! |

## Data-Driven Prompt Optimization

The tool includes a **📊 Export Results** button that saves complete search data as JSON:
- Your original query + optimized search query
- All 50 results with full metadata
- LLM scores and reasoning for each video
- Your quality observations (notes field)

**Use case:** Run 3 diverse searches, export each, then use a high-powered model (Opus 4.5, GPT-5.2) to analyze patterns and write optimized classification prompts based on real data instead of guessing.

## Customization

The LLM prompts are defined at the top of `index.html` in the `PROMPTS` object. Edit them to change how videos are evaluated:

```javascript
const PROMPTS = {
  translate: "...",  // How to convert your query to YouTube search
  classify: "...",   // How to score videos for quality/relevance
  rank: "..."        // How to summarize results
};
```

**Examples of custom criteria:**
- Prefer academic/educational content
- Avoid videos under 10 minutes
- Boost specific channels
- Penalize clickbait indicators
- Prioritize recent uploads

## Cost

- **YouTube API:** 100 units per search (10,000 free/day = 100 searches)
- **OpenAI API:** ~$0.003-0.005 per search using `gpt-4o-mini`

## Philosophy: A Manifesto for Free Won't

### The Problem

YouTube's algorithm is designed to minimize friction and maximize engagement:
- Homepage = instant scroll (no thought required)
- Recommendations optimize for watch time (their goal, not yours)
- Autoplay removes exit points (infinite consumption loop)

**You think you're choosing what to watch. You're not. You're being nudged.**

### The Insight

Free will might be an illusion, but **free won't** is real. You can't always control what you want, but you can gate whether you act on it.

**Friction is a feature, not a bug.**

### What This Tool Does Differently

Every other YouTube tool tries to make consumption easier, faster, more frictionless. This one makes it *harder*—and that's the point.

**Before you search:**
- You must articulate your intent (verbose query box)
- You must know what you're looking for
- You can't mindlessly "browse"

**The query box is a commitment device.** If you can't write 2-3 sentences about why you're here, you probably shouldn't be.

### The Architecture of Agency

| YouTube's Design | Intentional YouTube |
|-----------------|---------------------|
| Minimize entry friction | Maximize entry deliberation |
| Optimize for watch time | Optimize for YOUR criteria |
| Remove exit points | Built-in completion (you got what you came for, now leave) |

### Multi-Level Value

**Layer 1 (Technical):** Better search results, transparent algorithm, customizable scoring.

**Layer 2 (Cognitive):** Forces you to know what you're looking for before you start searching.

**Layer 3 (Behavioral):** Gating consumption with deliberation. The tool won't let you scroll mindlessly.

### Why This Matters

Attention isn't stolen—it's ceded through a thousand micro-decisions. Every "just browsing" session is a choice to let the algorithm decide for you.

This tool gives you **algorithmic sovereignty**, but the real power is at the behavioral level: it makes you think before you click.

**You're not optimizing consumption. You're optimizing agency.** 🦅

---

*If you can't articulate what you're trying to learn, you're not learning—you're being entertained.*

## License

MIT

## Credits

Built by Jan Frijters with ClawdBot in February 2026.
