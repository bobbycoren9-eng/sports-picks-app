# DraftKings Player Prop Command Center

This project is a single-page dashboard that locks onto DraftKings player props via [The Odds API](https://the-odds-api.com/) and automatically assembles high-upside bet builder cards with implied probability and payout projections.

## Prerequisites
- A modern web browser (Chrome, Edge, Firefox, or Safari)
- A The Odds API account with an API key that has access to the markets you want (player props require the paid plan)

## Running the dashboard locally
1. Clone or download this repository.
2. Start a simple web server in the project directory (any static server works). A quick option with Python is:
   ```bash
   python3 -m http.server 8000
   ```
3. Open your browser to [http://localhost:8000/index.html](http://localhost:8000/index.html).
4. Click **🔐 Set API Key** in the header and paste your The Odds API key.
5. After saving the key the board will automatically fetch the latest DraftKings props and parlay cards. You can click **🔄 Refresh Live Feed** whenever you want to pull a fresh snapshot.

> **Tip:** Your API key is stored in `localStorage` so you only need to set it once per browser. If props are missing, verify that your API plan supports the `player_props` market and that DraftKings has published lines for the slate.

## Customising the feed
- Update the `PLAYER_PROP_SPORTS` array in `index.html` to cover the leagues you care about.
- Tweak `PARLAY_LEG_SIZE`, `MAX_PARLAYS`, `PARLAY_CANDIDATE_POOL`, or `MAX_VISIBLE_PROPS` to control how aggressive the bet builder and prop rail are.

## Troubleshooting
- **No data / empty tiles:** Make sure your API key is correct and has enough remaining requests. The status indicator will warn you if a key is missing.
- **CORS errors:** Use a local web server as shown above instead of opening the file directly with the `file://` protocol.
- **Prop gaps:** DraftKings typically posts props closer to game time. Refresh later in the day or expand the league list if you are targeting additional slates.
