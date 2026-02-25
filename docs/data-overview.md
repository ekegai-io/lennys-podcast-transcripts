# Data Overview

A reference document for the structure, metadata, and key stats of the Lenny's Podcast transcript dataset.

---

## Counts

| Metric | Value |
|---|---|
| Total episodes | 303 |
| Episodes with topic index | 269 |
| Topic categories | 88 |
| Total transcript lines | ~197,000 |
| Average lines per transcript | ~1,300 |
| Date range | 2022 – 2026 |

---

## File Structure

Each episode lives at:

```
episodes/{guest-name}/transcript.md
```

The file is a Markdown document with YAML frontmatter followed by a timestamped transcript.

---

## Frontmatter Fields

Every transcript begins with a YAML block. Here is the complete list of fields:

| Field | Type | Example |
|---|---|---|
| `guest` | string | `Sean Ellis` |
| `title` | string | `The original growth hacker reveals his secrets \| Sean Ellis` |
| `youtube_url` | string | `https://www.youtube.com/watch?v=VjJ6xcv7e8s` |
| `video_id` | string | `VjJ6xcv7e8s` |
| `publish_date` | YYYY-MM-DD | `2024-09-05` |
| `description` | string | Short episode summary |
| `duration_seconds` | float | `6266.0` |
| `duration` | H:MM:SS | `1:44:26` |
| `view_count` | integer | `38230` |
| `channel` | string | `Lenny's Podcast` (always) |
| `keywords` | string[] | `[growth, retention, onboarding, ...]` |

**Notes:**
- `keywords` are AI-generated (10–20 tags per episode) and power the topic index
- `view_count` reflects the count at time of archiving, not live
- Some older episodes have `publish_date: 2022-01-01` as a placeholder (not the actual air date)

---

## Transcript Format

After the frontmatter, transcripts follow this pattern:

```
# Episode Title

## Transcript

Speaker Name (HH:MM:SS):
Dialogue text...

Speaker Name (HH:MM:SS):
Dialogue text...
```

Speakers are Lenny Rachitsky (host) and the guest(s). Timestamps are wall-clock time into the episode.

---

## Topic Index

The `index/` folder contains one `.md` file per topic. Each file lists all episodes tagged with that keyword.

### Top topics by episode count

| Topic | Episodes |
|---|---|
| Product Management | 142 |
| Leadership | 73 |
| Entrepreneurship | 52 |
| Product Strategy | 52 |
| Product Development | 46 |
| Career Development | 40 |
| Growth Strategy | 33 |
| Startup Growth | 24 |
| Product-Led Growth | 23 |
| Company Culture | 22 |
| Venture Capital | 21 |
| Decision Making | 21 |
| Team Building | 20 |
| Hiring | 19 |
| Google | 18 |
| Experimentation | 17 |
| Facebook | 15 |
| AB Testing | 14 |
| Innovation | 12 |
| Product-Market Fit | 11 |

### Company / brand topics

Airbnb (10), ChatGPT (9), Microsoft (9), Stripe (9), Uber (9), OpenAI (10), Meta (8), Slack (8)

### Softer / personal topics

Anxiety Management, Mental Health, Neuroscience, Personal Transformation, Work-Life Balance, Stress Management, Creativity, Psychology, Storytelling

---

## Episode Duration

- Typical range: 1:00:00 – 1:54:00
- Most episodes cluster around 1:20:00 – 1:45:00
- Shortest indexed: ~1:02:00
- Longest indexed: ~2:29:00 (Kunal Shah, 2,409 lines)

---

## Data Quality Notes

- 34 episodes exist in `episodes/` but are **not yet indexed** in the topic files
- `view_count` is `0` for some older episodes (not fetched at archiving time)
- Some `publish_date` values may be approximate (placeholder `2022-01-01`)
- Episode directory names use kebab-case guest names (e.g., `sean-ellis/`)
