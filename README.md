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

## Philosophy

You should control your own information diet. Algorithmic feeds optimize for the platform's goals (engagement, ad revenue), not yours (learning, understanding, growth).

This tool gives you sovereignty over how content is filtered and ranked. You define quality. You set the criteria. You audit the logic.

**Algorithmic sovereignty.** 🦅

## License

MIT

## Credits

Built by Jan Frijters with ClawdBot in February 2026.
