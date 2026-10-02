# 🎨 DIRAM Frontend Access Guide

## ✅ Frontend Status
- **Technology**: ASP.NET Blazor Server
- **Language**: C# with Razor components
- **UI Framework**: Bootstrap 5 + Custom CSS
- **Languages Support**: Arabic (RTL) + English

---

## 🚀 **How to Run the Frontend**

### **Prerequisites**
1. **.NET 8.0 SDK** installed
2. **Backend API** running on `http://localhost:8000`

### **Method 1: Using Batch Script (Recommended)**
```bash
# From project root directory
start_frontend.bat
```

### **Method 2: Manual Commands**
```bash
# Navigate to frontend directory
cd frontend

# Restore packages (first time only)
dotnet restore

# Build the project
dotnet build

# Run the application
dotnet run
```

### **Method 3: Visual Studio**
1. Open `frontend/frontend.csproj` in Visual Studio
2. Set as startup project
3. Press F5 or click "Start"

---

## 🌐 **Frontend Access URLs**

### **Main Application**
```
https://localhost:5001
```
- **Primary URL for the Blazor application**
- **Redirects to Dashboard automatically**

### **Alternative URL (HTTP)**
```
http://localhost:5000
```
- **HTTP version (auto-redirects to HTTPS)**

---

## 📱 **Available Pages & Features**

### **1. 🏠 Dashboard** (`/` or `/dashboard`)
- **Arabic Name**: لوحة التحكم الرئيسية
- **Features**:
  - System status overview
  - Recent articles summary
  - Active alerts display
  - Statistics cards
  - Real-time indicators

### **2. 📰 Articles** (`/articles`)
- **Arabic Name**: المقالات
- **Features**:
  - Browse all scraped articles
  - Search and filter articles
  - View article details
  - Morocco relevance scores
  - Analysis status

### **3. 🚨 Alerts** (`/alerts`)
- **Arabic Name**: التنبيهات
- **Features**:
  - Active alerts management
  - Alert configuration
  - Notification settings
  - Priority levels

### **4. 🏛️ Parliamentary Intelligence** (`/parliamentary-intelligence`)
- **Arabic Name**: الذكاء البرلماني
- **Features**:
  - Parliamentary session monitoring
  - Legislative analysis
  - Political trend tracking
  - Morocco-specific parliamentary insights

### **5. 🎯 Intelligence Operations** (`/intelligence`)
- **Arabic Name**: العمليات الاستخباراتية
- **Features**:
  - Threat assessment dashboard
  - Geopolitical analysis
  - Strategic briefings
  - Diplomatic relations tracking

### **6. 🧠 Enhanced Analysis** (`/enhanced-analysis`)
- **Arabic Name**: التحليل المحسن
- **Features**:
  - AI-powered article analysis
  - Morocco relevance scoring
  - Entity detection
  - Intelligence briefing generation

### **7. 👥 Users** (`/users`)
- **Arabic Name**: المستخدمون
- **Features**:
  - User management
  - Role assignment
  - Access control
  - Activity monitoring

### **8. 🔐 Login** (`/login`)
- **Arabic Name**: تسجيل الدخول
- **Features**:
  - JWT-based authentication
  - Role-based access
  - Session management

---

## 🎨 **UI Features**

### **🌍 Bilingual Interface**
- **Arabic (Primary)**: Right-to-left (RTL) layout
- **English (Secondary)**: Left-to-right support
- **Dynamic switching**: Based on content language

### **🎯 Morocco-Focused Design**
- **Morocco flag integration**
- **Cultural color scheme**
- **Professional diplomatic theme**
- **Government-style interface**

### **📱 Responsive Design**
- **Desktop optimized**
- **Tablet compatible**
- **Mobile responsive**
- **Modern UI components**

### **⚡ Real-time Features**
- **Live status indicators**
- **Auto-refreshing data**
- **WebSocket connections**
- **Interactive components**

---

## 🔧 **Configuration**

### **Backend API Connection**
The frontend connects to the backend API at:
```
http://localhost:8000
```

### **Authentication Settings**
JWT authentication configured for:
- **Token validation**
- **Role-based access**
- **Secure API communication**

### **CORS Configuration**
Allows communication between:
- Frontend: `https://localhost:5001`
- Backend: `http://localhost:8000`

---

## 🎮 **How to Use the Frontend**

### **Step 1: Start the Application**
1. Ensure backend is running (`http://localhost:8000`)
2. Run `start_frontend.bat` or `dotnet run` from frontend directory
3. Open browser to `https://localhost:5001`

### **Step 2: Navigate the Interface**
1. **Dashboard**: Overview of system status and recent activity
2. **Articles**: Browse and analyze scraped news articles
3. **Intelligence**: Access advanced analysis features
4. **Alerts**: Monitor and configure threat alerts

### **Step 3: Test Key Features**
1. **View Recent Articles**: Check Morocco relevance scores
2. **Test AI Analysis**: Use enhanced analysis features
3. **Monitor Threats**: Check intelligence operations
4. **Generate Reports**: Create strategic briefings

---

## 🛠️ **Development Features**

### **Hot Reload**
```bash
dotnet watch run
```
- **Automatic reload** on code changes
- **Live updates** without restart

### **Debug Mode**
- **Detailed error messages**
- **Browser dev tools integration**
- **SignalR debugging**

### **Component Structure**
```
frontend/
├── Pages/           # Razor pages
├── Components/      # Reusable components
├── Services/        # API communication
├── Models/          # Data models
├── Shared/          # Layout components
└── wwwroot/         # Static assets
```

---

## 🚨 **Troubleshooting**

### **Frontend Won't Start**
1. **Check .NET SDK**: `dotnet --version` (should be 8.0+)
2. **Restore packages**: `dotnet restore`
3. **Check port availability**: Ensure 5001 is free

### **Can't Connect to Backend**
1. **Verify backend is running**: Check `http://localhost:8000/health`
2. **Check CORS settings**: Ensure frontend URL is allowed
3. **Verify API endpoints**: Test with Swagger UI

### **Authentication Issues**
1. **Check JWT configuration**: Verify shared secrets
2. **Clear browser cache**: Remove stored tokens
3. **Check user roles**: Ensure proper permissions

### **Common Issues**
- **Port 5001 busy**: Change port in `launchSettings.json`
- **SSL certificate**: Accept development certificate
- **Arabic text issues**: Ensure UTF-8 encoding

---

## 📊 **Performance**

### **Optimizations**
- **Server-side rendering** for fast initial load
- **SignalR** for real-time updates
- **Lazy loading** for large datasets
- **Caching** for frequently accessed data

### **Monitoring**
- **Application insights** integration
- **Performance counters**
- **Memory usage tracking**
- **User activity analytics**

---

## 🎉 **You're Ready!**

**Start the DIRAM Frontend:**
1. Run `start_frontend.bat`
2. Open `https://localhost:5001`
3. Explore the bilingual diplomatic intelligence interface!

**Features Available:**
- ✅ **Complete dashboard** with real-time status
- ✅ **Article management** with AI analysis
- ✅ **Intelligence operations** dashboard
- ✅ **Enhanced AI analysis** integration
- ✅ **Bilingual interface** (Arabic/English)
- ✅ **Morocco-focused** design and features

**The enhanced DIRAM frontend is ready for diplomatic intelligence operations! 🚀** 
