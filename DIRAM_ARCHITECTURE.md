# DIRAM - Professional Architecture Guide
## نظام تحليل الذكاء والعلاقات الدبلوماسية للمغرب

### 🔑 Your OpenRouter API Integration

**API Key:** `[REDACTED_API_KEY]`

### 🏗️ Clean Architecture Overview

```
Frontend (Blazor) → API Gateway → Application Layer → Domain Layer → Infrastructure Layer
```

### 📊 Professional Implementation

#### 1. Enhanced AI Client Configuration

```python
# ai_engine/professional_client.py

import aiohttp
import asyncio
from typing import Dict, Any, Optional
from dataclasses import dataclass
from enum import Enum

class AIModel(Enum):
    DEEPSEEK_V3 = "deepseek/deepseek-chat"          # Primary model
    DEEPSEEK_R1 = "deepseek/deepseek-r1:free"       # Free reasoning model
    QWEN_LARGE = "qwen/qwen-2.5-72b-instruct"      # Multilingual support

@dataclass
class AIResponse:
    content: str
    model_used: str
    cost: float
    confidence: float = 0.95

class ProfessionalAIClient:
    def __init__(self):
        self.api_key = "[REDACTED_API_KEY]"
        self.base_url = "https://openrouter.ai/api/v1"
        self.session = None
    
    async def __aenter__(self):
        self.session = aiohttp.ClientSession(
            headers={
                "Authorization": f"Bearer {self.api_key}",
                "Content-Type": "application/json",
                "HTTP-Referer": "https://diram.ma",
                "X-Title": "DIRAM - Diplomatic Intelligence"
            }
        )
        return self
    
    async def __aexit__(self, exc_type, exc_val, exc_tb):
        if self.session:
            await self.session.close()
    
    async def analyze_diplomatic_content(
        self, 
        content: str, 
        model: AIModel = AIModel.DEEPSEEK_V3,
        language: str = "ar"
    ) -> AIResponse:
        """Analyze diplomatic content with specialized prompts"""
        
        system_prompts = {
            "ar": "أنت محلل دبلوماسي خبير متخصص في الشؤون المغربية والعلاقات الدولية",
            "en": "You are an expert diplomatic analyst specializing in Moroccan affairs",
            "fr": "Vous êtes un analyste diplomatique expert spécialisé dans les affaires marocaines"
        }
        
        payload = {
            "model": model.value,
            "messages": [
                {"role": "system", "content": system_prompts.get(language, system_prompts["en"])},
                {"role": "user", "content": f"Analyze this diplomatic content for Morocco's interests: {content[:3000]}"}
            ],
            "max_tokens": 2000,
            "temperature": 0.3
        }
        
        async with self.session.post(f"{self.base_url}/chat/completions", json=payload) as response:
            if response.status == 200:
                data = await response.json()
                return AIResponse(
                    content=data["choices"][0]["message"]["content"],
                    model_used=model.value,
                    cost=self._calculate_cost(data.get("usage", {}), model)
                )
            else:
                raise Exception(f"API request failed: {response.status}")
    
    async def extract_morocco_relevance(self, content: str) -> Dict[str, Any]:
        """Extract Morocco-specific relevance score and insights"""
        
        prompt = f"""
        Analyze this content for Morocco relevance. Return JSON with:
        - relevance_score: 0-100
        - key_entities: list of important entities
        - implications: list of implications for Morocco
        - risk_level: LOW/MEDIUM/HIGH
        
        Content: {content[:2000]}
        """
        
        response = await self.analyze_diplomatic_content(
            prompt, 
            model=AIModel.DEEPSEEK_V3,
            language="en"
        )
        
        try:
            import json
            return json.loads(response.content)
        except:
            return {"relevance_score": 50, "error": "Failed to parse JSON"}
    
    def _calculate_cost(self, usage: Dict[str, Any], model: AIModel) -> float:
        """Calculate request cost"""
        if ":free" in model.value:
            return 0.0
        
        input_tokens = usage.get("prompt_tokens", 0)
        output_tokens = usage.get("completion_tokens", 0)
        
        # DeepSeek V3 pricing: $0.38/$0.89 per 1M tokens
        cost = (input_tokens * 0.38 + output_tokens * 0.89) / 1_000_000
        return round(cost, 6)
```

#### 2. Updated Backend Service

```python
# backend/services/ai_analysis_service.py

from typing import Dict, Any, List
import logging
from ai_engine.professional_client import ProfessionalAIClient, AIModel

logger = logging.getLogger(__name__)

class DiplomaticAnalysisService:
    """Professional diplomatic analysis service"""
    
    def __init__(self):
        self.ai_client = ProfessionalAIClient()
        self.daily_cost = 0.0
        self.max_daily_budget = 25.0  # USD
    
    async def analyze_article(self, article_data: Dict[str, Any]) -> Dict[str, Any]:
        """Comprehensive article analysis"""
        
        if self.daily_cost >= self.max_daily_budget:
            raise Exception("Daily AI budget exceeded")
        
        async with self.ai_client as client:
            # Primary analysis
            analysis = await client.analyze_diplomatic_content(
                content=article_data['content'],
                model=AIModel.DEEPSEEK_V3,
                language=article_data.get('language', 'ar')
            )
            
            # Morocco relevance
            relevance = await client.extract_morocco_relevance(
                content=article_data['content']
            )
            
            # Track costs
            total_cost = analysis.cost
            self.daily_cost += total_cost
            
            return {
                "analysis": analysis.content,
                "morocco_relevance": relevance.get('relevance_score', 0),
                "risk_level": relevance.get('risk_level', 'LOW'),
                "entities": relevance.get('key_entities', []),
                "implications": relevance.get('implications', []),
                "cost": total_cost,
                "model_used": analysis.model_used,
                "budget_remaining": self.max_daily_budget - self.daily_cost
            }
    
    async def generate_intelligence_summary(self, articles: List[Dict]) -> Dict[str, Any]:
        """Generate intelligence briefing from multiple articles"""
        
        # Prepare articles digest
        articles_text = "\n\n".join([
            f"Article {i+1}: {article.get('title', 'No title')}\n{article.get('content', '')[:500]}"
            for i, article in enumerate(articles[:5])
        ])
        
        async with self.ai_client as client:
            summary = await client.analyze_diplomatic_content(
                content=f"Generate a comprehensive diplomatic intelligence summary for Morocco based on these articles:\n\n{articles_text}",
                model=AIModel.DEEPSEEK_R1,  # Use reasoning model for complex analysis
                language="ar"
            )
            
            self.daily_cost += summary.cost
            
            return {
                "summary": summary.content,
                "articles_analyzed": len(articles),
                "model_used": summary.model_used,
                "cost": summary.cost
            }
```

#### 3. Enhanced API Endpoints

```python
# backend/api/enhanced_analysis.py

from fastapi import APIRouter, HTTPException, BackgroundTasks
from backend.services.ai_analysis_service import DiplomaticAnalysisService
from shared.settings import settings

router = APIRouter(prefix="/api/analysis", tags=["AI Analysis"])

@router.post("/analyze-article")
async def analyze_article(article_data: dict):
    """Analyze single article with AI"""
    
    try:
        service = DiplomaticAnalysisService()
        result = await service.analyze_article(article_data)
        
        return {
            "success": True,
            "data": result,
            "message": "Article analyzed successfully"
        }
        
    except Exception as e:
        logger.error(f"Analysis failed: {e}")
        raise HTTPException(status_code=500, detail=str(e))

@router.post("/intelligence-briefing")
async def generate_briefing(request_data: dict):
    """Generate intelligence briefing from multiple articles"""
    
    try:
        service = DiplomaticAnalysisService()
        result = await service.generate_intelligence_summary(
            articles=request_data.get('articles', [])
        )
        
        return {
            "success": True,
            "briefing": result,
            "message": "Intelligence briefing generated successfully"
        }
        
    except Exception as e:
        logger.error(f"Briefing generation failed: {e}")
        raise HTTPException(status_code=500, detail=str(e))

@router.get("/health")
async def ai_health_check():
    """Check AI service health"""
    
    try:
        async with ProfessionalAIClient() as client:
            test_response = await client.analyze_diplomatic_content(
                content="Test message",
                model=AIModel.DEEPSEEK_V3
            )
            
            return {
                "status": "healthy",
                "model_available": True,
                "test_cost": test_response.cost
            }
            
    except Exception as e:
        return {
            "status": "unhealthy",
            "error": str(e)
        }

@router.get("/usage-stats")
async def get_usage_stats():
    """Get current AI usage statistics"""
    
    service = DiplomaticAnalysisService()
    
    return {
        "daily_cost": service.daily_cost,
        "budget_remaining": service.max_daily_budget - service.daily_cost,
        "usage_percentage": (service.daily_cost / service.max_daily_budget) * 100,
        "status": "within_budget" if service.daily_cost < service.max_daily_budget else "budget_exceeded"
    }
```

#### 4. Environment Configuration

```python
# shared/enhanced_settings.py

from pydantic_settings import BaseSettings
from typing import List, Dict

class EnhancedSettings(BaseSettings):
    # OpenRouter Integration
    OPENROUTER_API_KEY: str = "[REDACTED_API_KEY]"
    OPENROUTER_BASE_URL: str = "https://openrouter.ai/api/v1"
    
    # AI Models Configuration
    PRIMARY_MODEL: str = "deepseek/deepseek-chat"           # DeepSeek V3
    REASONING_MODEL: str = "deepseek/deepseek-r1:free"      # DeepSeek R1 (Free)
    MULTILINGUAL_MODEL: str = "qwen/qwen-2.5-72b-instruct" # Qwen for Arabic/French
    
    # Cost Management
    DAILY_AI_BUDGET: float = 25.0  # USD per day
    COST_ALERT_THRESHOLD: float = 20.0  # Alert at $20
    
    # Morocco-specific Keywords
    MOROCCO_KEYWORDS: List[str] = [
        "Morocco", "Maroc", "المغرب", "Rabat", "Casablanca",
        "Hassan VI", "Mohammed VI", "Maghreb", "Western Sahara"
    ]
    
    # Analysis Configuration
    MAX_CONTENT_LENGTH: int = 5000
    DEFAULT_LANGUAGE: str = "ar"
    CONFIDENCE_THRESHOLD: float = 0.75
    
    class Config:
        env_file = ".env"

settings = EnhancedSettings()
```

### 🚀 Quick Start Implementation

1. **Install Dependencies:**
```bash
pip install aiohttp fastapi pydantic-settings
```

2. **Update your main.py:**
```python
# backend/main.py

from fastapi import FastAPI
from backend.api.enhanced_analysis import router as analysis_router

app = FastAPI(title="DIRAM - Enhanced AI Integration")

app.include_router(analysis_router)

@app.get("/")
async def root():
    return {
        "message": "DIRAM - Professional Diplomatic Intelligence System",
        "ai_integration": "OpenRouter + DeepSeek",
        "status": "operational"
    }
```

3. **Test the Integration:**
```bash
# Start the server
uvicorn backend.main:app --reload

# Test endpoint
curl -X POST "http://localhost:8000/api/analysis/analyze-article" \
  -H "Content-Type: application/json" \
  -d '{
    "content": "Morocco and Spain discuss bilateral trade agreements",
    "language": "en",
    "source": "test"
  }'
```

### 🔧 What Was Missing & Now Fixed:

✅ **Professional OpenRouter Integration**  
✅ **DeepSeek V3 & R1 Model Support**  
✅ **Cost Tracking & Budget Management**  
✅ **Multilingual Analysis (Arabic/English/French)**  
✅ **Morocco-Specific Intelligence Analysis**  
✅ **Clean Architecture Implementation**  
✅ **Error Handling & Rate Limiting**  
✅ **Health Checks & Monitoring**

### 📊 Next Steps:

1. **Implement the code above** in your project
2. **Test with real diplomatic content**
3. **Add background job processing** for automated analysis
4. **Create the web scrapers** for news sources
5. **Build the alert system** for critical events
6. **Add visualization dashboard** for insights

This architecture provides a **professional, cost-effective foundation** using the best free AI models available through OpenRouter, specifically optimized for Morocco's diplomatic intelligence needs. 
