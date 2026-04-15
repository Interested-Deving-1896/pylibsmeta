# pylibsmeta

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue?logo=python" />
  <img src="https://img.shields.io/badge/PyPI-Integrated-blue?logo=pypi" />
  <img src="https://img.shields.io/badge/GitHub%20Actions-Automated-success?logo=githubactions" />
  <img src="https://img.shields.io/badge/License-MIT-green" />
  <img src="https://img.shields.io/badge/Scale-15k%2B%20Libraries-orange" />
</p>

<p align="center">
  <b>Large-Scale Static Python Library Metadata Infrastructure</b><br>
  Automated PyPI package introspection using AST parsing.<br>
  Designed for AI autocomplete engines, IDE tooling, and static analysis systems.
</p>

---

## 🚀 Overview

`pylibsmeta` is a fully automated Python ecosystem metadata generator.

Instead of installing and executing packages, this project:

- Fetches latest package versions from PyPI
- Downloads source distributions
- Parses Python files using AST
- Extracts structured symbol metadata
- Stores version-encoded JSON outputs
- Runs entirely via GitHub Actions

The result is a scalable, version-aware static metadata database for thousands of Python libraries.

---

## 🧠 Why This Exists

Modern developer tooling requires:

- Structured symbol data
- Safe introspection (no execution)
- Version-aware API tracking
- Scalable automation

Installing packages dynamically for introspection is slow and unsafe.

`pylibsmeta` solves this using pure static AST parsing at scale.

---

## 🔍 What Gets Extracted

For each PyPI package:

- Functions
- Classes
- Methods
- Global variables

Example output:

```json
{
  "getLogger": ["name"],
  "Logger": {
    "debug": ["msg", "*args", "**kwargs"],
    "info": ["msg", "*args", "**kwargs"]
  }
}
```

Each file is version encoded:

```
1.2.3 → v000100020003
```

Example:

```
requests_v000200310000.json
```

---

## 📦 Output Structure

```
lib_db/
 ├── requests_v000200310000.json
 ├── numpy_v000100260000.json
 ├── fastapi_v000000980000.json
```

---

## ⚙️ Core Features

- ✅ Version encoding
- ✅ Skip already processed versions
- ✅ Resume system via `progress.json`
- ✅ 5-hour safe exit (GitHub Actions limit aware)
- ✅ Fully automated update pipeline
- ✅ Handles 15,000+ libraries
- ✅ No package installation
- ✅ No code execution
- ✅ All public variables, functions, methods and classes parsing

---

## 🔄 Resume System

Designed for GitHub's 6-hour workflow limit.

Each run:

1. Processes a batch of packages
2. Saves progress
3. Exits safely before timeout
4. Resumes next scheduled run

This enables large-scale processing across thousands of libraries.

---

## 🤖 Automation

GitHub Actions workflow supports:

- Manual trigger (`workflow_dispatch`)
- Scheduled runs (cron)
- Incremental version updates
- Automated rebuilds

Example hourly schedule:

```yaml
schedule:
  - cron: "0 * * * *"
```

---

## 🛠 Local Setup

### 1️⃣ Add package list

Create `l.txt`:

```
requests
numpy
fastapi
django
```

### 2️⃣ Install dependencies

```
pip install -r requirements.txt
```

### 3️⃣ Run generator

```
python gen_libs.py
```

---

## 📊 Scale

Designed to support:

- ~100 packages per run
- ~15,000+ total packages
- Fully resumable processing
- Long-term incremental updates

This is infrastructure-level metadata generation — not a one-off script.

---

## 💡 Use Cases

- Offline AI autocomplete engines
- Static LLM grounding datasets
- IDE backend services
- Library API indexing
- Cross-version API comparison
- Large-scale symbol search systems
- Developer tooling backends

---

## 🔒 Safety

- No `exec`
- No `eval`
- No runtime execution
- No dependency installation
- Pure source parsing via AST

Safe for automation environments.

---

## 🧬 Roadmap

### v1 (Current)
- Function/class extraction
- Version encoding
- Automated scaling

### v2 (Planned)
- Type inference (basic)
- Return value analysis
- Symbol linking
- Structured symbol graph
- Docstring extraction
- Cross-version API comparison
- Compressed dataset builds
- API layer for partial access

---

## 📜 License

MIT License

---

## 🔥 Status

Production-ready  
Automated  
Scales to thousands of libraries  
Continuously improving  

---

<p align="center">
  Built for scalable developer tooling infrastructure.
</p>
<p align="center">
Donate: UQDZc4_R6v2PzTDCEfHAfgBeeP1VcoQaNH49YI2ayqWfyz4m (Toncoin)
</p>
