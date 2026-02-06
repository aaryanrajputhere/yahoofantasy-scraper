# Yahoo Fantasy Basketball Scraper

A web scraping tool that extracts player statistics and news from Yahoo Fantasy Basketball leagues. It automates collection of player data across multiple statistical categories and exports to Excel spreadsheets.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Data Output](#data-output)
- [Troubleshooting](#troubleshooting)

## Overview

This project uses browser automation to scrape player data from Yahoo Fantasy Basketball leagues. It authenticates using saved cookies, navigates through different statistical categories, and extracts player information including news updates. The scraped data is exported to Excel files.

## Features

- **Cookie-based Authentication**: Maintains logged-in sessions using saved cookies
- **Multi-Category Stats Scraping**: Cycles through all available stat categories
- **Pagination Handling**: Navigates through multiple pages of player listings
- **Player News Extraction**: Retrieves latest player news and updates
- **Comprehensive Stats**: Collects detailed statistics including:
  - Player name and link
  - Roster status (FA, Waivers, etc.)
  - NBA team
  - Fantasy points
  - Per-game stats (MPG, PTS, REB, AST, ST, BLK, TO)
  - Player notes and news
- **Excel Export**: Organizes data into multi-sheet Excel workbooks
- **Dynamic Content Loading**: Waits for dynamic content to fully load before extraction

## Tech Stack

- **Python 3.x**
- **Playwright** - Browser automation
- **Pandas** - Data manipulation
- **XlsxWriter** - Excel generation
- **Pickle** - Cookie storage

## Installation

```bash
pip install playwright pandas xlsxwriter
playwright install chromium
```

**Requirements:** Python 3.7+, Yahoo Fantasy Basketball account

## Usage

### 1. Save Cookies

```bash
python cookies.py
```
Log in when browser opens, wait 60 seconds, cookies save automatically.

### 2. Run Scraper

```bash
python main.py
```
Extracts all player data and saves to Excel.

### 3. Test Mode (Optional)

```bash
python test.py
```
Runs limited version for testing.

### Sample Data

The repository includes `player_data_with_news_by_stat.xlsx` as sample output showing the format and structure of scraped data.

## Configuration

**Update League ID:**
```python
url = "https://basketball.fantasysports.yahoo.com/nba/YOUR_LEAGUE_ID/players"
```
Replace `969` with your league ID from the URL.

**Headless Mode:**
```python
browser = p.chromium.launch(headless=True)  # Runs in background
```

## Data Output

Excel file with multiple sheets (one per stat category):
- Season Stats
- Last 7 Days, 14 Days, 30 Days
- Projected Stats
- More categories as available

### Columns

| Column | Description |
|--------|-------------|
| `name` | Player's full name |
| `link` | URL to player's Yahoo profile |
| `roster_status` | Roster availability (FA, Waivers, Rostered) |
| `nba_team` | Player's NBA team abbreviation |
| `fan_points` | Fantasy points |
| `per_ros_value` | Per-game Rest of Season value |
| `mpg` | Minutes per game |
| `pts` | Points per game |
| `reb` | Rebounds per game |
| `ast` | Assists per game |
| `st` | Steals per game |
| `blk` | Blocks per game |
| `to` | Turnovers per game |
| `player_notes` | Latest player news and updates (test.py only) |

## Notes

- Cookies expire after inactivity - re-run `cookies.py` if authentication fails
- Browser runs in visible mode by default for debugging
- Script includes delays to respect Yahoo's servers
- Adjust timeouts if you have slow connection

## Troubleshooting

**Authentication Errors:** Re-run `cookies.py`

**Element Not Found:** Yahoo updated their HTML - inspect page and update selectors

**Timeout Errors:** Increase timeout values or check connection

**Browser Not Found:** Run `playwright install chromium`

## Disclaimer

For educational and personal use only. Comply with Yahoo's Terms of Service. Use responsibly.
