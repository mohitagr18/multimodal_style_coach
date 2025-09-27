# Multimodal Style Coach 🎨

A sophisticated AI-powered fashion styling system built with Google's Agent Development Kit (ADK) and Gemini models. This project demonstrates advanced multi-agent orchestration, multimodal input processing, and agentic RAG (Retrieval-Augmented Generation) patterns for personalized fashion recommendations.

## 🌟 Overview

The Multimodal Style Coach goes beyond simple item lookups to provide intelligent, personalized fashion recommendations. It leverages specialized AI agents working in concert to understand complex queries, analyze images, infer user demographics, research trends, and assemble complete styled outfits with detailed explanations.

### Key Features

- **Multimodal Input Support**: Processes both text queries and image uploads
- **Gender-Aware Recommendations**: Automatically detects user demographics and provides appropriate styling
- **Real-time Trend Research**: Integrates Google Search for current fashion trends and context
- **Vector Search Integration**: Sophisticated product database queries with multimodal search capabilities
- **Complete Outfit Assembly**: Creates styled looks with detailed reasoning and explanations
- **Professional Report Generation**: Outputs comprehensive, formatted styling reports

## 🏗️ System Architecture

The system uses a **multi-agent architecture** with five specialized AI agents coordinated by a primary StyleCoach agent:

```
StyleCoach Agent (Orchestrator)
├── UserProfile Agent → Demographic analysis
├── InputAnalysis Agent → Image interpretation  
├── TrendResearch Agent → Fashion trend research
├── ItemSearch Tool → Vector database queries
└── StylingReasoning Agent → Outfit assembly
```

### Agent Responsibilities

| Agent | Model | Purpose |
|-------|-------|---------|
| **StyleCoach Agent** | gemini-2.5-flash | Main orchestrator managing workflow |
| **UserProfile Agent** | gemini-2.5-flash | Analyzes queries to infer age group and gender |
| **InputAnalysis Agent** | gemini-2.5-flash | Extracts structured data from fashion item images |
| **TrendResearch Agent** | gemini-2.5-flash | Researches trends using Google Search |
| **ItemSearch Tool** | - | Executes vector searches on product database |
| **StylingReasoning Agent** | gemini-2.5-flash | Assembles outfits with detailed explanations |

## 🚀 Installation & Setup

### Prerequisites

- Python 3.9+
- Access to Google's Agent Development Kit (ADK)

### Dependencies

```bash
# Core dependencies
google-genai>=0.2.0
requests
pathlib
datetime
json
```

### Configuration

1. Set up your search API endpoint:
```python
SEARCH_API_URL = "https://your-vector-search-endpoint.com/api/query"
```

2. Configure authentication for Google AI services according to ADK documentation.

## 📋 Usage

### Basic Text Query

```python
await test_gender_aware_system(query="I need a casual outfit for work")
```

### Image Analysis

```python
await test_gender_aware_system(image_path="./my_jacket.jpg")
```

### Combined Text + Image

```python
await test_gender_aware_system(
    query="What should I wear with this jacket?",
    image_path="./leather_jacket.jpg"
)
```

## 🔧 Core Components

### Vector Search Function

Interfaces with a custom Vector Search REST API for product database queries:

```python
def call_vector_search(url: str, query: str, rows: int = 3) -> dict | None:
    """Calls vector search API with multimodal capabilities"""
```

### Item Search Tool

Processes fashion queries with gender-aware categorization:

```python
def item_search_tool(queries: str) -> str:
    """Finds fashion items and categorizes them by gender"""
```

### Report Generation

Creates formatted styling reports with comprehensive output:

```python
def generate_styling_report(log_display, user_profile_result, final_response_text):
    """Generates professional styling reports with metadata"""
```

## 📊 Workflow Example

For a query like *"What should I wear with this vintage leather jacket for a rock concert?"*:

1. **Profile Analysis**: Determines user demographics (age: adult, gender: male, confidence: high)
2. **Image Analysis**: Extracts jacket details (item: leather jacket, style: vintage bomber, color: dark brown)
3. **Trend Research**: Searches for "rock concert fall fashion" trends
4. **Item Search**: Finds matching items (band t-shirts, distressed denim, boots)
5. **Styling Assembly**: Creates complete outfits with detailed explanations
6. **Report Generation**: Formats professional styling report with timestamps

## 📈 Advanced Features

### Gender-Aware Processing

- **Known Gender**: Generates 5 targeted queries for specific demographic
- **Unknown Gender**: Creates separate male and female recommendations
- **Confidence Levels**: High/medium/low with supporting evidence

### Multimodal Search

- **Dense Search**: Vector similarity matching
- **Sparse Search**: Keyword-based retrieval  
- **Reranking**: AI-powered result optimization
- **Image Analysis**: Visual feature extraction for styling context

### Professional Output

- Structured markdown formatting
- Clickable product image links
- Detailed styling explanations
- Timestamped metadata
- Error handling and fallbacks

## 🎯 Use Cases

- **Personal Styling**: Individual fashion recommendations
- **E-commerce Integration**: Product discovery and styling
- **Fashion Education**: Understanding style principles
- **Trend Analysis**: Market research and forecasting
- **Wardrobe Planning**: Outfit coordination assistance

## 🔍 Technical Details

### Session Management

Uses `InMemorySessionService` for handling concurrent agent sessions and maintaining conversation context.


***

*Built with Google's Agent Development Kit and powered by Gemini models*

