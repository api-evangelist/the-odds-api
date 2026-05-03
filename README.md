# The Odds API

The Odds API provides sports betting odds from 40+ major bookmakers worldwide. Access current and historical odds across 100+ sports for head-to-head, spreads, totals, and outrights markets. Also provides live scores, event listings, and participant data. Historical odds snapshots are available from June 2020.

**Website:** [the-odds-api.com](https://the-odds-api.com/)  
**Documentation:** [the-odds-api.com/liveapi/guides/v4/](https://the-odds-api.com/liveapi/guides/v4/)  
**GitHub:** [github.com/the-odds-api](https://github.com/the-odds-api)

---

## APIs

| API | Description | Base URL |
|-----|-------------|----------|
| [The Odds API v4](https://the-odds-api.com/liveapi/guides/v4/) | Sports betting odds, scores, and events | `https://api.the-odds-api.com/v4` |

---

## OpenAPI Specifications

| Spec | File |
|------|------|
| The Odds API | [openapi/the-odds-api-openapi.yml](openapi/the-odds-api-openapi.yml) |

**Endpoints:**
- `GET /v4/sports` — List available sports (free)
- `GET /v4/sports/{sport}/odds` — Current odds from bookmakers
- `GET /v4/sports/{sport}/scores` — Live and recent scores
- `GET /v4/sports/{sport}/events` — Event listings without odds (free)
- `GET /v4/sports/{sport}/events/{eventId}/odds` — All markets for a specific event
- `GET /v4/sports/{sport}/participants` — Teams and players
- `GET /v4/historical/sports/{sport}/odds` — Historical odds snapshots
- `GET /v4/historical/sports/{sport}/events` — Historical event listings

---

## Naftiko Capabilities

### Workflow Capabilities

| Workflow | File | Description |
|----------|------|-------------|
| Sports Betting Intelligence | [capabilities/sports-betting-intelligence.yaml](capabilities/sports-betting-intelligence.yaml) | Live odds + scores + events + historical data for betting research |

### Shared Per-API Definitions

| API | File |
|-----|------|
| The Odds API | [capabilities/shared/the-odds-api.yaml](capabilities/shared/the-odds-api.yaml) |

---

## Spectral Rules

| Ruleset | File |
|---------|------|
| Odds API Rules | [rules/the-odds-api-rules.yml](rules/the-odds-api-rules.yml) |

---

## JSON Schemas

| Schema | File |
|--------|------|
| Event | [json-schema/the-odds-api-event-schema.json](json-schema/the-odds-api-event-schema.json) |

---

## JSON Structure

| Structure | File |
|-----------|------|
| Event | [json-structure/the-odds-api-event-structure.json](json-structure/the-odds-api-event-structure.json) |

---

## JSON-LD

| Context | File |
|---------|------|
| Odds API Context | [json-ld/the-odds-api-context.jsonld](json-ld/the-odds-api-context.jsonld) |

---

## Examples

| Example | File |
|---------|------|
| Get NBA Odds | [examples/the-odds-api-get-odds-example.json](examples/the-odds-api-get-odds-example.json) |

---

## Vocabulary

| Vocabulary | File |
|------------|------|
| Odds API Vocabulary | [vocabulary/the-odds-api-vocabulary.yml](vocabulary/the-odds-api-vocabulary.yml) |

---

## Authentication

Pass your API key as a query parameter on every request:

```
?apiKey=YOUR_API_KEY
```

Sign up at [the-odds-api.com/#get-access](https://the-odds-api.com/#get-access).

---

## Quota

| Request Type | Credits |
|-------------|---------|
| `/v4/sports` | 0 (free) |
| `/v4/sports/{sport}/events` | 0 (free) |
| `/v4/sports/{sport}/odds` | 1 per region per market |
| `/v4/sports/{sport}/scores` | 1 (2 with daysFrom) |
| `/v4/sports/{sport}/events/{eventId}/odds` | 1 per market per region |
| `/v4/historical/sports/{sport}/odds` | 10 per region per market |

Quota usage is returned in response headers: `x-requests-remaining`, `x-requests-used`, `x-requests-last`.

---

## Markets

| Key | Description |
|-----|-------------|
| `h2h` | Head-to-head (moneyline) — pick the winner |
| `spreads` | Point spread (handicap) — margin of victory |
| `totals` | Over/Under — combined score |
| `outrights` | Futures — winner of tournament/competition |

---

## Maintainers

**FN:** Kin Lane  
**Email:** kin@apievangelist.com

---

*Profile generated 2026-05-03*
