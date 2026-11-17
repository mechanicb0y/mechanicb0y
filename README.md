# Awab Al-Shandawi

Final-year cyber security student at Lincoln University College, Malaysia. I build blue-team tools for Linux: log triage, attack detection, threat intelligence and incident response. Everything below runs on your own machine, and each project has a command you can try in a minute or two.

<p>
  <a href="https://www.linkedin.com/in/awab-alshandawi-327637326"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:awabalshandawi@gmail.com"><img src="https://img.shields.io/badge/Email-awabalshandawi%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
</p>

## Security projects

### [ACT: Adaptive Cyber Twin](https://github.com/mechanicb0y/ACT-Adaptive_Cyber_Twin) · final-year project

Watches a Linux machine's security logs, works out what the attacker is doing, and responds.

- Reads `sshd`, `sudo` and `useradd` activity from a log file, `journalctl`, or a remote host over SSH
- Groups single events into behaviours with 7 correlation rules: brute force, distributed brute force, successful brute force, user enumeration, privilege escalation, sensitive file access and persistence
- Scores each attacker from 0 to 100, with a reason for every point, and maps each step to MITRE ATT&CK and the kill chain
- Decides between block, alert and monitor. A local LLM gets a vote but can never trigger a block on its own; blocks are reversible `iptables` rules, and simulation mode is the default
- Writes an HTML/PDF incident report per attacker and sends Telegram alerts for critical attacks
- 370+ pytest tests; the core runs with no internet and no AI model

```bash
git clone https://github.com/mechanicb0y/ACT-Adaptive_Cyber_Twin && cd ACT-Adaptive_Cyber_Twin/backend
pip install -r requirements.txt
python -m app.main --file tests/logs/two_attackers.log     # replay a sample attack
```

`Python` `FastAPI` `PostgreSQL` `Ollama` `Docker`

### [HexBrief](https://github.com/mechanicb0y/hexbrief) · daily threat-intelligence brief · v1.0.0

Turns free threat feeds into a short morning brief that never invents an indicator.

- Pulls MITRE ATT&CK (over TAXII 2.1), CISA KEV, AlienVault OTX, abuse.ch and CIRCL into MISP and OpenCTI
- Ranks the last 24 hours of reporting with written rules, then a local LLM writes up the top 8 stories, citing each by ID
- A validator checks every IP, domain, URL, hash, CVE and ATT&CK ID in the text against the source data; if anything fails, a facts-only brief goes out instead
- Ships Markdown, HTML, PDF, JSON and a STIX 2.1 report; only TLP:CLEAR briefs are published to the [live archive](https://mechanicb0y.github.io/hexbrief/)

```bash
git clone https://github.com/mechanicb0y/hexbrief && cd hexbrief
pip install . && hexbrief demo     # full brief from recorded data: no keys, no Docker
```

`Python` `STIX 2.1` `TAXII 2.1` `MISP` `OpenCTI` `Ollama`

### [awab](https://github.com/mechanicb0y/awab) · Linux log triage in Rust · v0.2.0

Point it at a log and get back a ranked list of what looks like an attack.

- 18 YAML detection rules across SSH, privilege escalation, persistence, defence evasion, web and execution, each tagged with its ATT&CK technique
- Reads auth/syslog, journald, web access logs and auditd
- One static binary built on the Rust standard library only, with zero dependencies
- Terminal table, `--json` or a standalone `--html` report; exits with code 1 on high or critical findings, so it works as a cron or CI tripwire

```bash
curl -fsSL https://raw.githubusercontent.com/mechanicb0y/awab/main/install.sh | sh
awab scan /var/log/auth.log            # on systemd distros: journalctl -o short-iso | awab scan -
```

`Rust`

## Other projects

| Project | What it is | Built with |
|---|---|---|
| [Mimix](https://github.com/mechanicb0y/Mimix) | AI voice studio that runs on your own computer: text to speech, voice mixing, consent-first cloning, dubbing and transcription | Next.js, TypeScript, Python, FastAPI, PostgreSQL |
| [Passport Extraction System](https://github.com/mechanicb0y/Passport-Extraction-System) | Extracts data from passport images | JavaScript |
| [ProPlant](https://github.com/mechanicb0y/ProPlant) | Plant-care application | TypeScript |
| [CoffeeShop App](https://github.com/mechanicb0y/CoffeeShop-App) | Billing system for a coffee shop | C#, Windows Forms |

## Skills

| | |
|---|---|
| **Detection and response** | Linux log analysis, correlation rules, Sigma, MITRE ATT&CK, `iptables` |
| **Threat intelligence** | STIX 2.1, TAXII 2.1, MISP, OpenCTI, TLP 2.0 |
| **Languages** | Python, Rust, TypeScript, JavaScript, C# |
| **Tools** | FastAPI, Next.js, PostgreSQL, Docker, Git, GitHub Actions, Ollama |
| **Platforms** | Linux, Kali Linux |

## Training and awards

- 2nd place, Top Coders Malaysia 2026 (university round)
- Google Cybersecurity Professional Certificate, 2 courses (2026)
- New York University, Introduction to Cyber Security Specialization, 4 courses (2025–2026)
- Cisco Networking Academy, Introduction to Cybersecurity (2024)

## Now

- Finishing ACT for my final-year project
- Building Mimix, a local-first AI voice platform
- Open to internships, collaboration and freelance work

<sub>Based in Malaysia.</sub>
