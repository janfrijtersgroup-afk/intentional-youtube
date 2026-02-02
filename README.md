# Intentional YouTube Search

A minimal interface that restores agency in how you search and watch.  
No recommendations. No thumbnails. No algorithmic nudging.

## Philosophy

The default YouTube UI is optimized for attention capture.  
This interface is optimized for intention.

- Search only
- Text-only results
- You decide what to play

## Setup

1. Open `index.html` in your browser.
2. Paste your YouTube Data API v3 key into the "Paste YouTube API Key" field.
3. Click "Save Key".
4. Search.

The key is stored locally in `localStorage` in your browser. No server required.

## Getting a YouTube API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project
3. Enable **YouTube Data API v3**
4. Create an API key (Credentials → Create Credentials → API key)

Free tier: 10,000 quota units/day (~100 searches)

## Notes

- This is a static file. It works locally with no build step.
- If you exceed quota or the key is invalid, results will fail to load.
- No data leaves your machine except API calls to YouTube.

## Philosophy: Ontological Hygiene

Algorithmic recommendation systems optimize for engagement metrics, not your goals. They:
- Use visual thumbnails engineered for maximum click-through
- Present endless sidebars to extend session duration
- Employ autoplay and infinite scroll to maximize watch time

This tool inverts the relationship: **you** decide what to watch based on textual information, without visual manipulation.

An agentic tool for self-determination.
