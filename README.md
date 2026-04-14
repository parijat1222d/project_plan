**ApiMesh – Live API & Microservices Contract Visualizer**  


### 1. Executive Summary
**ApiMesh** is a pure **non-AI**, real-time, interactive API & microservices architecture visualizer built as a VS Code extension.  

It scans your backend codebase (Express, NestJS, FastAPI, Spring Boot, Go, etc.) and instantly builds a **live interactive map** showing:  
- All endpoints (REST / GraphQL / gRPC)  
- Service → Endpoint → Database → External service relationships  
- Impact radius of any change  
- Contract violations and architecture drift  

**Market Gap**: No single extension today provides this complete, multi-framework, backend-focused API landscape view with impact analysis. Existing tools are either framework-specific (Express only), file-level dependency graphs, or runtime dashboards.  

**Project Value**:  
- Solves daily pain for backend/microservices teams (onboarding, refactoring, migration).  
- 100% local, zero cloud dependency, rule-based & fast.  
- Final-year project scope: 4.5–6 months, strong research + implementation.  
- High market potential: 8k–20k+ installs in first 6–8 months.  

### 2. Project Overview & Problem Statement
Backend developers working on monoliths or microservices spend 30–40% of their time manually tracking:  
- Where each API endpoint lives  
- Which services/databases it touches  
- What will break if they change one route  

Current tools force you to jump between files, run the app, or use external diagramming tools. **ApiMesh** eliminates this by giving you a **live, clickable, always-up-to-date architecture map** directly inside VS Code.

**Target Users**:  
- Backend engineers (Node, Python, Java)  
- Microservices / monolith migration teams  
- Enterprise & Indian IT product companies  
- Open-source maintainers of large APIs  

### 3. Core Features (All Non-AI, Pure Local Computation)
1. **Real-time API Endpoint Graph**  
   - Auto-detects routes from controllers/routers/decorators.  
   - Visual nodes: Service → Endpoint → Method → Path.  
   - Edges: DB tables, external APIs, middleware, auth.

2. **Interactive Dependency Map** (Cytoscape.js / React Flow)  
   - Zoom, pan, filter, search, color-coded layers.  
   - Click any node → jump directly to code definition.

3. **Change Impact Analyzer** (Unique Selling Point)  
   - “If I modify this endpoint, how many files, routes, tests, and DB queries will be affected?”  
   - Real-time blast radius + risk score (static analysis + call-graph traversal).

4. **Contract & Health Checker**  
   - Duplicate routes  
   - Missing auth / OpenAPI tags  
   - Broken internal references  
   - Architecture drift detection (layer violations).

5. **One-Click OpenAPI / Swagger Generation**  
   - Static analysis → full OpenAPI 3.1 YAML/JSON from code.

6. **Export & Collaboration**  
   - Interactive HTML report  
   - PNG / Mermaid / Draw.io export  
   - Pre-commit hook support.

7. **Framework Support (Phase-wise)**  
   - Phase 1: Node.js (Express + NestJS)  
   - Phase 2: Python (FastAPI + Flask/Django)  
   - Phase 3: Java (Spring Boot) + Go (Gin/Fiber)

### 4. Technical Architecture & Implementation Details
**Language**: TypeScript (recommended for VS Code extensions)  
**Core Technologies**:
- VS Code Extension API + Webview (React + Vite + Tailwind + Shadcn UI)
- **Tree-sitter** (multi-language AST parsing – most critical part)
- Custom route parsers (for @Get, app.get, @Controller, etc.)
- Incremental graph engine (for real-time updates without full re-scan)
- Cytoscape.js or React Flow for visualization
- chokidar (file watcher)
- VS Code Git API (for change tracking)

**Performance Targets**:
- < 800ms full scan on 50k LOC project
- Real-time incremental updates on file save

**Privacy & Performance**:
- 100% local (no internet, no telemetry by default)
- Works offline
- Handles large monorepos

**Folder Structure (High-level)**:
```
/src
  ├── extension.ts
  ├── parsers/          # Tree-sitter + framework-specific parsers
  ├── graph/            # Graph engine + impact analysis
  ├── webview/          # React dashboard + Cytoscape
  ├── commands/         # VS Code commands
  ├── utils/            # File watcher, OpenAPI generator
  └── types/
```

**Extension Size Goal**: < 5 MB (lightweight).

### 5. Market Competitors Analysis (April 2026 Data)
I checked the VS Code Marketplace and recent web results. Here is the current landscape:

| Extension                        | Installs     | Strengths                          | Major Limitations                                      | Score (out of 10) |
|----------------------------------|--------------|------------------------------------|--------------------------------------------------------|-------------------|
| Express Routes Viewer            | ~362        | Express tree + basic graph         | Express-only, no impact analysis, no DB mapping        | 4/10             |
| FastAPI Extension (official)     | ~8,139      | Nice route tree explorer           | FastAPI-only, tree view only, no graph or impact       | 5/10             |
| Framework Routes Dashboard       | Low         | NestJS + FastAPI dashboard         | Limited frameworks, no impact or full mapping          | 5/10             |
| DepViz                           | ~2,080      | Function call graphs + impact slice| General code-level, not API/contract focused           | 6/10             |
| CodeGraphy                       | ~8,318      | File dependency force graph        | File-level only, no API endpoints or DB relations      | 5/10             |
| Spring Boot Dashboard            | Popular     | Running app management             | Runtime only, not static analysis                      | 4/10             |

**Other mentions**: CodeVisualizer, Vxplain, CodeAtlas-Live – mostly general codebase maps or AI-assisted, not backend-API specific.

**Key Observation**: No extension combines **multi-framework API detection + service/DB mapping + real-time impact analysis** in one polished tool.

### 6. How ApiMesh Beats Existing Products
| Feature                              | ApiMesh                  | Competitors                          | Advantage |
|--------------------------------------|--------------------------|--------------------------------------|---------|
| Multi-framework support              | Express + Nest + FastAPI + Spring + Go | Framework-specific (1–2 only)       | Huge |
| Endpoint → Service → DB → External mapping | Full interactive graph  | Missing or partial                   | Core differentiator |
| Real-time Change Impact Analysis     | Yes (blast radius)       | Rare / very basic                    | Game changer for refactoring |
| Contract violation + drift detection | Built-in                 | Almost none                          | Enterprise-ready |
| Static OpenAPI generation            | One-click                | Manual or runtime only               | Developer productivity |
| Pure local + zero AI dependency      | Yes                      | Some use LLM                         | Privacy + speed + reliability |

**Result**: ApiMesh is the **first dedicated backend architect’s tool** inside VS Code. It turns “I need to understand this API landscape” from a 2-hour manual task into a 10-second visual experience.

### 7. Development Roadmap (5 Months Realistic)
- **Month 1–2**: Core parsers (Node + Python) + basic graph  
- **Month 3**: Webview dashboard + impact analysis engine  
- **Month 4**: Java/Spring + polish + contract checker  
- **Month 5**: Testing, documentation, demo video, Marketplace publish  

**Weekly effort**: 15–20 hours (perfect for final-year student).

**Cost**: ₹0 – ₹1,500 maximum (optional logo/domain).

### 8. Market Impact & Future Potential
- **Short-term**: 8k–20k installs in 6–8 months (backend community is very active).  
- **Monetization**: Free core + Premium (team rules sync, CI integration, advanced reports).  
- **Enterprise appeal**: Indian IT companies + fintech + product teams will love it.  
- **Research angle**: “Static Multi-Framework API Architecture Visualization Using Tree-sitter” – excellent for thesis/paper.

