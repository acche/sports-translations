# 🌍 Open Sports Translations

A community-driven, open-source multi-lingual translation dictionary and API for sports entities (teams, clubs, leagues, tournaments, delegations, and players).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Total Entries](https://img.shields.io/badge/Entities-396-brightgreen.svg)](sports_translations.json)
[![Coverage](https://img.shields.io/badge/Translations-100%25%20No%20Blanks-blue.svg)](sports_translations.csv)

## 📌 Features

- **Multi-Sport Coverage**:
  - ⚽ **Football**: 306 clubs and national teams covering Premier League, La Liga, Serie A, Bundesliga, Ligue 1, EFL Championship, Campeonato Brasileiro Série A, Eredivisie, Primeira Liga, Copa Libertadores, UEFA Champions League, and FIFA World Cup.
  - 🏀 **Basketball**: Complete roster of all 30 NBA franchises.
  - 🔥 **Multi-Sport Events**: All 45 Olympic Council of Asia (OCA) National Olympic Committees for the Asian Games.
- **5 Major Languages Supported**:
  - `zh-Hans` (简体中文)
  - `zh-Hant` (繁體中文)
  - `en` (English)
  - `ja` (日本語)
  - `es` (Español)
- **Zero Blanks Guaranteed**: Every single entity contains human-verified translations across all 5 languages.
- **Comprehensive Search Aliases**: Nicknames, acronyms, common misspellings, and localized search keywords (e.g. `Juve`, `老妇人`, `尤文` for Juventus FC; `银河战舰`, `皇马` for Real Madrid).

---

## 🚀 Public CDN & API Usage

You can consume this repository directly from any web, mobile, or backend application without hosting your own translation service:

### 1. Raw GitHub API
```http
GET https://raw.githubusercontent.com/acche/sports-translations/main/sports_translations.json
```

### 2. High-Performance Global CDN (jsDelivr)
```http
GET https://cdn.jsdelivr.net/gh/acche/sports-translations@main/sports_translations.json
```

### 3. Spreadsheets & CSV
Download or inspect the tabular dataset directly:
```http
GET https://raw.githubusercontent.com/acche/sports-translations/main/sports_translations.csv
```

---

## 📐 Schema Specification

Each translation item conforms to the following JSON schema:

```json
{
  "id": "fb_se_palmeiras",
  "sport": "football",
  "type": "team",
  "canonical_name": "SE Palmeiras",
  "translations": {
    "zh-Hans": "帕尔梅拉斯",
    "zh-Hant": "彭美拉斯",
    "en": "Palmeiras",
    "ja": "パルメイラス",
    "es": "Palmeiras"
  },
  "aliases": [
    "Palmeiras",
    "SE Palmeiras",
    "帕尔梅拉斯",
    "彭美拉斯"
  ]
}
```

---

## 💻 Quick Integration Examples

### Go
```go
resp, err := http.Get("https://cdn.jsdelivr.net/gh/acche/sports-translations@main/sports_translations.json")
if err != nil {
    log.Fatal(err)
}
defer resp.Body.Close()

var payload struct {
    Translations []TranslationItem `json:"translations"`
}
json.NewDecoder(resp.Body).Decode(&payload)
```

### Swift (iOS / macOS)
```swift
let url = URL(string: "https://cdn.jsdelivr.net/gh/acche/sports-translations@main/sports_translations.json")!
let (data, _) = try await URLSession.shared.data(from: url)
let dataset = try JSONDecoder().decode(SportsTranslationResponse.self, from: data)
```

### Python
```python
import urllib.request, json

url = "https://cdn.jsdelivr.net/gh/acche/sports-translations@main/sports_translations.json"
with urllib.request.urlopen(url) as res:
    data = json.loads(res.read().decode('utf-8'))
```

---

## 🤝 Contributing

Contributions are welcome!
1. Fork this repository.
2. Add new teams, leagues, or aliases to `sports_translations.json` or `sports_translations.csv`.
3. Submit a Pull Request.

All additions must have all 5 language fields populated (no empty strings).

---

## 📄 License

MIT License © 2026 Open Sports Translations Contributors.
