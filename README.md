# Steam Price Tracker

This project is a **Steam Game Price Tracker** with a **GUI (Tkinter)** and **web interface (Flask)**. It lets you:

* Add Steam games by **AppID**, **store link**, or even a **search link**.
* Automatically fetch current price & discount info from the Steam API.
* Get notified on **WhatsApp** (via Twilio) when tracked games are **10% off or more**.
* Manage games through either:

  * A **desktop GUI** (Tkinter)
  * A **local web interface** (Flask, [http://localhost:5002](http://localhost:5002))

---

## Features

* GUI for adding/removing games to track
* Save/load tracked games from `games.json`
* Auto-check prices every **30 minutes**
* WhatsApp alerts when discounts reach **10%+**
* Works with:

  * Steam AppID directly
  * Store links (`/app/12345/`)
  * Search results (`/search/?term=...`)

---

## Requirements

Install dependencies:

```bash
pip install requests twilio python-dotenv flask
```

macOS users may need to install/updating Tk:

```bash
brew install python-tk
```

---

## Setup

1. Create a `.env` file in the project root:

```ini
# Twilio API credentials
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_auth
TWILIO_FROM_PHONE=whatsapp:+Your_twilio_whatsapp_number   # Twilio Sandbox number
TWILIO_TO_PHONE=whatsapp:+1YOURNUMBER     # Your WhatsApp number
```

Make sure you have joined the **Twilio WhatsApp Sandbox** by sending `join <code>` to their number.

---

## Usage

### GUI mode

Run the script:

```bash
python PriceTracker.py
```

A Tkinter window will open:

* **➕ Add Game** → input AppID, link, or search link
* **🗑 Remove Game** → remove selected game
* **🔄 Reload Games** → reload from `games.json`
* **💰 Check Prices** → check all games now

### Web mode

Flask runs in the background on port **5002**.
Open: [http://localhost:5002](http://localhost:5002)

---

## 💡 Example

1. Add Dota 2 by AppID: `570`
2. Or paste store link:

   ```
   https://store.steampowered.com/app/570/Dota_2/
   ```
3. Or paste a search link:

   ```
   https://store.steampowered.com/search/?term=dota
   ```

---

## Notes

* Steam API sometimes rate-limits → if you get HTTP 429, wait before retrying.
* Free games will show as `Free (0% off)`.
* On macOS, you may see a `Tk deprecation` warning — safe to ignore.
* Im still working on getting the steamAPI to work
---

