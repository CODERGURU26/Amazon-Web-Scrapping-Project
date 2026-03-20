# 🛒 Amazon Web Scraping Price Tracker

An automated web scraping tool that monitors Amazon product prices and sends email notifications when prices drop below a specified threshold. Built with Python, BeautifulSoup, and automated email alerts.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-43B02A?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Amazon](https://img.shields.io/badge/Amazon-FF9900?style=for-the-badge&logo=amazon&logoColor=white)

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Data Collected](#data-collected)
- [Email Notifications](#email-notifications)
- [Scheduling](#scheduling)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Legal & Ethical Considerations](#legal--ethical-considerations)
- [Troubleshooting](#troubleshooting)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [Author](#author)

---

## 🎯 Project Overview

This automated price tracker scrapes Amazon product listings to monitor price changes over time. When a product's price drops below your desired threshold, you receive an instant email notification, helping you save money on purchases.

**Perfect for:**
- 🛍️ Finding the best deals on Amazon
- 💰 Saving money through price monitoring
- 📊 Tracking price trends over time
- ⏰ Automated deal alerts
- 🎯 Never missing a sale again

---

## ✨ Features

### Web Scraping
- ✅ **Real-time Price Extraction**: Scrapes current Amazon product prices
- ✅ **Product Details**: Captures title, price, color, size, material, country of origin
- ✅ **User-Agent Handling**: Properly identifies requests to avoid blocking
- ✅ **Data Cleaning**: Automatically strips whitespace and formats data
- ✅ **Error Handling**: Robust scraping with fallback mechanisms

### Data Management
- ✅ **CSV Storage**: Saves all price history to CSV file
- ✅ **Timestamp Tracking**: Records date of each price check
- ✅ **Pandas Integration**: Easy data analysis and visualization
- ✅ **Append Mode**: Continuously adds new data without overwriting

### Automation
- ✅ **Scheduled Monitoring**: Runs checks every 24 hours automatically
- ✅ **Email Alerts**: Sends notifications when price drops
- ✅ **Price Threshold**: Customizable price trigger
- ✅ **Continuous Operation**: Runs indefinitely until stopped

### Email Notifications
- ✅ **SMTP Integration**: Uses Gmail for email delivery
- ✅ **Custom Messages**: Personalized email content
- ✅ **Instant Alerts**: Immediate notification on price drop
- ✅ **Secure Authentication**: Gmail App Password support

---

## 🔧 How It Works

### Workflow

```
1. Send HTTP Request to Amazon Product Page
           ↓
2. Parse HTML with BeautifulSoup
           ↓
3. Extract Product Details (Price, Title, etc.)
           ↓
4. Clean and Format Data
           ↓
5. Save to CSV File with Timestamp
           ↓
6. Check if Price Below Threshold
           ↓
7. If YES → Send Email Alert
           ↓
8. Wait 24 Hours
           ↓
9. Repeat from Step 1
```

### Data Flow

```
Amazon Product Page
    → BeautifulSoup Parser
        → Extract Data
            → Clean Data
                → CSV Storage
                    → Price Check
                        → Email Alert (if threshold met)
```

---

## 🚀 Installation

### Prerequisites
- Python 3.7 or higher
- Gmail account (for email notifications)
- Internet connection

### Step 1: Clone the Repository

```bash
git clone https://github.com/CODERGURU26/Amazon-Price-Tracker.git
cd Amazon-Price-Tracker
```

### Step 2: Install Dependencies

```bash
# Install required libraries
pip install beautifulsoup4
pip install requests
pip install pandas
pip install lxml

# Or install all at once
pip install beautifulsoup4 requests pandas lxml
```

### Step 3: Gmail Setup for Email Notifications

1. **Enable 2-Step Verification** on your Gmail account
2. **Generate App Password**:
   - Go to Google Account → Security
   - Select "2-Step Verification"
   - Scroll to "App passwords"
   - Generate password for "Mail"
   - Copy the 16-character password

3. **Update Email Credentials** in the notebook:
   ```python
   server.login('your_email@gmail.com', 'your_app_password')
   ```

---

## 💻 Usage

### Quick Start

1. **Open Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

2. **Open the Project**
   ```
   Amazon_Web_Scrapping_Project.ipynb
   ```

3. **Update Product URL**
   - Find product on Amazon
   - Copy product URL
   - Replace URL in notebook

4. **Set Price Threshold**
   ```python
   if(price <= 400):  # Change to your desired price
       send_mail()
   ```

5. **Run All Cells**
   - Execute cells sequentially
   - Monitor output for price data

### Manual Price Check

```python
# Run once to check current price
check_price()
```

### Automated Monitoring

```python
# Uncomment to run continuously
while(True):
    check_price()
    time.sleep(86400)  # 24 hours = 86400 seconds
```

---

## ⚙️ Configuration

### Product URL Configuration

```python
url = 'https://www.amazon.in/product-url-here'
```

**How to get product URL:**
1. Search for product on Amazon
2. Click on product
3. Copy URL from browser address bar
4. Paste in notebook

### User-Agent Configuration

```python
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
}
```

**Why User-Agent?**
- Identifies scraper as browser
- Prevents blocking by Amazon
- Follows web scraping best practices

### Price Threshold

```python
if(price <= 400):  # Set your desired price threshold
    send_mail()
```

### Check Interval

```python
time.sleep(86400)  # 86400 seconds = 24 hours

# Other options:
# 1 hour: time.sleep(3600)
# 12 hours: time.sleep(43200)
# 1 week: time.sleep(604800)
```

---

## 📊 Data Collected

### CSV File Structure

| Column | Description | Example |
|--------|-------------|---------|
| **Title** | Product name | "DUDEME Fuda: While Alive Eat Sleep Code..." |
| **Price** | Current price (₹) | 499 |
| **Color** | Product color | Black |
| **Size** | Product size | L |
| **Material** | Product material | 100% Cotton |
| **Country** | Country of origin | India |
| **Date** | Date of price check | 2026-03-19 |

### Sample Data

```csv
Title,Price,Color,Size,Material,Country,Date
"DUDEME Fuda: While Alive...",499,Black,L,100% Cotton,India,2026-03-19
"DUDEME Fuda: While Alive...",450,Black,L,100% Cotton,India,2026-03-20
"DUDEME Fuda: While Alive...",399,Black,L,100% Cotton,India,2026-03-21
```

### Data Analysis

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load data
df = pd.read_csv('AmazonWebScrappingDataset.csv')

# View all price records
print(df)

# Price statistics
print(f"Current Price: ₹{df['Price'].iloc[-1]}")
print(f"Lowest Price: ₹{df['Price'].min()}")
print(f"Highest Price: ₹{df['Price'].max()}")
print(f"Average Price: ₹{df['Price'].mean():.2f}")

# Plot price trend
plt.figure(figsize=(10, 6))
plt.plot(df['Date'], df['Price'], marker='o')
plt.title('Amazon Product Price Trend')
plt.xlabel('Date')
plt.ylabel('Price (₹)')
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

## 📧 Email Notifications

### Email Setup

```python
def send_mail():
    # Gmail SMTP Configuration
    server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
    server.ehlo()
    server.login('your_email@gmail.com', 'your_app_password')

    # Email content
    subject = "Amazon Price Alert!"
    body = "The product you're tracking is now below your price threshold!"

    msg = f"Subject: {subject}\n\n{body}"
    
    # Send email
    server.sendmail(
        'your_email@gmail.com',
        'recipient@gmail.com',  # Can be same or different
        msg
    )
    
    print("Email sent successfully!")
    server.quit()
```

### Custom Email Template

```python
def send_mail():
    subject = f"🎉 Price Drop Alert: {title}"
    
    body = f"""
    Great news! The product you're tracking has dropped in price!
    
    Product: {title}
    Current Price: ₹{price}
    Previous Price: ₹{previous_price}
    Savings: ₹{previous_price - price}
    
    Color: {color}
    Size: {size}
    
    Buy now: {url}
    
    Happy Shopping! 🛒
    """
    
    msg = f"Subject: {subject}\n\n{body}"
    server.sendmail('your_email@gmail.com', 'recipient@gmail.com', msg)
```

### Email Security Best Practices

1. **Never commit passwords to GitHub**
   ```python
   # Use environment variables
   import os
   password = os.getenv('GMAIL_APP_PASSWORD')
   ```

2. **Use App Passwords, not account password**

3. **Store credentials in .env file**
   ```
   # .env file
   GMAIL_USER=your_email@gmail.com
   GMAIL_PASSWORD=your_app_password
   ```

---

## ⏰ Scheduling

### Option 1: Built-in Loop (Recommended for Testing)

```python
while(True):
    check_price()
    time.sleep(86400)  # 24 hours
```

### Option 2: Windows Task Scheduler

1. Create Python script file (`price_checker.py`)
2. Open Task Scheduler
3. Create New Task
4. Set trigger (daily at specific time)
5. Set action: `python price_checker.py`

### Option 3: Linux Cron Job

```bash
# Edit crontab
crontab -e

# Add job (runs daily at 9 AM)
0 9 * * * /usr/bin/python3 /path/to/price_checker.py
```

### Option 4: Cloud Deployment

**AWS Lambda + CloudWatch Events:**
- Deploy as Lambda function
- Schedule with CloudWatch Events
- Runs serverless in cloud

**Heroku Scheduler:**
- Deploy to Heroku
- Use Heroku Scheduler add-on
- Free tier available

---

## 🛠️ Technologies Used

### Core Technologies

| Technology | Purpose | Version |
|------------|---------|---------|
| **Python** | Programming language | 3.7+ |
| **BeautifulSoup4** | HTML parsing | Latest |
| **Requests** | HTTP requests | Latest |
| **Pandas** | Data management | Latest |
| **smtplib** | Email automation | Built-in |

### Libraries

```python
from bs4 import BeautifulSoup  # Web scraping
import requests                # HTTP requests
import time                    # Scheduling delays
import datetime                # Timestamps
import smtplib                 # Email sending
import csv                     # CSV file operations
import pandas as pd            # Data analysis
```

---

## 📂 Project Structure

```
Amazon-Price-Tracker/
│
├── Amazon_Web_Scrapping_Project.ipynb
│   └── Main Jupyter Notebook
│
├── AmazonWebScrappingDataset.csv
│   └── Price history data (generated)
│
├── price_checker.py (optional)
│   └── Standalone Python script
│
├── .env (create this)
│   └── Email credentials (DO NOT COMMIT)
│
├── requirements.txt
│   └── Python dependencies
│
└── README.md
    └── Project documentation (this file)
```

---

## ⚖️ Legal & Ethical Considerations

### Amazon's Terms of Service

**Important:** Web scraping Amazon may violate their Terms of Service. This project is for **educational purposes only**.

### Best Practices

1. **Respect robots.txt**
   ```
   Check: https://www.amazon.com/robots.txt
   ```

2. **Rate Limiting**
   - Don't overwhelm servers
   - Use reasonable delays (24 hours recommended)
   - Limit number of products tracked

3. **User-Agent**
   - Always identify your scraper
   - Use appropriate User-Agent header

4. **Personal Use Only**
   - Don't resell scraped data
   - Don't scrape at scale
   - Educational/personal use only

### Legal Alternatives

Consider using:
- **Amazon Product Advertising API** (official)
- **Keepa API** (price tracking service)
- **CamelCamelCamel** (price history)
- Browser extensions (Honey, Capital One Shopping)

---

## 🐛 Troubleshooting

### Common Issues

#### Issue 1: HTML Element Not Found
**Error:** `AttributeError: 'NoneType' object has no attribute 'get_text'`

**Solution:**
```python
# Add error handling
try:
    title = soup2.find(id='productTitle').get_text()
except AttributeError:
    title = "Title not found"
    print("Warning: Could not find product title")

# Or check if element exists
title_element = soup2.find(id='productTitle')
if title_element:
    title = title_element.get_text()
else:
    title = "N/A"
```

#### Issue 2: Request Blocked (403 Error)
**Error:** `403 Forbidden`

**Solutions:**
```python
# 1. Update User-Agent
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)...",
    "Accept": "text/html,application/xhtml+xml",
    "Accept-Language": "en-US,en;q=0.9",
}

# 2. Add delay between requests
time.sleep(5)

# 3. Use session with cookies
session = requests.Session()
session.get(url, headers=headers)
```

#### Issue 3: Email Not Sending
**Error:** `smtplib.SMTPAuthenticationError`

**Solutions:**
```python
# 1. Enable "Less secure app access" or use App Password
# 2. Check credentials
# 3. Verify Gmail SMTP settings

# Debug email sending
try:
    send_mail()
    print("Email sent successfully!")
except Exception as e:
    print(f"Email error: {e}")
```

#### Issue 4: Price Format Issues
**Error:** Cannot convert price to integer

**Solution:**
```python
# Clean price string properly
price = soup2.find(class_='a-price-whole').get_text()
price = price.strip().replace(',', '').replace('₹', '')
price = int(float(price))  # Handle decimal prices
```

#### Issue 5: Amazon Page Structure Changed
**Error:** Element IDs/classes changed

**Solution:**
```python
# Inspect current page structure
print(soup2.prettify())

# Update selectors
# Old: soup2.find(id='productTitle')
# New: soup2.find(class_='product-title-word-break')

# Use multiple fallback selectors
title = (
    soup2.find(id='productTitle') or
    soup2.find(class_='product-title') or
    soup2.find('h1', {'class': 'a-size-large'})
).get_text()
```

---

## 🔮 Future Enhancements

### Feature Additions
- [ ] Track multiple products simultaneously
- [ ] Support for other e-commerce sites (Flipkart, eBay)
- [ ] Price prediction using machine learning
- [ ] SMS notifications via Twilio
- [ ] Discord/Slack webhook notifications
- [ ] Web dashboard for visualization
- [ ] Mobile app for price alerts

### Technical Improvements
- [ ] Implement headless browser (Selenium/Playwright)
- [ ] Add proxy rotation to avoid blocking
- [ ] Database storage (SQLite/PostgreSQL)
- [ ] API endpoint for price data
- [ ] Docker containerization
- [ ] Unit tests and error handling
- [ ] Logging system for monitoring

### Analytics Features
- [ ] Price trend visualization
- [ ] Best time to buy predictions
- [ ] Competitor price comparison
- [ ] Historical price charts
- [ ] Deal score calculation
- [ ] Price drop percentage alerts

### User Experience
- [ ] GUI application (Tkinter/PyQt)
- [ ] Web interface (Flask/Django)
- [ ] Configuration file for settings
- [ ] Multiple price threshold alerts
- [ ] Wishlist management
- [ ] Export to Excel with charts

---

## 📊 Sample Output

### Console Output
```
2026-03-19
DUDEME Fuda: While Alive Eat Sleep Code Geek Printed Half Sleeve Cotton T Shirt
499
Black
L
100% Cotton
India
Price check completed!
```

### CSV Output
```
Title,Price,Color,Size,Material,Country,Date
"DUDEME Fuda: While Alive Eat Sleep Code...",499,Black,L,100% Cotton,India,2026-03-19
"DUDEME Fuda: While Alive Eat Sleep Code...",499,Black,L,100% Cotton,India,2026-03-20
"DUDEME Fuda: While Alive Eat Sleep Code...",399,Black,L,100% Cotton,India,2026-03-21
```

### Email Notification
```
Subject: The T-shirt you want to buy is below 400! This is your chance to buy!

Guru! This is the moment you have been waiting for! 
This is the great chance to buy your T-shirt at this price! 
Don't miss this opportunity!
```

---

## 🎓 Learning Outcomes

This project demonstrates:

- ✅ **Web Scraping**: BeautifulSoup for HTML parsing
- ✅ **HTTP Requests**: Using requests library
- ✅ **Data Storage**: CSV file operations
- ✅ **Email Automation**: SMTP protocol
- ✅ **Task Scheduling**: Time-based automation
- ✅ **Data Cleaning**: String manipulation
- ✅ **Error Handling**: Robust code practices
- ✅ **File I/O**: Reading and writing files

---

## 🤝 Contributing

Contributions welcome! Here's how:

1. **Fork the repository**
2. **Create feature branch**
   ```bash
   git checkout -b feature/NewFeature
   ```
3. **Make improvements**
   - Add new features
   - Fix bugs
   - Improve documentation
4. **Commit changes**
   ```bash
   git commit -m 'Add: New feature'
   ```
5. **Push and create PR**

### Contribution Ideas
- Add support for more sites
- Improve error handling
- Create web interface
- Add unit tests
- Implement database storage
- Build mobile app

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

**Disclaimer:** This project is for educational purposes only. Web scraping Amazon may violate their Terms of Service. Use responsibly and at your own risk.

---

## 📧 Contact & Connect

### Author

**Gururaj Krishna Sharma**

- 📧 Email: [guruuu2468@gmail.com](mailto:guruuu2468@gmail.com)
- 💼 LinkedIn: [Gururaj Krishna Sharma](https://www.linkedin.com/in/gururaj-krishna-sharma)
- 💻 GitHub: [@CODERGURU26](https://github.com/CODERGURU26)

---

## 🌟 Acknowledgments

- **BeautifulSoup** team for excellent parsing library
- **Requests** library developers
- **Python** community for documentation
- **Amazon** for product data (educational use)

---

## 📚 Additional Resources

### Learn More
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Requests Documentation](https://requests.readthedocs.io/)
- [Web Scraping Best Practices](https://www.scrapehero.com/web-scraping-best-practices/)
- [Gmail SMTP Setup](https://support.google.com/mail/answer/7126229)

### Related Projects
- CamelCamelCamel (Amazon price tracker)
- Keepa (price history)
- Honey browser extension
- Price comparison websites

---

## 🎯 Use Cases

**For Shoppers:**
- Save money on purchases
- Track wishlist items
- Never miss a sale
- Find best prices

**For Developers:**
- Learn web scraping
- Practice automation
- Build portfolio project
- Understand email APIs

**For Data Analysts:**
- Collect pricing data
- Analyze market trends
- Study price patterns
- Build datasets

---

**⭐ If you find this project helpful, please give it a star!**

**🔔 Watch this repository for updates!**

---

*Last Updated: February 2026*

**Happy Deal Hunting! 🛍️💰**

**Note:** Always respect website terms of service and use web scraping ethically and legally.
