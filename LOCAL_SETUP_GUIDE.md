# DIRAM Local Setup Guide
## Complete Guide to Run DIRAM System on Your Local Machine 🏠

---

## 📋 Prerequisites

### System Requirements:
- **Python 3.8+** (Recommended: Python 3.10 or newer)
- **4GB RAM minimum** (8GB recommended)
- **2GB free disk space**
- **Internet connection** (for AI services and news scraping)

### Check Python Version:
```bash
python --version
# Should show Python 3.8 or higher
```

---

## 🛠️ Step 1: Install Dependencies

```bash
# Install all required packages
pip install -r requirements.txt

# Or install manually if requirements.txt fails:
pip install fastapi uvicorn sqlalchemy passlib[bcrypt] aiohttp beautifulsoup4 schedule psutil python-multipart jinja2
```

---

## 💾 Step 2: Database Setup

### **Option A: Automatic Setup (Recommended for beginners)**
```bash
# Run the database setup script
python setup_database.py
```

This will automatically:
- ✅ Create SQLite database file: `diram_database.db`
- ✅ Create all tables (users, articles, alerts, analysis_results)
- ✅ Create admin user (username: `admin`, password: `admin123`)
- ✅ Add 3 sample articles for testing
- ✅ Add sample analysis results

### **Option B: Manual Setup**
```bash
# If automatic setup doesn't work, try manual initialization:
python -c "
import asyncio
from backend.database.db_session import init_db
asyncio.run(init_db())
print('✅ Database initialized manually!')
"
```

### **Option C: Reset Database (if needed)**
```bash
# Reset everything and start fresh
python setup_database.py reset
```

---

## 🔑 Step 3: Configuration (Optional)

### Create Environment File:
Create a `.env` file in the project root directory:

```bash
# AI Configuration (Optional - for enhanced AI features)
OPENROUTER_API_KEY=your_openrouter_api_key_here

# Database Configuration (Optional - defaults to SQLite)
DATABASE_URL=sqlite:///./diram_database.db

# Security Configuration
SECRET_KEY=your-secret-key-here
```

### Get OpenRouter API Key (Optional):
1. Visit: https://openrouter.ai/
2. Sign up for a free account
3. Get your API key from the dashboard
4. Add it to your `.env` file

**Note:** System works without API key, but AI features will be limited.

---

## 🚀 Step 4: Start the System

### **Method 1: Simple Start (Recommended)**
```bash
python backend/main.py
```

### **Method 2: Using Uvicorn**
```bash
uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
```

### **Method 3: Custom Port**
```bash
uvicorn backend.main:app --port 8001  # If port 8000 is busy
```

---

## 🌐 Step 5: Access Your System

Once the server starts, you can access:

### **Main URLs:**
- **🏠 Home Page:** http://localhost:8000/
- **📚 API Documentation:** http://localhost:8000/docs
- **📖 Alternative Docs:** http://localhost:8000/redoc
- **❤️ Health Check:** http://localhost:8000/health
- **🧪 AI Test:** http://localhost:8000/api/test-ai

### **Default Login Credentials:**
```
👤 Username: admin
🔐 Password: admin123
📧 Email: admin@diram.ma
🏢 Department: Foreign Affairs
```

---

## 🧪 Step 6: Test Everything

### **Test 1: Database Connection**
```bash
python setup_database.py info
```
**Expected Output:**
```
📊 Database Statistics:
   👥 Users: 1
   📰 Articles: 3
   🚨 Alerts: 0
   🔬 Analysis Results: 3
```

### **Test 2: Enhanced Components**
```bash
python test_enhanced_components.py
```
**Expected Output:**
```
✅ Enhanced International Scrapers: Ready
✅ Advanced Alert System: Ready
✅ Background Processor: Ready
```

### **Test 3: News Scraping**
```bash
python scrapers/test_scrapers.py
```

### **Test 4: API Endpoints**
```bash
# Test health endpoint
curl http://localhost:8000/health

# Test articles endpoint  
curl http://localhost:8000/api/articles/
```

---

## 🔄 Step 7: Background Processing (Advanced)

### **Start Background Processor:**
Create a file called `start_background.py`:
```python
import asyncio
from backend.services.background_processor import BackgroundProcessor

async def main():
    async with BackgroundProcessor() as processor:
        processor.start()
        print("🔄 Background processor started...")
        try:
            while True:
                await asyncio.sleep(60)
        except KeyboardInterrupt:
            print("🛑 Background processor stopped")

if __name__ == "__main__":
    asyncio.run(main())
```

Then run:
```bash
python start_background.py
```

### **What Background Processor Does:**
- **🕷️ Automated News Scraping:** Every 30 minutes
- **🚨 Alert Generation:** Every 15 minutes  
- **🏥 System Health Checks:** Every 10 minutes
- **🧹 Database Cleanup:** Daily at 2:00 AM
- **🤖 AI Model Optimization:** Weekly on Sundays

---

## ⚡ Quick Start Summary

### **For Beginners (3 Simple Commands):**
```bash
# 1. Install everything
pip install -r requirements.txt

# 2. Setup database with sample data
python setup_database.py

# 3. Start the server
python backend/main.py
```

### **Daily Development Workflow:**
```bash
# Morning: Start the system
python backend/main.py

# Test components
python test_enhanced_components.py

# Check database status
python setup_database.py info

# Test scraping
python scrapers/test_scrapers.py
```

---

## 🔧 Troubleshooting Common Issues

### **Issue 1: "ModuleNotFoundError: No module named '...'"**
**Solution:**
```bash
pip install -r requirements.txt
# Or install specific package:
pip install sqlalchemy fastapi uvicorn
```

### **Issue 2: "Database connection failed"**
**Solution:**
```bash
# Reset database
python setup_database.py reset

# Or check file permissions
ls -la diram_database.db  # Linux/Mac
dir diram_database.db     # Windows
```

### **Issue 3: "Port 8000 already in use"**
**Solution:**
```bash
# Use different port
uvicorn backend.main:app --port 8001

# Or kill existing process (Linux/Mac)
lsof -ti:8000 | xargs kill -9

# Windows: Find and kill process
netstat -ano | findstr :8000
taskkill /PID [PID_NUMBER] /F
```

### **Issue 4: "AI features not working"**
**Solution:**
```bash
# Check if API key is set
echo $OPENROUTER_API_KEY  # Linux/Mac
echo %OPENROUTER_API_KEY% # Windows

# System still works without AI key (basic features only)
```

### **Issue 5: "Scraping tests fail"**
**Solution:**
```bash
# Check internet connection
ping google.com

# Test individual components
python scrapers/mock_scraper.py
```

### **Nuclear Option - Reset Everything:**
```bash
# Delete everything and start fresh
rm -f diram_database.db    # Linux/Mac
del diram_database.db      # Windows

# Clear Python cache
rm -rf __pycache__ backend/__pycache__ scrapers/__pycache__

# Re-setup
python setup_database.py
```

---

## 📁 Understanding File Structure

```
diram-diplomatic-ai/
├── 📁 backend/                          # Main FastAPI application
│   ├── 📁 api/                         # API endpoints
│   │   ├── 📁 international/              # Individual scrapers
│   └── main.py                        # FastAPI app entry point
├── 📁 scrapers/                        # News scraping system
│   ├── enhanced_international_scrapers.py  # Main scraper
│   └── test_scrapers.py               # Scraper tests
├── 📁 ai_engine/                       # AI analysis engine
│   ├── enhanced_openrouter_client.py  # AI client
│   └── 📁 prompts/                    # AI prompts
├── 📁 frontend/                        # Web interface (Blazor)
├── 📁 shared/                          # Shared configurations
├── setup_database.py                  # Database setup script
├── test_enhanced_components.py        # System tests
├── requirements.txt                   # Python dependencies
├── diram_database.db                  # SQLite database (created after setup)
├── LOCAL_SETUP_GUIDE.md              # This guide
└── .env                               # Environment variables (you create this)
```

---

## 📊 Database Information

### **Database Tables Created:**
1. **👥 users** - User accounts and authentication
2. **📰 articles** - Scraped news articles
3. **🔬 analysis_results** - AI analysis results
4. **🚨 alerts** - Diplomatic alerts and notifications

### **Default Data Created:**
- **1 Admin User:** admin/admin123
- **3 Sample Articles:** English, Arabic, French content
- **3 Analysis Results:** AI analysis examples

### **Database Commands:**
```bash
# View database info
python setup_database.py info

# Reset database
python setup_database.py reset

# Test connection
python -c "from backend.database.db_session import DatabaseManager; print('✅ Connected' if DatabaseManager.test_connection() else '❌ Failed')"
```

---

## 🎯 What You Get After Setup

### **Core Features:**
- **🤖 AI-Powered Analysis:** Sentiment, entities, risk assessment
- **📰 Automated News Monitoring:** Real-time scraping from international sources
- **🚨 Intelligent Alert System:** Morocco-focused diplomatic alerts
- **📊 Analytics Dashboard:** Comprehensive analysis and reporting
- **🔐 Secure Authentication:** User management and role-based access

### **Morocco-Specific Features:**
- **🇲🇦 Morocco Relevance Scoring:** Articles ranked by Morocco relevance
- **🏛️ Diplomatic Context:** Western Sahara, Maghreb relations, etc.
- **🌍 International Relations:** EU, Africa, Gulf cooperation monitoring
- **⚡ Real-time Alerts:** Critical diplomatic developments
- **📈 Trend Analysis:** Pattern detection and intelligence briefings

---

## 🚀 Next Steps After Setup

### **Immediate Actions:**
1. **✅ Verify System Health:** Check all test scripts pass
2. **🔧 Configure API Keys:** Add OpenRouter key for enhanced AI
3. **📊 Explore Dashboard:** Browse API docs and test endpoints
4. **🧪 Run Sample Tests:** Test scraping and analysis features

### **Advanced Configuration:**
1. **⚙️ Customize Alert Rules:** Modify Morocco-specific keywords
2. **🔄 Setup Background Processing:** Enable automated operations
3. **📱 Configure Notifications:** Email/SMS alerts for critical events
4. **📈 Performance Tuning:** Optimize for your hardware

### **Production Considerations:**
1. **🔐 Change Default Passwords:** Update admin credentials
2. **🛡️ Security Hardening:** Configure HTTPS and security headers
3. **💾 Database Backup:** Setup regular backups
4. **📊 Monitoring:** Add logging and performance monitoring

---

## 💡 Pro Tips

### **Development Tips:**
- **Start with SQLite:** Easy setup, upgrade to PostgreSQL later if needed
- **Use Background Processor:** Enables full automation capabilities
- **Monitor Resources:** Keep an eye on CPU/memory with `htop` or Task Manager
- **Regular Testing:** Run test scripts after any changes

### **Performance Tips:**
- **SSD Storage:** Faster database operations
- **8GB+ RAM:** Better for concurrent operations
- **Good Internet:** Faster news scraping
- **Clean Cache:** Regular cleanup of Python cache files

### **Debugging Tips:**
- **Check Console Output:** Most errors appear in terminal
- **Test Components Individually:** Isolate issues using test scripts
- **Reset When Stuck:** `python setup_database.py reset` fixes many issues
- **Check File Permissions:** Ensure write access to database file

---

## 🆘 Need More Help?

### **If You're Still Having Issues:**

1. **📋 Run Full Diagnostics:**
   ```bash
   python test_enhanced_components.py
   python setup_database.py info
   python -c "import sys; print(f'Python: {sys.version}')"
   ```

2. **🔍 Check System Requirements:**
   - Python 3.8+ installed
   - All packages from requirements.txt installed
   - Internet connection working
   - Sufficient disk space (2GB+)

3. **🔄 Try Complete Reset:**
   ```bash
   # Delete database
   rm -f diram_database.db
   
   # Reinstall packages
   pip uninstall -y -r requirements.txt
   pip install -r requirements.txt
   
   # Re-setup
   python setup_database.py
   ```

---

## 🎉 Congratulations!

### **You Now Have a Complete Diplomatic Intelligence System!**

**Your DIRAM system includes:**
- ✅ **Professional-grade database** with diplomatic data models
- ✅ **AI-powered analysis** using state-of-the-art language models
- ✅ **Automated news monitoring** from international sources
- ✅ **Intelligent alert system** with Morocco-specific rules
- ✅ **Background processing** for hands-off operation
- ✅ **RESTful API** for integration with other systems
- ✅ **Comprehensive testing** suite for reliability

**Access your system at: 🌐 http://localhost:8000**

**Default login: 👤 admin / 🔐 admin123**

---

### **Welcome to the Future of Diplomatic Intelligence! 🌟🇲🇦**
