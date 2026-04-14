# n8n Weather Workflow

Automated workflow built with n8n that sends a daily weather summary email every morning at 7:30 AM.

## How it works

```
Schedule Trigger (7:30 AM) → HTTP Request (OpenWeatherMap API) → Send Email
```

1. **Schedule Trigger** — fires every day at 7:30 AM via cron (`0 30 7 * * *`)
2. **HTTP Request** — fetches current weather data from the OpenWeatherMap API
3. **Send Email** — delivers a plain-text summary via SMTP

## Email preview

```
Good morning!

Weather in Guarapuava:
- nublado
- Temp: 22.03°C
- Humidity: 65%
```

## Requirements

* [n8n](https://n8n.io) (Cloud or self-hosted)
* [OpenWeatherMap API key](https://openweathermap.org/api) (free tier)
* SMTP credentials configured in n8n (Gmail or any SMTP provider)

## Setup

### Option 1 — n8n Cloud (easiest)

1. Create an account at https://n8n.io
2. Open the n8n editor
3. Go to **Workflows → Import from file**
4. Upload `workflow.json`
5. Configure your API key and email credentials
6. Activate the workflow

---

### Option 2 — Run n8n locally with Docker

```bash
docker run -it --rm \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  n8nio/n8n
```

Access `http://localhost:5678` to open the n8n editor.

---

### Get your OpenWeatherMap API key

1. Create a free account at https://openweathermap.org
2. Go to **API keys** in your dashboard
3. Copy your key

---

### Import the workflow

1. Download [`workflow.json`](./workflow.json) from this repository
2. In n8n, go to **Workflows → Import from file**
3. Select the downloaded file

---

### Configure credentials

* **HTTP Request node**: replace `YOUR_API_KEY` in the URL with your actual OpenWeatherMap key
* **Send Email node**: connect your SMTP credentials in n8n settings

---

### Activate the workflow

Toggle the workflow to **Active** — it will run automatically every day at 7:30 AM.

## Workflow file

The exported workflow is available in [`workflow.json`](./workflow.json).
Import it directly into any n8n instance to get started.

> The API key has been removed from the exported file. Add your own key before activating.

## Tech stack

* [n8n](https://n8n.io) — workflow automation
* [OpenWeatherMap API](https://openweathermap.org/api) — weather data
* Docker — local environment

## License

MIT
