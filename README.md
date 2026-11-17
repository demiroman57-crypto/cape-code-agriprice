# African Farmer Market USSD

African Farmer Market USSD is a hackathon pilot that helps smallholder farmers check crop prices using ussd.
Farmers do not need a smartphone, internet connection, or app. They simply dial a USSD code, choose their language, and ask for the price of a crop.

## The problem

 Small farmers grow crops for months, but they do not always know what their crops are worth when it is time to sell.

Because they may not have access to up-to-date market prices, they often depend on local buyers or middlemen for pricing information. This can make it difficult for farmers to negotiate a fair price. When farmers are paid less than they should be, they have less money to reinvest in seeds, fertiliser, tools, storage, or transport.

Existing online price platforms do not always work well for rural farmers because:

- Many farmers use basic feature phones and may not have reliable or affordable internet.
- Many platforms are mainly in English instead of local languages.

This can lead to farmers selling too early, accepting low prices, or missing better markets. It can also make it harder for farming families to grow their income and escape poverty.

## Our solution

African Farmer Market USSD gives farmers a simple way to check crop prices from any mobile phone using USSD.

A farmer dials a shortcode, selects their language, and chooses a crop. The service then shows the available price information.

### Why it works for Africa

- **No internet needed:** USSD works on basic phones, so farmers do not need mobile data or an app.
- **Local languages:** The MVP supports English, isiZulu, isiXhosa, Afrikaans, and Kiswahili.
- **Simple to use:** Farmers can check prices, compare prices, and find the highest reported price through a short menu.
- **Built to grow:** The system can later add more crops, more African languages, markets, and countries, AI and auto region detection. 

## Features

- USSD language selection: English, isiZulu, isiXhosa, Afrikaans, and Kiswahili.
- Price lookup for basic crops like tomatoes, maize, and potatoes.
- Price comparison and highest reported price.
- FastAPI endpoint that works with Africa’s Talking USSD callbacks.
- Browser-based USSD simulator.
- SQLite database and pytest tests.
- 
## How to access demo
https://cape-code-agriprice.onrender.com/

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

Open:

- Simulator: http://127.0.0.1:8000
- API documentation: http://127.0.0.1:8000/docs

## How the USSD works

1. When a farmer dials the USSD code, they first choose a language.
2. They can choose:
   - `1` for prices
   - `2` to compare prices
   - `3` for the best reported price
   - `4` to change language
   - `0` to exit
3. They then choose a crop:
   - `1` tomatoes
   - `2` maize
   - `3` potatoes

### Examples

- `text=""` shows the language menu.
- `text="1"` shows the English main menu.
- `text="1*1"` shows the crop menu.
- `text="1*1*1"` shows tomato prices.

## Connecting to Africa’s Talking

Set the USSD callback URL to:

```text
[https://YOUR-HOST/ussd](https://YOUR-HOST/ussd)
```

Use the `POST` method.

The endpoint accepts these form fields:

- `sessionId`
- `serviceCode`
- `phoneNumber`
- `text`


## Hackathon approach

We built African Farmer Market USSD using GitHub Copilot while keeping token use low.

Instead of asking AI to build a large website or complicated system, we used it mainly for the important logic: a small function that matches the crop name a farmer types to the correct crop in the system.

We kept the USSD flow, crop dictionary, backend setup, and demo data simple. This helped us build a working, multilingual agricultural pricing service without using unnecessary AI tokens.

## Tests

```bash
python -m pytest -q
```

##Contributors
Nothile Masango
Shamain Bhengesa
David Maila
Paseka Moloi
Demi Roman
