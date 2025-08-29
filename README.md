# Telegram Crypto Price Bot

A witty, conversational Telegram bot that fetches current and historical cryptocurrency prices. This project is built using n8n for automation and powered by the Dobby model from SentientAGI for natural language processing.

**Bot Link:** [https://t.me/Sentient_crypto_price_bot](https://t.me/Sentient_crypto_price_bot)

---

## Features

-   **Natural Language Queries:** Ask for prices in plain English (e.g., "btc price yesterday").
-   **Historical Data:** Fetches prices for any specific date within the last year.
-   **Humorous Personality:** Uses a second AI call to craft witty and engaging responses.
-   **Rate Limiting:** Manages user access with a limit of 3 messages per day, tracked in Google Sheets.
-   **Open-Source Workflow:** The complete, sanitized n8n workflow is available in this repository.

## How It Works

1.  **User Message:** A user sends a message to the Telegram bot.
2.  **Rate Limit Check:** The workflow checks a Google Sheet to see if the user has exceeded their daily message limit.
3.  **AI Extraction (Brain 1):** The user's message is sent to the Dobby AI model to extract the cryptocurrency name and the target date.
4.  **Data Fetching:** The workflow uses the CoinGecko API to find the correct coin ID and fetch the price for the specified date.
5.  **AI Response Formatting (Brain 2):** The structured data (coin name, price, date) is sent back to the Dobby AI with instructions to create a humorous, conversational sentence.
6.  **Telegram Reply:** The final, witty response is sent back to the user on Telegram.

## Setup Instructions

To run this workflow yourself:

1.  **Download:** Download the `crypto-price-bot-workflow.json` file from this repository.
2.  **Import:** Import the JSON file into your n8n instance.
3.  **Credentials:** Connect your own credentials for:
    *   Telegram
    *   Google Sheets
    *   Fireworks AI (using HTTP Header Auth)
4.  **Google Sheet:** Create a new Google Sheet with three columns: `UserID`, `MessageCount`, and `Date`. Update the Google Sheets nodes in the workflow to point to your new sheet.
5.  **API Key:** Open the **Code1** node and paste your own CoinGecko API key into the `COINGECKO_API_KEY` constant.
6.  **Activate:** Activate the workflow.

## Tech Stack

-   **Automation:** [n8n.io](https://n8n.io/)
-   **AI Model:** SentientAGI's `dobby-mini-unhinged-plus-llama-3-1-8b` via Fireworks AI
-   **Data Source:** [CoinGecko API](https://www.coingecko.com/en/api)
-   **Database:** Google Sheets
