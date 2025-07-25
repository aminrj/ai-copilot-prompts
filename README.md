# AI Copilot Prompts 🤖

> **Production-ready prompts that transform AI copilots from autocomplete into senior developers**

A curated collection of battle-tested prompts for GitHub Copilot, Claude Code, Cursor, and other AI development tools. Turn your AI assistant into an architectural partner, not just a code generator.

[![GitHub stars](https://img.shields.io/github/stars/molntek/ai-copilot-prompts?style=social)](https://github.com/aminrj/ai-copilot-prompts/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🎯 **Why This Exists**

Most developers use AI copilots like autocomplete. This repository contains prompts that unlock their true potential:

- **❌ Typical approach:** "Write a function to calculate tax"
- **✅ This approach:** "Design a tax calculation system for e-commerce that handles multiple jurisdictions, integrates with external APIs, includes comprehensive error handling, and provides audit trails for compliance"

**Result:** Instead of 10 lines of basic code, you get a complete, production-ready system with architecture, security, testing, and documentation.

## 📚 **Prompt Categories**

### 🏗️ [Foundation](./prompts/01-foundation/)

Essential techniques that work with any AI copilot

- [Context Loading](./prompts/01-foundation/context-loading.md) - Set proper context for better results
- [Think Step by Step](./prompts/01-foundation/think-step-by-step.md) - Activate deeper AI reasoning
- [Error-First Development](./prompts/01-foundation/error-first-development.md) - Build robust, production-ready code

### 🐛 [Debugging](./prompts/02-debugging/)

Systematic problem-solving and troubleshooting

- [Systematic Analysis](./prompts/02-debugging/systematic-analysis.md) - Debug any issue methodically
- [Performance Investigation](./prompts/02-debugging/performance-investigation.md) - Find and fix bottlenecks
- [Security Audit](./prompts/02-debugging/security-audit.md) - Identify vulnerabilities

### 🏛️ [Architecture](./prompts/03-architecture/)

System design and high-level planning

- [System Design](./prompts/03-architecture/system-design.md) - Design complete systems from requirements
- [API Design](./prompts/03-architecture/api-design.md) - Create robust, scalable APIs
- [Database Schema](./prompts/03-architecture/database-schema.md) - Design optimal data models

### 🎭 [Advanced Techniques](./prompts/04-advanced/)

Expert-level prompting strategies

- [Time Traveler](./prompts/04-advanced/time-traveler.md) - Future-proof your code
- [Chaos Engineering](./prompts/04-advanced/chaos-engineering.md) - Build resilient systems
- [Legacy Modernization](./prompts/04-advanced/legacy-modernization.md) - Refactor old code safely

### 👥 [Team Workflows](./prompts/05-team/)

Collaboration and team productivity

- [Code Review](./prompts/05-team/code-review.md) - Comprehensive review processes
- [Knowledge Transfer](./prompts/05-team/knowledge-transfer.md) - Document and share expertise
- [Incident Response](./prompts/05-team/incident-response.md) - Handle production issues

## 🚀 **Quick Start**

### Option 1: Copy & Paste (Easiest)

1. Browse the [prompts directory](./prompts/)
2. Find a relevant prompt for your task
3. Copy the template
4. Replace placeholders with your specific context
5. Paste into your AI copilot

### Option 2: VS Code Snippets

1. Install the snippets: Copy [tools/vscode-snippets.json](./tools/vscode-snippets.json) to your VS Code snippets
2. Use shortcuts like `ai-debug` or `ai-arch` to insert prompts
3. Tab through placeholders to customize

### Option 3: CLI Tool (Coming Soon)

```bash
npm install -g @molntek/ai-prompts
ai-prompt search "debug performance"
ai-prompt copy debugging/systematic-analysis
```

## 💡 **Usage Examples**

### Before vs After

**❌ Typical AI Usage:**

```
Human: "Fix this slow query"
AI: [Suggests basic index]
```

**✅ Using Our Prompts:**

```
Human: [Uses systematic-analysis.md template]
"Analyze this database performance issue systematically:

Current situation: Query takes 2.3 seconds, should be under 100ms
Query: SELECT * FROM orders WHERE user_id = ? AND status = 'pending'
Context: E-commerce app, 50k orders/day, MySQL 8.0

Investigate:
1. Query execution plan and bottlenecks
2. Index strategy optimization
3. Schema design improvements
4. Caching opportunities
5. Alternative query approaches
6. Monitoring and alerting setup

Provide specific solutions with implementation steps."

AI: [Provides comprehensive analysis with execution plan review,
     optimal indexing strategy, query rewrite options,
     caching recommendations, and monitoring setup]
```

## 🛠️ **Tool-Specific Configurations**

- **GitHub Copilot:** [Configuration guide](./tools/github-copilot-setup.md)
- **Claude Code:** [Setup instructions](./tools/claude-code-setup.md)
- **Cursor:** [Optimization settings](./tools/cursor-setup.md)
- **VS Code:** [Snippets and extensions](./tools/vscode-snippets.json)

## 📊 **Effectiveness Tracking**

Rate prompts you've used:

- ⭐⭐⭐⭐⭐ **Excellent** - Saved 4+ hours, production-ready output
- ⭐⭐⭐⭐ **Very Good** - Saved 2+ hours, minor tweaks needed
- ⭐⭐⭐ **Good** - Saved 1+ hour, moderate changes required
- ⭐⭐ **Fair** - Some value, significant modifications needed
- ⭐ **Poor** - Minimal value, mostly rewrite required

[Submit your ratings here](https://github.com/molntek/ai-copilot-prompts/issues/new?template=prompt-rating.md)

## 🤝 **Contributing**

We welcome contributions! See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

### Quick Contribution Ideas

- Add prompts for your favorite framework/language
- Submit real-world usage examples
- Improve existing prompt templates
- Add tool-specific optimizations
- Report effectiveness ratings

## 📈 **Success Stories**

> "Using the systematic debugging prompt, I found a memory leak that had been plaguing our production system for months. The AI walked through the investigation step-by-step and identified the exact cause." - _Sarah, Senior Developer_

> "The architecture design prompt helped me plan our microservices migration. Instead of weeks of planning, I had a complete strategy in 2 hours." - _Marcus, Tech Lead_

[Share your success story](https://github.com/molntek/ai-copilot-prompts/issues/new?template=success-story.md)

## 📝 **License**

MIT License - feel free to use these prompts in your commercial projects.

## 🔗 **Related Resources**

- [The Developer's Ultimate AI Copilot Toolkit](https://molntek.com/ai-toolkit) - Complete guide with advanced techniques
- [AI Development Best Practices](https://molntek.com/blog) - Latest insights and updates
- [Community Discord](https://discord.gg/ai-devs) - Discuss prompts and share discoveries

---

**⭐ If these prompts save you time, please star this repository to help others discover it!**

Made with ❤️ by [Molntek](https://molntek.com) | Follow us [@molntek](https://twitter.com/molntek)

---

## 📁 Repository File Structure

```
ai-copilot-prompts/
├── README.md
├── CONTRIBUTING.md
├── LICENSE
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── prompt-request.md
│   │   ├── prompt-rating.md
│   │   └── success-story.md
│   └── workflows/
│       └── validate-prompts.yml
├── prompts/
│   ├── 01-foundation/
│   │   ├── README.md
│   │   ├── context-loading.md
│   │   ├── think-step-by-step.md
│   │   └── error-first-development.md
│   ├── 02-debugging/
│   │   ├── README.md
│   │   ├── systematic-analysis.md
│   │   ├── performance-investigation.md
│   │   └── security-audit.md
│   ├── 03-architecture/
│   │   ├── README.md
│   │   ├── system-design.md
│   │   ├── api-design.md
│   │   └── database-schema.md
│   ├── 04-advanced/
│   │   ├── README.md
│   │   ├── time-traveler.md
│   │   ├── chaos-engineering.md
│   │   └── legacy-modernization.md
│   └── 05-team/
│       ├── README.md
│       ├── code-review.md
│       ├── knowledge-transfer.md
│       └── incident-response.md
├── tools/
│   ├── vscode-snippets.json
│   ├── github-copilot-setup.md
│   ├── claude-code-setup.md
│   └── cursor-setup.md
├── examples/
│   ├── real-world-scenarios/
│   │   ├── e-commerce-payment-system.md
│   │   ├── microservices-migration.md
│   │   └── performance-optimization.md
│   └── before-after-demos/
└── analytics/
    └── usage-stats.md
```
