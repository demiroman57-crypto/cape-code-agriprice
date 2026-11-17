# African Farmer Market USSD

A hackathon MVP demonstrating multilingual USSD access to agricultural market prices.

## Features
- USSD language selection: English, isiZulu, isiXhosa, Sesotho, Afrikaans and Kiswahili.
- Commodity price lookup for tomatoes, maize and potatoes.
- Price comparison and highest reported price.
- FastAPI endpoint compatible with Africa's Talking form callback.
- Browser-based simulator.
- SQLite persistence and pytest tests.

## Important demo-data warning
The application seeds illustrative prices for the demo. They are NOT live, verified or recommended selling prices. Replace them with a reliable market data feed or verified market-agent submissions before real-world use. Prices need source, grade, market, unit, currency and timestamp metadata.

## Requirements
Python 3.10 or newer.

## Run locally
```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
uvicorn app.main:app --reload
```

Open http://127.0.0.1:8000 for the simulator and http://127.0.0.1:8000/docs for API docs.

## USSD flow
1. Empty `text`: language menu.
2. `1`: English, `2`: isiZulu, `3`: isiXhosa, `4`: Sesotho, `5`: Afrikaans, `6`: Kiswahili.
3. After language selection: `1` prices, `2` compare, `3` best reported price, `4` change language, `0` exit.
4. Commodity: `1` tomatoes, `2` maize, `3` potatoes.

Examples:
- `text=""` -> language menu
- `text="1"` -> English main menu
- `text="1*1"` -> commodity menu
- `text="1*1*1"` -> tomato prices

## Africa's Talking integration
Configure the USSD callback URL to `https://YOUR-HOST/ussd` and HTTP method POST. The endpoint accepts form fields:
- `sessionId`
- `serviceCode`
- `phoneNumber`
- `text`

For a real deployment:
- Use HTTPS.
- Configure the provider's USSD product and shortcode.
- Check the provider's current callback and response requirements.
- Use a persistent managed database rather than local SQLite if running multiple instances.
- Add rate limiting, monitoring, privacy controls and operational support.
- Verify translations with native speakers and test GSM character encoding and message-length limits.

## Tests
```bash
python -m pytest -q
```

## Hosted Link
https://cape-code-agriprice.onrender.com/

