<div align="center">

# 🕵️ theHarvester OSINT Reconnaissance Lab

### Public Information Gathering & Domain Footprinting with Kali Linux

![theHarvester](https://img.shields.io/badge/theHarvester-OSINT%20Tool-blue?style=for-the-badge&logo=github&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali%20Linux-Security%20Testing-black?style=for-the-badge&logo=kalilinux&logoColor=white)
![OSINT](https://img.shields.io/badge/OSINT-Reconnaissance-purple?style=for-the-badge)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Learning-red?style=for-the-badge)
![PsychoMods](https://img.shields.io/badge/PsychoMods-Tech%20Lab-8AFF00?style=for-the-badge&logo=github&logoColor=black)

**A practical learning record for discovering publicly indexed domain information and interpreting reconnaissance results.**

[GitHub Profile](https://github.com/Psychomods666) · [Upstream theHarvester Project](https://github.com/laramies/theHarvester)

</div>

---

## 🧭 Overview

This project documents a learning exercise using **theHarvester**, an open-source OSINT tool that helps collect publicly available information related to a domain. Depending on the configured data sources and available access, results can include hostnames, email addresses, IP addresses, and people-related references.

The screenshots show the tool being cloned and launched from a Linux terminal, with the search sources `hackertarget`, `crtsh`, and `certspotter`. Public screenshots in this repository have been redacted to avoid unnecessarily publishing target details.

This is documentation of a reconnaissance exercise—not proof that a target is vulnerable or compromised.

```text
Prepare Linux Environment
          ↓
Obtain theHarvester
          ↓
Review Help & Options
          ↓
Choose Approved Data Sources
          ↓
Run a Scoped OSINT Search
          ↓
Review and Validate Results
          ↓
Document Findings Responsibly
```

> ⚠️ **Ethical use:** Gather information only within an authorized assessment, approved research scope, or a lawful educational lab. Publicly available information can still be sensitive.

---

## 🎯 Objectives

- Understand the purpose of theHarvester in OSINT.
- Learn how to obtain the project from its upstream repository.
- Understand the target-domain and data-source options.
- Run a scoped search for a domain you own or are authorized to assess.
- Interpret discovered hostnames and other output categories.
- Understand the limits of third-party data sources.
- Redact identifying details before publishing evidence.
- Document reconnaissance results clearly on GitHub.

---

## 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| 🐉 Kali Linux / Linux terminal | Command-line environment |
| 🕵️ theHarvester | Public-information gathering |
| 🌐 Certificate Transparency | Public certificate-related data sources |
| 🔎 Search providers | Publicly indexed information, where supported |
| 📝 GitHub Markdown | Lab documentation |

---

# 🧪 Practical Walkthrough

## 01 — Obtain the Project

The first screenshot shows the upstream repository being cloned.

### Command

```bash
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
```

### Explanation

- `git clone` downloads a copy of the repository.
- `cd theHarvester` enters the downloaded project directory.

If the directory already exists, do not clone another copy over it. Enter the existing folder and consult the current upstream installation guide.

### 📸 Terminal Evidence

![theHarvester setup and command](images/01-installation-and-command.jpg)

---

## 02 — Review Installation Requirements

Installation instructions can change between releases. Use the project's current documentation rather than relying on old commands or a previously created environment.

### Recommended starting points

- [theHarvester repository and installation notes](https://github.com/laramies/theHarvester)
- [Project documentation](https://github.com/laramies/theHarvester/tree/master/docs)

Follow the instructions for your installed release and operating system. Avoid running unknown scripts as root unless the official documentation requires it and you understand why.

---

## 03 — Understand the Command Structure

The recorded terminal command follows this general format:

```bash
theHarvester -d example.com -b hackertarget,crtsh,certspotter
```

Use `example.com` only as a placeholder. Replace it only with a domain that you own or are explicitly authorized to assess.

### What the options mean

| Option | Purpose |
|---|---|
| `-d` | Specify the domain to research |
| `-b` | Select the supported data source or sources |
| `-h` | Display help and available options |

Check the installed version's help output because available options and provider names can change:

```bash
theHarvester -h
```

### Sources shown in the screenshot

- **Hackertarget** — a source that may provide publicly available host and DNS-related information.
- **crt.sh / Certificate Transparency** — searches public certificate records that may reveal domain names included in certificates.
- **CertSpotter** — a certificate-transparency-related source that may expose certificate and hostname information.

Provider availability, quotas, API requirements, and output vary. A provider returning no results does not mean that no public information exists.

---

## 04 — Run a Scoped Reconnaissance Search

For an authorized domain, use the command syntax supported by your installed version:

```bash
theHarvester -d example.com -b hackertarget,crtsh,certspotter
```

### What the tool may report

Depending on the source and current tool behavior, results may include:

- Hostnames associated with the domain.
- Email addresses discovered in public sources.
- People-related references, where supported.
- IP addresses associated with discovered hosts.
- Status messages showing which sources were queried.

**Important:** Do not assume every returned hostname is active, controlled by the same organization, or in scope for testing. Validate ownership and authorization before any further assessment.

---

## 05 — Review the Output

The second screenshot shows theHarvester banner, selected source names, source status messages, and a host count. The hostnames and IP addresses have been redacted in the public image.

### 📸 Terminal Evidence

![Redacted theHarvester scan summary](images/02-scan-summary-redacted.jpg)

### Interpreting the displayed results

The screenshot indicates that the tool queried the selected sources and displayed a host count. It also shows no results for some categories in that particular run.

Those messages describe only that run. Results depend on the domain, source coverage, provider access, rate limits, configuration, and time of collection.

---

# 📊 Understanding the Output

| Output category | What it can mean | What to verify |
|---|---|---|
| Hosts / hostnames | Names associated with the domain in queried sources | Ownership, DNS status, and assessment scope |
| IP addresses | Addresses associated with returned hosts | Current DNS records and attribution |
| Emails | Publicly indexed email addresses, if returned | Relevance and privacy; avoid unnecessary disclosure |
| People | Public references, where supported | Accuracy and whether collection is necessary |
| Source status | Whether a provider was queried or returned data | Provider limitations, errors, and API requirements |

> **A discovered hostname is not a vulnerability.** Reconnaissance results need context and verification before being included in a security report.

---

# 🔬 OSINT Workflow

```text
       Approved Domain
              │
              ▼
      theHarvester Tool
              │
              ▼
     Selected Public Sources
              │
              ▼
     Hostnames / Other Results
              │
              ▼
      Validate and De-duplicate
              │
              ▼
      Confirm Scope & Relevance
              │
              ▼
      Sanitize Notes and Report
```

OSINT helps establish an initial picture of publicly visible information. It should not be treated as a complete inventory or as permission to probe every discovered system.

---

# 🧠 Key Learning

Through this practical, I learned how to:

- Obtain an open-source OSINT tool from its upstream repository.
- Recognize the basic domain and source options.
- Understand the role of certificate-transparency data in hostname discovery.
- Read source status messages and host counts.
- Interpret empty results without drawing unsupported conclusions.
- Redact hostnames and IP addresses before public documentation.
- Keep reconnaissance separate from vulnerability confirmation.
- Document findings with a clear scope and responsible-use statement.

---

# 🛡️ Scope & Authorization

| Activity | Environment | Authorization |
|---|---|---|
| Tool setup | Local Linux environment | Own system |
| Public-source lookup | Domain you own or have approval to research | Follow applicable rules and scope |
| Reviewing hostnames | Local notes / report | Validate ownership and relevance |
| Active testing of discovered hosts | Separate assessment activity | Explicit permission required |
| Publishing results | GitHub repository | Remove sensitive and identifying data |

> 🔐 **Only investigate domains within your approved scope.** Public availability does not automatically grant permission to test, access, or exploit a discovered host.

Do not publish credentials, API keys, private contact details, personal data, or unredacted host inventories without a valid reason and authorization.

---

# 📁 Project Structure

```text
theharvester-osint-lab/
│
├── README.md
│
└── images/
    ├── 01-installation-and-command.jpg
    └── 02-scan-summary-redacted.jpg
```

Keep the `images/` folder and filenames unchanged so GitHub can render the screenshot links.

---

# 📸 Screenshots Gallery

<details>
<summary><strong>📷 Screenshot 1 — Repository Setup and Command</strong></summary>

![theHarvester setup screenshot](images/01-installation-and-command.jpg)

*Shows the repository being cloned, the project directory being opened, and the command being prepared.*

</details>

<details>
<summary><strong>📷 Screenshot 2 — Source Search and Results</strong></summary>

![theHarvester redacted result screenshot](images/02-scan-summary-redacted.jpg)

*Shows the tool banner, selected sources, status messages, and a result count. Target-specific hostnames and IP addresses are redacted.*

</details>

---

# 🚀 Future Improvements

- [ ] Record the installed theHarvester version.
- [ ] Add sanitized sample output from a dedicated lab domain.
- [ ] Compare results from different supported public sources.
- [ ] Document how certificate-transparency records are created.
- [ ] Add a repeatable note template for source, date, and scope.
- [ ] Verify discovered hostnames against approved asset inventories.
- [ ] Create a structured OSINT summary without exposing unnecessary personal data.

---

# 👨‍💻 Author

<div align="center">

## PsychoMods

**Cybersecurity · Ethical Hacking · OSINT · Technology**

Learning by building, testing, and documenting.

[![GitHub](https://img.shields.io/badge/GitHub-Psychomods666-181717?style=for-the-badge&logo=github)](https://github.com/Psychomods666)

**Cybersecurity Learning Project**

</div>

---

<div align="center">

### 🔐 Learn • Research • Verify • Document

<sub>Created for cybersecurity education and authorized OSINT research.</sub>

<sub>theHarvester is an upstream open-source project. This repository contains personal lab notes and is not an official theHarvester project.</sub>

</div>
