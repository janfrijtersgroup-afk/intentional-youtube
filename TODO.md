# TODO - Intentional YouTube Enhancements

*Feature backlog for deepening ontological hygiene*

---

## A. Enhanced Content Summaries (LLM-Powered)

**Goal:** Preview video content quality/relevance before watching

**Approach:**
- Fetch YouTube transcript via API
- Send to LLM with user's search query
- Generate relevance score + summary
- Display: "This video covers X, Y, Z — relevance to your query: high/medium/low"

**Implementation notes:**
- YouTube Transcript API or `youtube-transcript-api` (Python)
- LLM call (Claude, GPT, local model)
- Privacy consideration: transcripts go to LLM — could run locally or use privacy-focused API
- Cost consideration: LLM API calls per result (batch? selective?)

**Questions:**
- Which LLM? (Local, OpenAI, Anthropic)
- When to summarize? (All results? On-demand per result?)
- Privacy vs convenience tradeoff?

---

## B. Defeat Behavioral Nudging in API Results

**Goal:** Reduce IP/search history shaping of results

**Known vectors of manipulation:**
1. **Personalization based on IP/location**
2. **Search history tracking** (if API key is tied to Google account)
3. **Result ordering** (YouTube's relevance algorithm)

**Potential mitigations:**

### B1. IP Obfuscation
- Route API calls through proxy/VPN
- Rotate IPs to prevent profile building
- Use Tor or privacy-focused proxy services

### B2. API Key Isolation
- Use project-specific API key (not tied to personal Google account)
- Periodically rotate API keys
- Document "burner key" strategy

### B3. Result Re-Ranking
- Fetch more results than displayed (e.g., top 50)
- Re-rank locally by:
  - Pure chronological (newest first)
  - View count (popular vs niche)
  - Channel size (favor small creators vs algorithmic winners)
  - Random shuffle (defeat ordering bias)
- User chooses ranking strategy

### B4. Query Neutralization
- Strip personalization hints from search queries
- Add noise queries to confuse profiling
- Document "clean search" practices

### B5. Metadata Analysis
- Track which results get recommended over time
- Identify patterns in API response ordering
- Build transparency layer: "This result ranked #3, but chronologically it's #12"

---

## C. Additional Enhancements (Future)

### C1. Transcript Search
- Search *within* transcripts, not just titles/descriptions
- Find exact moments where concepts are discussed

### C2. Channel Blocklist
- User-defined channel blocklist
- Filter out channels known for clickbait/manipulation

### C3. Keyboard Navigation
- Full keyboard control (j/k for results, Enter to play)
- Accessibility improvement

### C4. Watch Later / Bookmarks
- Local storage bookmarking system
- Export as plain text list of URLs

### C5. Export Search History
- Log your searches + what you chose to watch
- Personal data sovereignty (you own the log)

---

## Implementation Priorities

**Phase 1 (Quick Wins):**
- [ ] TODO.md (this file) ✅
- [ ] Result re-ranking options (B3)
- [ ] Keyboard navigation (C3)

**Phase 2 (Privacy Layer):**
- [ ] API key rotation strategy docs (B2)
- [ ] Proxy/VPN guide (B1)
- [ ] Result ordering transparency (B5)

**Phase 3 (LLM Integration):**
- [ ] Transcript fetching (A)
- [ ] LLM summarization (A)
- [ ] Privacy/cost decisions (A)

**Phase 4 (Advanced):**
- [ ] Transcript search (C1)
- [ ] Channel blocklist (C2)
- [ ] Watch later / bookmarks (C4)

---

## Contributing Notes

This is a personal tool, but ideas/PRs welcome if you share the ontological hygiene ethos.

Focus: agency, intentionality, transparency, privacy.
Reject: growth metrics, engagement optimization, dark patterns.
