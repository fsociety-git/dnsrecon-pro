# DNSRecon Pro 🔍

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-orange)](https://github.com/yourusername/dnsrecon-pro/releases)
[![Maintained](https://img.shields.io/badge/maintained-yes-brightgreen.svg)](https://github.com/yourusername/dnsrecon-pro/commits/main)

> Advanced DNS Enumeration & Subdomain Discovery Tool for Security Professionals

DNSRecon Pro is a powerful and fast DNS reconnaissance tool designed for penetration testers, bug bounty hunters, and security researchers. It combines multiple DNS enumeration techniques with modern Python async capabilities to deliver comprehensive results quickly.

## ⚡ Key Features

### 🎯 DNS Enumeration
- **Complete DNS record enumeration** (A, AAAA, MX, NS, CNAME, SOA, TXT, PTR)
- **Zone transfer attempts** against all nameservers
- **Reverse DNS lookups** for discovered IPs
- **Wildcard detection** to filter false positives
- **Custom DNS server support** for bypassing filters

### 🔍 Subdomain Discovery
- **Multi-threaded brute force** with customizable thread count
- **Smart wildcard filtering** to reduce false positives
- **Multiple wordlist support** with included lists
- **Progress tracking** with real-time updates
- **CNAME chain following** for complete enumeration

### 📊 Output & Reporting
- **Multiple export formats**: JSON, CSV, HTML
- **Beautiful HTML reports** with statistics and visualizations
- **Real-time colored console output** for better readability
- **Detailed scan statistics** including timing and discovered assets
- **Clean tabular display** of results

### 🚀 Performance
- **Asynchronous DNS queries** for maximum speed
- **Configurable thread pools** (default: 20 threads)
- **Smart rate limiting** to avoid detection
- **Efficient memory usage** for large wordlists
- **Automatic retry logic** for failed queries

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Git

### Quick Install

```bash
# Clone the repository
git clone https://github.com/yourusername/dnsrecon-pro.git
cd dnsrecon-pro

# Install dependencies
pip install -r requirements.txt

# Make executable (Linux/Mac)
chmod +x dnsrecon.py

# Run the tool
python dnsrecon.py -h
```

### Install with Virtual Environment (Recommended)

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Linux/Mac:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## 🎮 Usage

### Basic Scan
```bash
python dnsrecon.py -d example.com
```

### Full Enumeration
```bash
python dnsrecon.py -d example.com --full-scan
```

### Custom Wordlist & Threads
```bash
python dnsrecon.py -d example.com -w wordlists/subdomains-large.txt -t 50
```

### Export Results
```bash
# JSON format
python dnsrecon.py -d example.com -o results.json

# HTML report
python dnsrecon.py -d example.com -o report.html --format html

# CSV format
python dnsrecon.py -d example.com -o results.csv --format csv
```

### Advanced Options
```bash
# Use custom DNS server
python dnsrecon.py -d example.com --dns-server 8.8.8.8

# Verbose mode with custom timeout
python dnsrecon.py -d example.com -v --timeout 5

# Multiple options combined
python dnsrecon.py -d example.com \
    --full-scan \
    --threads 100 \
    --dns-server 1.1.1.1 \
    --timeout 3 \
    -o results.json \
    -v
```

## 📖 Command Reference

| Option | Short | Description | Default |
|--------|-------|-------------|---------|
| `--domain` | `-d` | Target domain to enumerate | *Required* |
| `--wordlist` | `-w` | Path to subdomain wordlist | `wordlists/subdomains-medium.txt` |
| `--threads` | `-t` | Number of concurrent threads | `20` |
| `--timeout` | | DNS query timeout (seconds) | `2.0` |
| `--dns-server` | | Custom DNS server IP | System default |
| `--output` | `-o` | Output file path | None |
| `--format` | | Output format (json/csv/html) | `json` |
| `--full-scan` | | Perform all enumeration techniques | `False` |
| `--verbose` | `-v` | Enable verbose output | `False` |
| `--no-color` | | Disable colored output | `False` |

## 📁 Project Structure

```
dnsrecon-pro/
├── dnsrecon.py              # Main executable script
├── requirements.txt         # Python dependencies
├── README.md               # Project documentation
├── LICENSE                 # MIT license file
├── setup_and_usage.md      # Setup instructions
│
├── core/                   # Core modules
│   ├── __init__.py        # Module initialization
│   ├── dns_enum.py        # DNS enumeration engine
│   ├── subdomain.py       # Subdomain discovery engine
│   └── utils.py           # Utility functions
│
├── wordlists/             # Subdomain wordlists
│   ├── subdomains-small.txt    # ~100 common subdomains
│   ├── subdomains-medium.txt   # ~1000 subdomains (default)
│   └── subdomains-large.txt    # ~10000 subdomains
│
├── output/                # Output directory
│   └── .gitkeep          # Placeholder
│
└── tests/                 # Unit tests
    ├── __init__.py
    └── test_dns_enum.py
```

## 🎨 Sample Output

### Console Output
```
[*] Target domain: example.com
[*] Threads: 50
[*] DNS Server: 8.8.8.8

[*] Starting DNS enumeration...
[+] A: 4 records found
[+] MX: 3 records found
[+] NS: 4 records found
[+] TXT: 2 records found

[*] Starting subdomain discovery...
[+] Found: api.example.com -> 192.168.1.10
[+] Found: mail.example.com -> 192.168.1.20
[+] Found: vpn.example.com -> 192.168.1.30

[+] Scan Statistics:
  Total subdomains found: 15
  Unique IP addresses: 12
  Scan duration: 45.2 seconds

[+] Results saved to: results.json
```

### HTML Report
The HTML report includes:
- Professional styling with responsive design
- Scan statistics dashboard
- Sortable tables for all findings
- Visual indicators for different record types
- Export functionality for further analysis

## 🔧 Configuration

### Custom Wordlists
Place your wordlists in the `wordlists/` directory:
```bash
# Download SecLists
wget https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/DNS/subdomains-top1million-5000.txt \
    -O wordlists/subdomains-large.txt
```

### DNS Servers
Recommended DNS servers for better results:
- Google: `8.8.8.8`, `8.8.4.4`
- Cloudflare: `1.1.1.1`, `1.0.0.1`
- Quad9: `9.9.9.9`, `149.112.112.112`

## 🛡️ Legal & Ethical Use

> **⚠️ IMPORTANT**: This tool is designed for **authorized security testing only**.

### Before using DNSRecon Pro:
- ✅ Ensure you have **written permission** to test the target domain
- ✅ Respect rate limits and avoid overwhelming DNS servers
- ✅ Follow responsible disclosure if you find vulnerabilities
- ✅ Comply with all applicable laws and regulations

### Prohibited Uses:
- ❌ Unauthorized reconnaissance of third-party domains
- ❌ Disrupting DNS services through excessive queries
- ❌ Using discovered information for malicious purposes

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### How to Contribute:
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Areas for Contribution:
- New enumeration techniques
- Performance improvements
- Additional export formats
- Bug fixes and error handling
- Documentation improvements

## 🐛 Bug Reports & Feature Requests

Found a bug or have a feature idea? Please open an issue:
- [Report Bug](https://github.com/yourusername/dnsrecon-pro/issues/new?labels=bug)
- [Request Feature](https://github.com/yourusername/dnsrecon-pro/issues/new?labels=enhancement)

## 📚 Resources & References

### DNS Enumeration Techniques
- [OWASP Testing Guide - DNS Enumeration](https://owasp.org/www-project-web-security-testing-guide/)
- [DNS RFC Standards](https://www.ietf.org/standards/rfcs/)

### Wordlist Sources
- [SecLists by Daniel Miessler](https://github.com/danielmiessler/SecLists)
- [Assetnote Wordlists](https://wordlists.assetnote.io/)
- [CommonSpeak2](https://github.com/assetnote/commonspeak2)

### Similar Tools
- [DNSRecon](https://github.com/darkoperator/dnsrecon)
- [Sublist3r](https://github.com/aboul3la/Sublist3r)
- [Amass](https://github.com/OWASP/Amass)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Security Researcher**

- GitHub: [@yourusername](https://github.com/yourusername)
- Twitter: [@yourusername](https://twitter.com/yourusername)

## 🌟 Acknowledgments

- DNS enumeration techniques inspired by industry-standard tools
- Wordlists compiled from various public sources
- Thanks to all contributors and the security community

---

<p align="center">
  Made with ❤️ by the Security Community
</p>

<p align="center">
  <a href="#dnsrecon-pro-">Back to top</a>
</p>
