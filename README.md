# AI-Powered Compliance Auditor

A Python-based tool that uses AI to scan web app logs, configuration files, and code snippets to identify security vulnerabilities, compliance issues, and bad practices. It automatically generates readable audit reports with severity levels and actionable recommendations.

---

## Project Overview

Modern startups and small businesses often deploy web applications without formal security audits or compliance checks. This tool helps bridge that gap by scanning real-world files (like `.env`, `access.log`, or `docker-compose.yml`) and using AI to flag common risks such as:

- Exposed secrets or credentials
- Suspicious access patterns
- Outdated configurations
- OWASP Top 10 vulnerabilities
- Non-compliance with data privacy standards

The tool returns human-readable reports and raw structured data that can be integrated into workflows or CI pipelines.

---

## Use Case

A startup without a dedicated security team wants to quickly scan their deployment logs and configs before going live. They run this tool and receive an audit report with security recommendations, allowing them to fix potential issues before launch.

---

## Tech Stack

- **Language**: Python 3.11+
- **AI Engine**: OpenAI GPT-4 API (or local LLM with `llama-cpp-python`)
- **Parsing & Analysis**: Regex, custom file analyzers
- **Templating**: Jinja2 for reports
- **(Optional)** Web Dashboard: Flask (HTML/CSS)
- **DevOps**: Docker, GitHub Actions (for CI), future AWS/Fly.io deployment

---

## Features

✅ Upload and analyze:
- Web server logs (Apache/Nginx)
- `.env` and config files
- Source code snippets (e.g., Python, JS)

✅ Generates:
- JSON audit reports
- Readable Markdown or HTML summaries

✅ Uses AI to:
- Detect exposed secrets, bad patterns, suspicious IPs
- Suggest fixes and security best practices
- Classify severity levels (low, medium, high)

✅ Optional:
- Real-time alerting (Slack/email)
- Web dashboard to visualize findings
- Export as CSV/HTML/PDF

---

## Project Structure
compliance-auditor/
├── scanner/ # Core logic
│ ├── parser.py # File reader and formatter
│ ├── analyzer.py # AI interaction + rule-based checks
│ └── prompts/ # Reusable LLM prompt templates
├── reports/ # Generated JSON/HTML reports
├── test_data/ # Example log and config files
├── web/ # Flask dashboard (optional)
├── run_scan.py # CLI interface
├── requirements.txt
└── README.md

## Example Output

```json
{
  "finding": "Sensitive token found in .env file",
  "severity": "high",
  "recommendation": "Store this value securely as an environment variable or use a secret manager."
}
