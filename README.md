# ⚙️ n8n Automation Projects

Welcome to my **n8n Automation Projects** repository! 🚀

This repository contains practical workflow automation projects built using **n8n**, APIs, data processing, email integrations, and other automation tools. Each project includes documentation and an exported workflow JSON file to make it easier to understand, import, and reuse.

## 🎯 Repository Goals

- Learn and practise workflow automation using n8n.
- Integrate APIs and external services.
- Automate repetitive tasks and notifications.
- Build practical projects for my technical portfolio.
- Document each project for easy understanding and reuse.

## 📂 Repository Structure

```text
n8n-automation-projects/
├── README.md
└── 01-daily-weather-digest/
    └── daily-weather-digest.json
```

---

## 🌦️ 01. Daily Weather Digest

An **n8n** workflow that fetches the day's weather forecast every morning at 7:00 AM and emails a short summary.

### 🎯 What it does

1. **Schedule Trigger** starts the workflow every day at 7:00 AM.
2. **HTTP Request** calls the free [Open-Meteo](https://open-meteo.com/) API (no API key needed) for the day's maximum temperature, minimum temperature and rain probability.
3. **Edit Fields** picks out those three values and names them `max`, `min` and `rain`.
4. **Gmail (Send a message)** builds an HTML email with expressions such as `{{ $json.max }}` and sends it.

```text
Schedule Trigger -> HTTP Request -> Edit Fields -> Gmail
```

### 🧠 Key Concepts

- Schedule-based automation
- API integration
- JSON data extraction
- Dynamic expressions
- Automated email notifications
- Credentials (Gmail OAuth2), so no login details are stored in the workflow

### 🧰 Tools and Technologies

- **n8n**: workflow automation platform
- **Open-Meteo API**: free weather data
- **Gmail with OAuth2**: email delivery
- **JSON**: structured data exchange

### 📥 How to Use

1. In n8n, go to **Workflows -> Import from file** and select `01-daily-weather-digest/daily-weather-digest.json`.
2. Open the **Send a message** node, then create or select your own **Gmail OAuth2 credential**.
3. In the same node, replace `your-email@example.com` with your email address.
4. Open the **HTTP Request** node and change `latitude` and `longitude` in the URL to your city. The default is Kochi, India (`9.95`, `76.27`).
5. Open the **Schedule Trigger** node and set the time you want. Check your n8n timezone under Settings.
6. Click **Execute workflow** to test it, then **Publish** to run it automatically every day.

### 💡 Ideas for Extending It

- Add an **IF** node so the email only mentions an umbrella when the rain chance is above 50%.
- Send the digest to Telegram or Slack instead of email.
- Show the forecast for the next 3 days.

### 🔐 Security Notes

- The exported JSON contains no passwords or API keys. n8n does not export credentials, so you need to connect your own.
- Replace placeholder values with your own configuration before running.
- Open-Meteo is free for non-commercial use. Check their terms if you plan to use it commercially.

---

## 🔗 Useful Resources

- [n8n](https://n8n.io/)
- [n8n Documentation](https://docs.n8n.io/)
- [Open-Meteo API](https://open-meteo.com/)

---

**Built with curiosity, consistency, and a passion for automation.** 💻✨
