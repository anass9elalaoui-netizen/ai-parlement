# 🇲🇦 DIRAM - Diplomatic Intelligence & Relations Analyzer for Morocco

> **نظام تحليل الذكاء والعلاقات الدبلوماسية للمغرب**  
> Advanced AI-powered system for analyzing diplomatic intelligence and international relations affecting Morocco

## 🎯 Overview

DIRAM is a comprehensive diplomatic intelligence analysis system designed specifically for Morocco's foreign affairs and international relations. The system leverages advanced AI technologies to monitor, analyze, and provide insights on global diplomatic activities that impact Morocco's interests.

### Key Features

- **🤖 AI-Powered Analysis**: Advanced sentiment analysis, entity extraction, and summarization
- **🌐 Multi-Source Scraping**: Automated collection from international news sources
- **🚨 Real-Time Alerts**: Intelligent alerts for critical diplomatic developments
- **📊 Risk Assessment**: Automated diplomatic risk evaluation and scoring
- **🔍 Morocco Relevance Scoring**: Specialized algorithms to assess relevance to Morocco
- **🌍 Multi-Language Support**: Arabic, English, French, and Spanish
- **👥 Role-Based Access**: Secure access control for different government departments
- **📈 Dashboard Analytics**: Comprehensive analytics and reporting capabilities

## 🏗️ Architecture

```
📁 DIRAM Project Structure
├── 🔧 backend/                 # FastAPI Backend Services
│   ├── 🚀 main.py             # FastAPI application entry point
│   ├── 🛠️ api/                 # API endpoints
│   │   ├── articles.py        # Article management & analysis
│   │   ├── users.py           # Authentication & user management
│   │   └── alerts.py          # Alert system & notifications
│   ├── ⚙️ services/            # Business logic & AI services
│   │   ├── summarizer.py      # AI summarization service
│   │   ├── sentiment.py       # Sentiment analysis service
│   │   ├── ner.py             # Named entity recognition
│   │   └── tone.py            # Diplomatic tone analysis
│   ├── 🏢 core/                # Domain models
│   │   ├── article.py         # Article domain models
│   │   ├── user.py            # User & permissions models
│   │   └── analysis.py        # Analysis result models
│   └── 🗄️ database/           # Database layer
│       ├── models.py          # SQLAlchemy ORM models
│       └── db_session.py      # Database session management
│
├── 🤖 ai_engine/              # AI Integration Layer
│   ├── openrouter_client.py   # OpenRouter AI client
│   ├── 📝 prompts/            # AI prompts library
│   └── utils.py               # AI utilities
│
├── 🕷️ scrapers/               # Web Scraping Services
│   ├── france24_scraper.py    # France 24 news scraper
│   ├── reuters_scraper.py     # Reuters news scraper
│   ├── aljazeera_scraper.py   # Al Jazeera scraper
│   └── [other news sources]
│
├── 🎨 frontend/               # Blazor Web UI
│   ├── Pages/                 # Web pages
│   ├── Components/            # Reusable components
│   ├── Services/              # Frontend services
│   └── Models/                # Data transfer objects
│
├── 🔧 shared/                 # Shared utilities
│   ├── settings.py            # Configuration management
│   └── constants.py           # System constants
│
├── 📊 reports/                # Report generation
│   └── generate_report.py     # PDF/HTML report generator
│
└── 🧪 tests/                  # Test suites
    ├── test_articles.py       # Article testing
    └── test_ai_engine.py      # AI engine testing
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- .NET 6.0+ (for Blazor frontend)
- SQLite/PostgreSQL/MySQL
- OpenRouter API key (for AI features)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-org/diram-diplomatic-ai.git
   cd diram-diplomatic-ai
   ```

2. **Set up Python environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Configure environment**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Initialize database**
   ```bash
   python -m backend.database.init_db
   ```

5. **Start the backend**
   ```bash
   uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
   ```

6. **Start the frontend** (separate terminal)
   ```bash
   start_frontend.bat
   ```

### Default Credentials

- **Username**: `admin`
- **Password**: `admin123`
- **Email**: `admin@diram.ma`

⚠️ **Change default credentials immediately in production!**

## 🔧 Configuration

### Environment Variables

Key environment variables in `.env`:

```bash
# AI Configuration
OPENROUTER_API_KEY="your-api-key-here"
DEFAULT_AI_MODEL="anthropic/claude-3-sonnet"

# Database
DATABASE_URL="sqlite:///./diram_database.db"

# Security
SECRET_KEY="your-secret-key-here"

# Email Notifications
SMTP_HOST="smtp.gmail.com"
SMTP_USERNAME="your-email@gmail.com"
SMTP_PASSWORD="your-app-password"
```

### AI Models Supported

- **Claude 3 Sonnet** (Recommended for Arabic)
- **GPT-4** (Good for multilingual analysis)
- **Mistral Large** (Cost-effective option)
- **Llama 3** (Open-source alternative)

## 📖 API Documentation

### Authentication

```bash
# Login
POST /api/users/login
{
  "username": "admin",
  "password": "admin123"
}

# Response
{
  "access_token": "eyJ...",
  "token_type": "bearer",
  "user": {...}
}
```

### Article Analysis

```bash
# Upload and analyze article
POST /api/articles/upload
Content-Type: multipart/form-data

title: "Article Title"
content: "Article content..."
source: "Reuters"
language: "ar"
```

### Alerts Management

```bash
# Get active alerts
GET /api/alerts/?priority=HIGH&active_only=true

# Create custom alert
POST /api/alerts/
{
  "title": "Alert Title",
  "description": "Alert description",
  "alert_type": "DIPLOMATIC_CRISIS",
  "priority": "HIGH"
}
```

## 🔒 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Role-Based Access Control**: Multiple user roles (Admin, Analyst, Viewer, Guest)
- **Input Validation**: Comprehensive input sanitization
- **Rate Limiting**: API rate limiting to prevent abuse
- **CORS Protection**: Configurable CORS policies
- **Data Encryption**: Sensitive data encryption at rest

## 🌐 Supported News Sources

### International Sources
- **Reuters** - Global news and analysis
- **BBC World** - British perspective on global events
- **France 24** - French international news
- **Deutsche Welle** - German international broadcaster
- **Al Jazeera** - Middle Eastern perspective

### Regional Sources
- **Jeune Afrique** - African affairs
- **Middle East Eye** - Middle Eastern analysis
- **Le Monde** - French newspaper
- **The Guardian** - British newspaper

### Official Sources
- **UN News** - United Nations official news
- **EU Council** - European Union updates
- **African Union** - Continental organization news

## 🤖 AI Analysis Capabilities

### Sentiment Analysis
- **Multilingual Support**: Arabic, English, French, Spanish
- **Diplomatic Context**: Specialized for diplomatic language
- **Emotion Detection**: Joy, anger, fear, sadness analysis
- **Confidence Scoring**: Reliability metrics for each analysis

### Named Entity Recognition
- **Diplomatic Entities**: Countries, organizations, officials
- **Geographic Entities**: Cities, regions, landmarks
- **Temporal Entities**: Dates, events, periods
- **Economic Entities**: Trade agreements, currencies, markets

### Risk Assessment
- **Diplomatic Risk**: Crisis, tensions, conflicts
- **Economic Risk**: Trade impacts, sanctions, partnerships
- **Security Risk**: Threats, military activities, terrorism
- **Regional Risk**: Spillover effects, migration, stability

### Morocco Relevance Scoring
- **Direct Mentions**: Morocco, Rabat, Casablanca references
- **Regional Relevance**: Maghreb, North Africa, Sahel
- **Bilateral Relations**: Partner countries and relationships
- **Economic Partnerships**: Trade agreements and investments

## 👥 User Roles & Permissions

### Admin
- Full system access
- User management
- System configuration
- All analysis features

### Analyst
- Article upload and analysis
- Alert creation
- Export capabilities
- Dashboard access

### Viewer
- Read-only article access
- View analysis results
- Dashboard viewing
- Export reports

### Guest
- Limited article access
- Basic analysis viewing
- No administrative functions

## 📊 Dashboard & Analytics

### Key Metrics
- **Article Volume**: Daily/weekly/monthly article counts
- **Risk Distribution**: Breakdown by risk levels
- **Source Analysis**: Performance by news source
- **Language Statistics**: Content distribution by language
- **User Activity**: System usage analytics

### Visualizations
- **Risk Trend Charts**: Risk level changes over time
- **Geographic Heat Maps**: Global activity visualization
- **Sentiment Trends**: Emotional analysis over time
- **Entity Networks**: Relationship mapping

## 🔄 Automated Workflows

### Scheduled Scraping
- **Frequency**: Every 6 hours (configurable)
- **Sources**: Multiple international news sources
- **Filtering**: Morocco-relevant content prioritization
- **Processing**: Automatic analysis pipeline

### Alert Generation
- **Real-time Processing**: Immediate analysis of new articles
- **Risk Thresholds**: Configurable alert triggers
- **Notification Channels**: Email, push notifications, dashboard
- **Escalation Rules**: Priority-based routing

### Data Management
- **Auto-archiving**: Old articles automatic archiving
- **Backup Scheduling**: Regular database backups
- **Cache Management**: Analysis result caching
- **Performance Optimization**: Automatic system optimization

## 🧪 Testing

### Unit Tests
```bash
pytest tests/unit/ -v
```

### Integration Tests
```bash
pytest tests/integration/ -v
```

### API Tests
```bash
pytest tests/api/ -v
```

### Performance Tests
```bash
pytest tests/performance/ -v
```

## 📈 Performance & Scalability

### Current Specifications
- **Concurrent Users**: Up to 100 concurrent users
- **Article Processing**: 1000+ articles per hour
- **Analysis Speed**: 2-5 seconds per article
- **Database**: Optimized for 1M+ articles

### Scaling Options
- **Horizontal Scaling**: Multiple backend instances
- **Database Sharding**: Distribute data across databases
- **CDN Integration**: Static content delivery
- **Caching Layers**: Redis/Memcached integration

## 🛠️ Development

### Code Style
- **Python**: PEP 8 compliance
- **Type Hints**: Full type annotation
- **Documentation**: Comprehensive docstrings
- **Linting**: flake8, black, mypy

### Git Workflow
```bash
# Feature development
git checkout -b feature/new-analysis-type
git commit -m "feat: add new analysis type"
git push origin feature/new-analysis-type
```

### Contributing
1. Fork the repository
2. Create feature branch
3. Add tests for new features
4. Ensure all tests pass
5. Submit pull request

## 📋 Deployment

### Docker Deployment
```bash
# Build and run with Docker Compose
docker-compose up -d
```

### Manual Deployment
```bash
# Production setup
pip install -r requirements.txt
export ENVIRONMENT=production
uvicorn backend.main:app --host 0.0.0.0 --port 8000
```

### Environment-Specific Settings
- **Development**: Debug enabled, SQLite database
- **Staging**: Production-like with test data
- **Production**: Optimized, PostgreSQL, monitoring

## 🔍 Monitoring & Logging

### Application Monitoring
- **Health Checks**: API endpoint monitoring
- **Performance Metrics**: Response time tracking
- **Error Tracking**: Exception monitoring
- **User Analytics**: Usage pattern analysis

### Logging
- **Structured Logging**: JSON format logs
- **Log Levels**: DEBUG, INFO, WARNING, ERROR
- **Log Rotation**: Automatic log file rotation
- **Centralized Logging**: Optional ELK stack integration

## 🆘 Troubleshooting

### Common Issues

#### AI Service Not Working
```bash
# Check API key configuration
echo $OPENROUTER_API_KEY

# Test connection
curl -H "Authorization: Bearer $OPENROUTER_API_KEY" \
     https://openrouter.ai/api/v1/models
```

#### Database Connection Issues
```bash
# Check database URL
python -c "from backend.database.db_session import engine; print(engine.url)"

# Test connection
python -c "from backend.database.db_session import get_db; next(get_db())"
```

#### Scraping Not Working
```bash
# Check scraping service
python -m scrapers.france24_scraper --test

# Verify network connectivity
curl -I https://www.france24.com
```

## 📞 Support

For technical support and questions:

- **Email**: support@diram.ma
- **Documentation**: [docs.diram.ma](https://docs.diram.ma)
- **Issues**: [GitHub Issues](https://github.com/your-org/diram/issues)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **OpenRouter** for AI API services
- **FastAPI** for the excellent Python framework
- **Microsoft Blazor** for the web frontend
- **SQLAlchemy** for database ORM
- **The open-source community** for various libraries and tools

---

**Built with ❤️ for Morocco's diplomatic intelligence needs**

*"في خدمة الدبلوماسية المغربية والتحليل الاستراتيجي"* 

# DIRECT START - No delays, Morocco focus
articles = await scraper.scrape_articles(
    max_articles=15,
    days_back=15,
    morocco_only=True
) 

# Last 30 days for comprehensive intelligence
articles = await scraper.scrape_articles(
    max_articles=30,
    days_back=30,
    morocco_only=True
) 

# Minimal delay testing
articles = await scraper.scrape_articles(
    max_articles=5,
    days_back=7,
    morocco_only=False
) 

# Run comprehensive diagnostics
diagnose_system.bat

# Or manual frontend startup
cd frontend
dotnet restore
dotnet build --configuration Release
dotnet run --urls http://localhost:5000
