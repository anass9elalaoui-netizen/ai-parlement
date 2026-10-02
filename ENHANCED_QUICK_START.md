# DIRAM Enhanced - Quick Start Guide
## نظام DIRAM المحسن - دليل البدء السريع

### 🚀 Professional Diplomatic Intelligence with OpenRouter & DeepSeek

---

## ✨ What's New in DIRAM Enhanced

- **🤖 Advanced AI Integration**: OpenRouter + DeepSeek V3 & R1 models
- **🇲🇦 Morocco-Focused Intelligence**: Specialized diplomatic analysis
- **💰 Cost-Effective**: Free DeepSeek R1 model + budget management
- **🌍 Multi-Language**: Arabic, English, French support
- **⚡ Real-Time Analysis**: Instant diplomatic insights
- **🎯 High Accuracy**: Professional-grade analysis with confidence scoring

---

## 🔑 Your API Configuration

**OpenRouter API Key**: `[REDACTED_API_KEY]`

**Available Models**:
- **DeepSeek V3** (`deepseek/deepseek-chat`) - General analysis - $0.38/$0.89 per 1M tokens
- **DeepSeek R1** (`deepseek/deepseek-r1:free`) - Reasoning model - **FREE**
- **Qwen Large** (`qwen/qwen-2.5-72b-instruct`) - Multilingual - $1.50/$3.00 per 1M tokens

---

## 🏃‍♂️ Quick Start (5 Minutes)

### 1. Install Dependencies
```bash
pip install fastapi uvicorn aiohttp pydantic-settings
```

### 2. Start the Server
```bash
cd backend
python main.py
```

### 3. Test the System
```bash
# Open browser and go to:
http://localhost:8000/api/docs

# Or test with curl:
curl http://localhost:8000/health
```

---

## 🔥 Key Features & Endpoints

### 📊 Enhanced Analysis
```bash
POST /api/enhanced/analyze-article
{
  "content": "Morocco and Spain discuss bilateral trade agreements",
  "language": "en",
  "analysis_depth": "comprehensive"
}
```

### ⚡ Quick Analysis
```bash
POST /api/enhanced/quick-analysis?content=your_text&language=ar
```

### 🇲🇦 Morocco Relevance
```bash
POST /api/enhanced/morocco-relevance?content=your_diplomatic_content
```

### 📋 Intelligence Briefing
```bash
POST /api/enhanced/intelligence-briefing
{
  "articles": [...],
  "focus_region": "North Africa",
  "language": "ar"
}
```

### 💰 Usage Statistics
```bash
GET /api/enhanced/usage-stats
```

### 🏥 Health Check
```bash
GET /api/enhanced/health
```

---

## 💡 Usage Examples

### Example 1: Analyze Diplomatic Content
```python
import aiohttp
import asyncio

async def analyze_content():
    async with aiohttp.ClientSession() as session:
        payload = {
            "content": "المغرب وإسبانيا يناقشان التعاون الأمني",
            "language": "ar",
            "analysis_depth": "comprehensive"
        }
        
        async with session.post(
            "http://localhost:8000/api/enhanced/analyze-article",
            json=payload
        ) as response:
            result = await response.json()
            print(f"Morocco Relevance: {result['analysis']['morocco_relevance']}/100")
            print(f"Risk Level: {result['analysis']['risk_level']}")

asyncio.run(analyze_content())
```

### Example 2: Quick Intelligence Check
```bash
curl -X POST "http://localhost:8000/api/enhanced/quick-analysis" \
  -G -d "content=Morocco and Algeria discuss border security" \
  -d "language=en"
```

---

## 🎯 Professional Features

### 🔍 Advanced Analysis Capabilities
- **Diplomatic Sentiment Analysis**
- **Entity Recognition** (Countries, Leaders, Organizations)
- **Risk Assessment** (LOW/MEDIUM/HIGH/CRITICAL)
- **Morocco Relevance Scoring** (0-100)
- **Strategic Recommendations**
- **Cost Tracking & Budget Management**

### 🌍 Multi-Language Support
- **Arabic**: Native support for diplomatic Arabic content
- **English**: International diplomatic communications
- **French**: Francophone diplomatic relations

### 💰 Cost Management
- **Daily Budget**: $25 limit with monitoring
- **Free Model**: DeepSeek R1 for complex reasoning (no cost)
- **Cost Tracking**: Real-time usage statistics
- **Budget Alerts**: Automatic warnings at 80% usage

---

## 🔧 Architecture Overview

```
Frontend (Blazor) 
    ↓
FastAPI Backend (/api/enhanced/*)
    ↓
Enhanced OpenRouter Client
    ↓
AI Models (DeepSeek V3, R1, Qwen)
    ↓
Morocco-Focused Analysis
    ↓
Diplomatic Intelligence Results
```

---

## 📊 Testing Your Setup

### 1. Run the Test Suite
```bash
python test_enhanced_diram.py
```

### 2. Check API Documentation
Visit: `http://localhost:8000/api/docs`

### 3. Test Individual Endpoints
```bash
# Health check
curl http://localhost:8000/api/enhanced/health

# Models info
curl http://localhost:8000/api/enhanced/models-info

# Usage stats
curl http://localhost:8000/api/enhanced/usage-stats
```

---

## 🚨 Important Notes

### Security
- ✅ API key is properly configured
- ✅ CORS enabled for development
- ✅ Error handling implemented
- ✅ Budget limits enforced

### Performance
- ⚡ Async operations for speed
- 🎯 Optimized for diplomatic content
- 💾 Efficient memory usage
- 🔄 Automatic retries on failures

### Costs
- 🆓 DeepSeek R1 model is completely free
- 💰 DeepSeek V3: ~$0.001 per analysis
- 📊 Real-time cost tracking
- 🚦 Budget alerts and limits

---

## 📈 Next Steps

1. **✅ Test the enhanced analysis endpoints**
2. **📊 Monitor usage statistics and costs**
3. **🔧 Customize analysis parameters for your needs**
4. **📱 Integrate with your existing systems**
5. **📊 Set up monitoring and alerting**
6. **🎯 Add custom Morocco-specific keywords**

---

## 🆘 Troubleshooting

### Common Issues
1. **AI requests failing**: Check your internet connection and API key
2. **Budget exceeded**: Monitor usage at `/api/enhanced/usage-stats`
3. **Slow responses**: Use DeepSeek R1 (free) for complex analysis
4. **Analysis errors**: Check content length (max ~5000 chars)

### Support
- 📋 Check API documentation: `http://localhost:8000/api/docs`
- 🏥 Health check: `http://localhost:8000/api/enhanced/health`
- 📊 Usage stats: `http://localhost:8000/api/enhanced/usage-stats`

---

## 🎉 Success!

Your **DIRAM Enhanced** system is now ready for professional diplomatic intelligence analysis!

🔑 **API Key Active** | 🤖 **AI Models Ready** | 🇲🇦 **Morocco Focus** | �� **Budget Managed** 
