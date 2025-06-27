# Web Application Vulnerability Scanner

A comprehensive vulnerability scanner that detects XSS, SQL Injection, CSRF, and security header issues in web applications.

## Features

- 🔍 Web crawling and form discovery
- 🚨 XSS detection (Reflected, Stored, DOM-based)
- 💉 SQL Injection testing (Error-based, Time-based, Blind)
- 🛡️ CSRF vulnerability detection
- 📋 Security headers analysis
- 🌐 Web-based interface
- 📊 Detailed HTML reports
- 🎯 CLI and GUI modes

## Installation

### Prerequisites
- Python 3.7+
- pip package manager

### Quick Setup
```bash
# Clone or download the project
git clone https://github.com/NETHRANAND-20449/ELEVATE-LABS-PROJECT-1
cd vulnerability_scanner

# Install dependencies
pip install -r requirements.txt

# Run setup script
python setup.py

# Test installation
python main.py --help
```

## Usage

### Command Line Interface
```bash
# Basic scan
python main.py http://localhost/dvwa/

# Scan vulnerable test site
python main.py http://testphp.vulnweb.com/
```

### Web Interface
```bash
# Start web server
python web_interface/app.py

# Open browser and navigate to:
http://localhost:5000
```

### Testing with Vulnerable Applications

1. **DVWA Setup:**
   ```bash
   # Download DVWA
   git clone https://github.com/digininja/DVWA.git
   
   # Start with XAMPP/WAMP
   # Access: http://localhost/DVWA/
   ```

2. **WebGoat Setup:**
   ```bash
   # Download WebGoat
   docker run -p 8080:8080 webgoat/goatandwolf
   
   # Access: http://localhost:8080/WebGoat/
   ```

## Project Structure
```
vulnerability_scanner/
├── main.py                 # CLI entry point
├── requirements.txt        # Dependencies
├── setup.py               # Setup script
├── scanner/               # Core scanner modules
│   ├── crawler.py         # Web crawling
│   ├── vulnerability_tests.py  # Vulnerability detection
│   └── report_generator.py    # Report generation
├── web_interface/         # Web GUI
│   ├── app.py            # Flask application
│   ├── templates/        # HTML templates
│   └── static/           # CSS/JS files
├── payloads/             # Test payloads
└── reports/              # Generated reports
```

## Supported Vulnerabilities

### Cross-Site Scripting (XSS)
- Reflected XSS
- Stored XSS
- DOM-based XSS
- Various bypass techniques

### SQL Injection
- Error-based detection
- Time-based blind SQLi
- Boolean-based blind SQLi
- Union-based SQLi

### Cross-Site Request Forgery (CSRF)
- Missing CSRF tokens
- Weak CSRF protection

### Security Headers
- X-Frame-Options
- X-XSS-Protection
- X-Content-Type-Options
- Strict-Transport-Security
- Content-Security-Policy

## Sample Output

```
Starting vulnerability scan of http://localhost/dvwa/
============================================================
Step 1: Crawling website...
Found 5 forms and 12 URLs

Step 2: Testing for vulnerabilities...
XSS found: http://localhost/dvwa/vulnerabilities/xss_r/ with payload: <script>alert('XSS')</script>
SQLi found: http://localhost/dvwa/vulnerabilities/sqli/ with payload: ' OR '1'='1

Step 3: Generating report...

============================================================
SCAN COMPLETE
============================================================
Target: http://localhost/dvwa/
Forms tested: 5
URLs crawled: 12
Vulnerabilities found: 8
  Critical: 2
  High: 3
  Medium: 2
  Low: 1
Report saved to: reports/vulnerability_report_20240620_143022.html
```

## Development and Customization

### Adding New Vulnerability Tests
1. Edit `scanner/vulnerability_tests.py`
2. Add new test method following existing patterns
3. Update `run_all_tests()` method
4. Test with known vulnerable applications

### Customizing Payloads
1. Edit files in `payloads/` directory
2. Add new payload files
3. Update scanner to load custom payloads

### Modifying Reports
1. Edit `scanner/report_generator.py`
2. Customize HTML templates
3. Add new report formats (JSON, XML, etc.)

## Security Considerations

⚠️ **Important:** This tool is for educational and authorized testing only.

- Only test applications you own or have explicit permission to test
- Use isolated testing environments
- Follow responsible disclosure practices
- Comply with local laws and regulations

## Troubleshooting

### Common Issues

1. **Import Errors:**
   ```bash
   # Ensure you're in the project directory
   cd vulnerability_scanner
   
   # Check Python path
   export PYTHONPATH=$PYTHONPATH:$(pwd)
   ```

2. **Permission Denied:**
   ```bash
   # Create reports directory
   mkdir -p reports
   chmod 755 reports
   ```

3. **Connection Errors:**
   - Check target URL is accessible
   - Verify firewall settings
   - Test with local vulnerable apps first

### Performance Tips

- Use `max_depth=1` for faster scans
- Implement rate limiting for large sites
- Run scans during off-peak hours
- Use multiple threads for concurrent testing

## Contributing

1. Fork the repository
2. Create feature branch
3. Add tests for new functionality
4. Submit pull request

## License

This project is for educational purposes only. Use responsibly and ethically.

## Disclaimer

This tool is provided for educational and authorized security testing purposes only. Users are responsible for complying with all applicable laws and regulations. The authors are not responsible for any misuse of this tool.
