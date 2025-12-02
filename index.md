
---

---

# CAIRO: The In-App Operator Framework

**By ColomboAI**

CAIRO is the world’s first **In-App Operator** — a framework that turns traditional software, robots, and web platforms into **autonomous, context-aware, goal-driven systems**.

Where most tools stop at “AI assistants” or “agents,” CAIRO brings **Operational Intelligence**: it doesn’t just answer questions, it operates applications, workflows, and interfaces through a unified SDK.

---

## 🌐 What CAIRO Does

- Converts any UI or API into callable tools  
- Builds a global map of your application’s flows  
- Selects the right tools intelligently (without being overwhelmed)  
- Remembers and adapts to context over time  
- Runs composable, testable autonomous workflows (“skills”)  

You can use CAIRO to:

- Automate complex product flows (checkout, onboarding, refunds, form filling)  
- Operate enterprise dashboards, internal tools, and legacy systems  
- Build AI copilots that can *actually take action* inside your app  
- Coordinate multi-step, cross-page operations with full observability  

---

## 🧠 Five Foundational Intelligence Modules

CAIRO’s core capabilities are built on five modules:

1. **Scraping2Tools** – *Convert Any Interface Into Callable Tools*  
2. **SiteMap2Tools** – *Give CAIRO a Global Map of the System*  
3. **MCP-RAG** – *Intelligent Retrieval and Planning Engine*  
4. **Memo AI** – *CAIRO’s Dynamic Memory System*  
5. **Agent Skills** – *Composable, Testable Modules for Autonomous Action*  

### 1. Scraping2Tools

Automatically turns UIs into structured tools:

- No manual integration needed  
- Works with legacy apps, desktop UIs (via scraping), and web interfaces  
- Adapts in real time when the UI changes  

### 2. SiteMap2Tools

Builds a global model of your app:

- Enables multi-page navigation and reasoning  
- Prevents context loss when switching views  
- Supports cross-workflow / cross-section operations  

### 3. MCP-RAG

Acts as the “retrieval + planner” brain:

- Keeps CAIRO from being overwhelmed by thousands of tools  
- Improves reasoning quality and action routing  
- Enables understandable, debuggable execution traces  

### 4. Memo AI

CAIRO’s evolving memory layer:

- Personalizes behavior over time  
- Learns from historical usage and outcomes  
- Supports more explainable decision-making  

### 5. Agent Skills

Reusable, modular workflows:

- Skills are composable units of autonomous behavior  
- Can be tested, versioned, and shared across teams  
- Provide safe, auditable execution pipelines  

---

## 🔐 Security & Compliance

CAIRO is designed for secure and observable operation:

- Policy-based access control  
- Transparent execution logs  
- Role-scoped credentials and API keys  
- Rate limiting, request size limits, HTTPS enforcement, and strict CORS  

---

## 📦 Installation

### Cairo Framework (In-App Operator)

```bash
npm install @colomboai/cairo
Cairo SDK
Production-ready SDK with:

MCP-RAG v2.0

High tool selection accuracy

Sub-20ms latency and multi-tier caching

npm install cairo-sdk
# or
yarn add cairo-sdk
🔑 Getting Your API Key
Go to the ColomboAI Platform

Sign up or log in

Navigate to Developer / API Keys

Generate a new API key for your app

Add it to your environment:

# .env
CAIRO_API_KEY=sk-your-api-key-here
Your API key is required for authentication, usage tracking, and skills-first optimization.

⚡ Quick Start (Minimal Setup)
Only an API key is required — everything else is handled automatically by the SDK.

import { Cairo } from 'cairo-sdk';

// Only API key required - everything else is automatic!
const cairo = new Cairo({
  apiKey: process.env.CAIRO_API_KEY
});

// Start using Cairo SDK
const result = await cairo.ask("Your query here");
console.log(result);
🔧 Core API Methods
CAIRO SDK exposes simple, high-level methods. All backend routing, skills vs MC-1 selection, and caching are automatic.

ask()
Sync-style call with skills-first execution & intelligent routing:

const cairo = new Cairo({ apiKey: process.env.CAIRO_API_KEY });

const result = await cairo.ask("Find and click the submit button");
console.log(result);
askStream()
Streaming responses for chat interfaces, real-time feedback, or long-form generation:

const cairo = new Cairo({ apiKey: process.env.CAIRO_API_KEY });

for await (const chunk of cairo.askStream("Process this form step by step")) {
  console.log(chunk.data);
}
🌐 Framework Examples
Next.js (Recommended)
// app/api/cairo/route.ts
import { Cairo } from 'cairo-sdk';
import { NextRequest } from 'next/server';

const cairo = new Cairo({
  apiKey: process.env.CAIRO_API_KEY
});

export async function POST(request: NextRequest) {
  const { query } = await request.json();
  const result = await cairo.ask(query);
  return Response.json(result);
}
Frontend usage:

const response = await fetch('/api/cairo', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ query: userMessage })
});
const result = await response.json();
Direct Server-Side Usage
import { Cairo } from 'cairo-sdk';

const cairo = new Cairo({
  apiKey: process.env.CAIRO_API_KEY
});

// Use ask() for complete responses
const result = await cairo.ask("Qualify this lead");
console.log(result.content);

// Use askStream() for progressive display
for await (const chunk of cairo.askStream("Generate report")) {
  console.log(chunk.data);
}
Express.js Integration
import express from 'express';
import { Cairo } from 'cairo-sdk';

const app = express();
app.use(express.json());

const cairo = new Cairo({ apiKey: process.env.CAIRO_API_KEY });

app.post('/api/cairo', async (req, res) => {
  const result = await cairo.ask(req.body.query);
  res.json(result);
});

app.listen(3000);
🤖 When to Use ask() vs askStream()
// Use ask() for:
const result = await cairo.ask("Qualify this lead");         // background automation
const descriptions = await Promise.all(                      // batch processing
  properties.map(p => cairo.ask(`Generate description for ${p}`))
);

// Use askStream() for:
for await (const chunk of cairo.askStream(userMessage)) {    // chat interfaces
  displayInChat(chunk.data);
}

for await (const chunk of cairo.askStream("Write detailed report")) { // long-form
  updateProgress(chunk);
}
🧭 How Cairo SDK Routes Requests
The SDK automatically routes each request to Skills or MC-1 based on complexity and confidence.

Your App → Cairo SDK → Intelligent Routing
                              ↓
                         Skills (FREE)
                              ↓
                         MC-1 API (PAID)
Common & recurring queries → FREE skills (cached and fast)

Complex queries → MC-1 advanced LLM

You don’t have to manually choose; the SDK optimizes cost and latency for you

🔐 Authentication
Every request must include an API key as a Bearer token:

Authorization: Bearer YOUR_API_KEY
You can manage keys in the Developer Portal.

📦 Response Format
Standard successful response structure:

{
  "id": "uuid-here",
  "type": "sync",
  "content": "Task completed successfully",
  "media": null,
  "executionPlan": {
    "steps": [
      {
        "toolId": "btn_submit",
        "action": "execute",
        "parameters": { "tool_name": "click_button" }
      }
    ],
    "mode": "sync"
  },
  "actionResults": [
    {
      "id": "action-uuid",
      "status": "success",
      "result": "Executed click_button tool"
    }
  ]
}
❗ Error Handling
Error responses include structured details:

{
  "success": false,
  "error": "Invalid API key",
  "code": "AUTH_ERROR",
  "details": "The provided API key is invalid or expired"
}
Common error codes:

AUTH_ERROR – authentication failed

RATE_LIMIT – too many requests

INVALID_REQUEST – malformed request

TOOL_ERROR – tool execution failed

🧱 Architecture (High-Level)
Request flow:

API request → Bearer token auth

Skills registry search (DB + in-memory)

If skill match (confidence > threshold)

Execute skill (FREE)

Return result

Else, call MC-1 (PAID) and return LLM-backed result

Vector/Tool search uses:

ChromaDB for semantic discovery

PostgreSQL for storage

LRU caching for sub-10ms retrieval

🧰 Skills Registry (Built-In Skills)
CAIRO ships with pre-built workflows:

complete_checkout – e-commerce checkout flows

process_refund – refund handling

navigate_to_section – navigation automation

fill_form_with_data – form automation

You can extend or replace these with your own skills.

✅ Best Practices
Some recommendations for production use:

Use clear, specific queries

Provide context (user/session/env)

Implement retry logic with backoff

Cache tool manifests instead of fetching every time

Monitor usage in the developer portal

Use streaming for long-running tasks

Never expose API keys in client-side code

📈 Performance Benchmarks
Observed metrics:

Query latency: ~16.5 ms (well below 50 ms target)

Tool selection accuracy: ~100% (above 85% target)

Cache hit rate: ~95%+

Memory footprint: <100 MB (under 200 MB budget)

🛠 Troubleshooting
“Invalid API Key”

Verify the key from the platform

Check env loading in your runtime

Ensure no extra quotes/spaces in .env

“Request Timeout”

Check network conditions

Increase timeout:

const cairo = new Cairo({ apiKey: process.env.CAIRO_API_KEY, timeout: 60000 });
Streaming not working

Use for await syntax

Ensure Node.js ≥ 18

Confirm your API route streams properly

📜 License
© 2025 ColomboAI. All rights reserved.

For support, visit the ColomboAI Platform or contact the team via the channels listed there.


---
