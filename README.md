# The Odds API

The Odds API aggregates live and historical sports betting odds from 40+ major bookmakers worldwide across 70+ sports. The v4 REST API covers head-to-head (moneyline), point spreads, totals (over/under), outrights/futures, player props, and alternate lines, plus live scores, event listings, participants, and historical snapshots dating back to June 2020.

Operated since 2017 from Melbourne, Australia. Quota is consumed per request based on the number of regions and markets requested.

**Website:** [the-odds-api.com](https://the-odds-api.com/)
**Documentation:** [the-odds-api.com/liveapi/guides/v4/](https://the-odds-api.com/liveapi/guides/v4/)
**GitHub:** [github.com/the-odds-api](https://github.com/the-odds-api)
**Status:** [status.the-odds-api.com](https://status.the-odds-api.com/)

---

## APIs

| API | Description | Base URL |
|-----|-------------|----------|
| [The Odds API v4](https://the-odds-api.com/liveapi/guides/v4/) | Sports betting odds, scores, events, and historical snapshots | `https://api.the-odds-api.com/v4` |

---

## OpenAPI Specifications

| Spec | File |
|------|------|
| The Odds API | [openapi/the-odds-api-openapi.yml](openapi/the-odds-api-openapi.yml) |

### Endpoints

| Method | Path | Quota | Description |
|--------|------|-------|-------------|
| GET | `/v4/sports` | Free | List available sports |
| GET | `/v4/sports/{sport}/odds` | 1 per region per market | Current odds across bookmakers |
| GET | `/v4/sports/{sport}/scores` | 1 (2 with `daysFrom`) | Live and recent scores |
| GET | `/v4/sports/{sport}/events` | Free | Event listings without odds |
| GET | `/v4/sports/{sport}/events/{eventId}/odds` | 1 per market per region | All markets for a specific event |
| GET | `/v4/sports/{sport}/events/{eventId}/markets` | 1 | Available markets per bookmaker |
| GET | `/v4/sports/{sport}/participants` | 1 | Teams and players for a sport |
| GET | `/v4/historical/sports/{sport}/odds` | 10 per region per market | Historical odds snapshots |
| GET | `/v4/historical/sports/{sport}/events` | 1 (free if empty) | Historical event listings |
| GET | `/v4/historical/sports/{sport}/events/{eventId}/odds` | 1 per market per region | Historical odds for a single event |

---

## Naftiko Capabilities

One self-contained capability per OpenAPI tag (REST + MCP exposers).

| Capability | File |
|------------|------|
| Sports | [capabilities/the-odds-sports.yaml](capabilities/the-odds-sports.yaml) |
| Odds | [capabilities/the-odds-odds.yaml](capabilities/the-odds-odds.yaml) |
| Scores | [capabilities/the-odds-scores.yaml](capabilities/the-odds-scores.yaml) |
| Events | [capabilities/the-odds-events.yaml](capabilities/the-odds-events.yaml) |
| Participants | [capabilities/the-odds-participants.yaml](capabilities/the-odds-participants.yaml) |
| Historical | [capabilities/the-odds-historical.yaml](capabilities/the-odds-historical.yaml) |

---

## Spectral Rules

| Ruleset | File |
|---------|------|
| Odds API Rules | [rules/the-odds-api-rules.yml](rules/the-odds-api-rules.yml) |

---

## JSON Schema, Structure, and JSON-LD

| Artifact | File |
|----------|------|
| Event Schema | [json-schema/the-odds-api-event-schema.json](json-schema/the-odds-api-event-schema.json) |
| Event Structure | [json-structure/the-odds-api-event-structure.json](json-structure/the-odds-api-event-structure.json) |
| JSON-LD Context | [json-ld/the-odds-api-context.jsonld](json-ld/the-odds-api-context.jsonld) |

---

## Examples and Vocabulary

| Artifact | File |
|----------|------|
| Get NBA Odds Example | [examples/the-odds-api-get-odds-example.json](examples/the-odds-api-get-odds-example.json) |
| Odds API Vocabulary | [vocabulary/the-odds-api-vocabulary.yml](vocabulary/the-odds-api-vocabulary.yml) |

---

## Commercial Artifacts

| Artifact | Specification | File |
|----------|---------------|------|
| Plans & Pricing | API Commons Plans 0.1 | [plans/the-odds-api-plans-pricing.yml](plans/the-odds-api-plans-pricing.yml) |
| Rate Limits | API Commons Rate Limits 0.1 | [rate-limits/the-odds-api-rate-limits.yml](rate-limits/the-odds-api-rate-limits.yml) |
| FinOps | FOCUS / FinOps Framework | [finops/the-odds-api-finops.yml](finops/the-odds-api-finops.yml) |

---

## Authentication

Pass the API key as a query parameter on every request:

```
?apiKey=YOUR_API_KEY
```

Sign up at [the-odds-api.com/#get-access](https://the-odds-api.com/#get-access). All endpoints require an API key except where noted as free.

---

## Pricing Tiers

| Plan | Cost | Monthly Credits |
|------|------|-----------------|
| Starter | Free | 500 |
| 20K | $30 / month | 20,000 |
| 100K | $59 / month | 100,000 |
| 5M | $119 / month | 5,000,000 |
| 15M | $249 / month | 15,000,000 |

Credits are consumed per request based on regions and markets requested. Free endpoints (`/sports`, `/events`) consume no credits, and responses with empty data do not count toward quota.

---

## Rate-Limit Headers

| Header | Description |
|--------|-------------|
| `x-requests-remaining` | Credits remaining until quota reset |
| `x-requests-used` | Credits consumed since last reset |
| `x-requests-last` | Cost of the last API call |

`429 Too Many Requests` is returned when the quota is exceeded.

---

## Markets

| Key | Description |
|-----|-------------|
| `h2h` | Head-to-head (moneyline) — pick the winner |
| `spreads` | Point spread / handicap — margin of victory |
| `totals` | Over/Under — combined score |
| `outrights` | Futures — winner of tournament/competition |
| `player_props` | Player propositions (selected US sports & books) |
| `alternate_spreads` / `alternate_totals` | Alternate lines (selected sports) |

---

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

---

*Profile last refreshed 2026-05-25*
