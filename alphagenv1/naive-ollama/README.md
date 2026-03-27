# Naive-Ollama Alpha Generator

A sophisticated alpha factor generation system that uses Ollama with financial language models to generate, test, and submit alpha factors to WorldQuant Brain. This system replaces the previous Kimi interface with a local Ollama-based solution for better performance and control.



##  Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Web Dashboard │    │ Alpha Generator │    │  WorldQuant API │
│   (Flask)       │◄──►│   (Ollama)      │◄──►│   (External)    │
│   Port 5000     │    │   Port 11434    │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │              ┌─────────────────┐              │
         └──────────────►│ Alpha Orchestrator │◄─────────────┘
                        │   (Python)      │
                        └─────────────────┘
                                │
                                ▼
                        ┌─────────────────┐
                        │   Results &     │
                        │   Logs Storage  │
                        └─────────────────┘
```


## File Structure

```
naive-ollama/
├── alpha_generator_ollama.py      # Main alpha generation script
├── alpha_orchestrator.py          # Orchestration and scheduling
├── alpha_expression_miner.py      # Alpha expression mining
├── successful_alpha_submitter.py  # Alpha submission to WorldQuant
├── web_dashboard.py               # Flask web dashboard
├── templates/
│   └── dashboard.html             # Dashboard HTML template
├── results/                       # Generated alpha results
├── logs/                          # System logs
├── Dockerfile                     # Docker image definition
├── docker-compose.gpu.yml         # GPU-enabled deployment
├── docker-compose.yml             # CPU-only deployment
├── requirements.txt               # Python dependencies
├── credential.txt                 # WorldQuant credentials
├── start_gpu.bat                  # Windows GPU startup script
├── start_dashboard.bat            # Windows dashboard startup script
└── README_Docker.md               # Detailed Docker documentation
```

##  Workflow

### 1. Alpha Generation
- **Continuous Mode**: Generates alphas every 6 hours
- **Batch Processing**: Generates 3 alphas per batch
- **Ollama Integration**: Uses local LLM for alpha idea generation
- **WorldQuant Testing**: Tests each alpha immediately

### 2. Alpha Mining
- **Expression Mining**: Analyzes promising alphas for variations
- **Pattern Recognition**: Identifies successful alpha patterns
- **Optimization**: Suggests improvements to existing alphas

### 3. Alpha Submission
- **Daily Limit**: Submits only once per day
- **Success Filtering**: Only submits alphas with good performance
- **Rate Limiting**: Respects WorldQuant API limits

##  Monitoring

### Real-time Metrics
- **Alpha Generation Rate**: Alphas generated per hour
- **Success Rate**: Percentage of successful alphas
- **GPU Utilization**: Memory and compute usage
- **API Response Times**: WorldQuant API performance

### Log Analysis
- **Alpha Generator Logs**: Filtered for alpha-related activity
- **System Logs**: Complete system activity
- **Error Tracking**: Failed generations and API calls

