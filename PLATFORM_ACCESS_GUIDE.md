# 🌐 DIRAM Platform Access Guide

## ✅ Platform Status
- **Status**: ✅ ACTIVE AND RUNNING
- **Version**: 2.0.0 Enhanced
- **Message**: DIRAM - Enhanced Diplomatic Intelligence & Relations Analyzer for Morocco

---

## 🔗 **How to Access the Platform**

### 1. 🏠 **Main Platform Interface**
```
http://localhost:8000
```
- **What you'll see**: Platform status and basic information
- **Response**: JSON with system status, version, and description

### 2. 📚 **Interactive API Documentation (Swagger UI)** ⭐ **RECOMMENDED**
```
http://localhost:8000/docs
```
- **What you'll see**: Complete interactive API documentation
- **Features**: 
  - Test all API endpoints directly in browser
  - See request/response examples
  - Authentication testing
  - Real-time API exploration

### 3. 📖 **Alternative API Documentation (ReDoc)**
```
http://localhost:8000/redoc
```
- **What you'll see**: Clean, readable API documentation
- **Features**: Detailed endpoint descriptions and schemas

### 4. 🔧 **OpenAPI JSON Schema**
```
http://localhost:8000/openapi.json
```
- **What you'll see**: Raw OpenAPI specification
- **Use for**: API integration, client generation

---

## 🎯 **Available API Endpoints**

### **Enhanced Analysis APIs** (`/api/enhanced/*`)
1. **Analyze Article**: `POST /api/enhanced/analyze-article`
2. **Intelligence Briefing**: `POST /api/enhanced/intelligence-briefing`
3. **Morocco Relevance**: `POST /api/enhanced/morocco-relevance`
4. **Detect Entities**: `POST /api/enhanced/detect-entities`
5. **Usage Statistics**: `GET /api/enhanced/usage-stats`
6. **Health Check**: `GET /api/enhanced/health`
7. **Quick Analysis**: `POST /api/enhanced/quick-analysis`
8. **Models Info**: `GET /api/enhanced/models-info`

### **Intelligence Operations APIs** (`/api/intelligence/*`)
1. **Threat Assessment**: `POST /api/intelligence/threat-assessment`
2. **Intelligence Analysis**: `POST /api/intelligence/intelligence-analysis`
3. **Geopolitical Analysis**: `POST /api/intelligence/geopolitical-analysis`
4. **Diplomatic Relations**: `POST /api/intelligence/diplomatic-relations`
5. **Strategic Briefing**: `POST /api/intelligence/strategic-briefing`
6. **Intelligence Dashboard**: `GET /api/intelligence/intelligence-dashboard`
7. **Threat Monitoring**: `POST /api/intelligence/threat-monitoring`
8. **Operations Status**: `GET /api/intelligence/operations-status`

### **Core APIs** (`/api/*`)
- **Articles**: `/api/articles/*`
- **Users**: `/api/users/*`
- **Alerts**: `/api/alerts/*`
- **Health**: `/api/health`

---

## 🚀 **How to Use the Platform**

### **Step 1: Open Your Browser**
Navigate to the **Swagger UI** for the best experience:
```
http://localhost:8000/docs
```

### **Step 2: Explore Available Endpoints**
You'll see all APIs organized by categories:
- 🧠 **Enhanced AI Analysis** (8 endpoints)
- 🎯 **Intelligence Operations** (8 endpoints)
- 📰 **Articles Management**
- 👥 **Users Management**
- 🚨 **Alerts System**

### **Step 3: Test APIs Directly**
1. Click on any endpoint to expand it
2. Click "Try it out"
3. Fill in required parameters
4. Click "Execute"
5. See real-time results!

---

## 💡 **Quick Examples**

### **Test Morocco Relevance Analysis**
1. Go to: `http://localhost:8000/docs`
2. Find: `POST /api/enhanced/morocco-relevance`
3. Click "Try it out"
4. Enter text: `"Morocco and Spain discuss renewable energy cooperation"`
5. Click "Execute"
6. See Morocco relevance score!

### **Test Threat Assessment**
1. Go to: `http://localhost:8000/docs`
2. Find: `POST /api/intelligence/threat-assessment`
3. Click "Try it out"
4. Enter diplomatic content
5. Get comprehensive threat analysis!

### **Check AI Usage Statistics**
1. Go to: `http://localhost:8000/docs`
2. Find: `GET /api/enhanced/usage-stats`
3. Click "Try it out"
4. Click "Execute"
5. See current AI budget and usage!

---

## 🌍 **International News Sources Available**

The platform monitors 5 major international sources:

1. **France24** 🇫🇷
   - Priority: 4/5
   - Languages: French, English
   - Sections: Africa, Middle East, International, Live News

2. **Al Jazeera** 🌍
   - Priority: 5/5
   - Languages: English, Arabic
   - Sections: Middle East, Africa, News, Politics

3. **Reuters** 📰
   - Priority: 5/5
   - Language: English
   - Sections: Africa, Middle East, World, Politics

4. **Jeune Afrique** 🌍
   - Priority: 3/5
   - Language: French
   - Focus: Maghreb, Politics, Economy
   - **High Morocco Relevance Factor**

5. **UN News** 🇺🇳
   - Priority: 4/5
   - Language: English
   - Sections: Africa, Peace & Security, Development

---

## 🎨 **Platform Features**

### **🧠 AI-Powered Analysis**
- **Models**: DeepSeek V3, DeepSeek R1
- **Languages**: Arabic, English, French
- **Specialization**: Diplomatic intelligence, Morocco-focused

### **🇲🇦 Morocco-Specific Intelligence**
- Relevance scoring for Moroccan interests
- Bilateral relations analysis
- Regional impact assessment
- Strategic recommendations

### **🎯 Advanced Operations**
- Threat assessment and monitoring
- Geopolitical forecasting
- Intelligence briefing generation
- Diplomatic entity recognition

### **📊 Professional Monitoring**
- Real-time news monitoring
- Quality scoring
- Source credibility tracking
- Cost monitoring and budgeting

---

## 🔐 **Authentication** (If Required)

Some endpoints may require authentication:
1. Look for the 🔒 lock icon in Swagger UI
2. Click "Authorize" button
3. Enter authentication credentials
4. Test protected endpoints

---

## 📱 **Mobile Access**

The platform is accessible from mobile devices:
- Use the same URLs
- Swagger UI is mobile-responsive
- All features available on mobile

---

## 🆘 **Troubleshooting**

### **If Platform Doesn't Load:**
1. Check if server is running:
   ```bash
   python -c "import requests; print(requests.get('http://localhost:8000/health').json())"
   ```

2. Restart the server:
   ```bash
   python -m uvicorn backend.main:app --host 0.0.0.0 --port 8000 --reload
   ```

### **If APIs Don't Work:**
1. Check the Swagger UI for exact request format
2. Ensure required parameters are provided
3. Check AI budget hasn't been exceeded

### **Common Issues:**
- **Port 8000 busy**: Use different port with `--port 8001`
- **Network access**: Try `http://127.0.0.1:8000` instead
- **AI limits**: Check usage stats endpoint

---

## 🎉 **You're Ready to Go!**

**Start exploring the enhanced DIRAM platform:**
👉 **http://localhost:8000/docs**

The platform is fully operational with 16 enhanced API endpoints ready for diplomatic intelligence analysis! 🚀 
