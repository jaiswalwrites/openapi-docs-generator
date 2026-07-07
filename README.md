# 📄 OpenAPI → Documentation Generator

[![OpenAPI 3.0](https://img.shields.io/badge/OpenAPI-3.0.3-85ea2d?logo=swagger)](openapi.yaml)
[![Redoc](https://img.shields.io/badge/Docs-Redoc-8b5cf6)](https://redocly.com/redoc/)
[![Portfolio](https://img.shields.io/badge/Portfolio-Manish%20Jaiswal-6366f1)](https://github.com/jaiswalwrites)

A complete **spec-first API documentation** example — demonstrating how to write a production-quality OpenAPI 3.0 specification and generate beautiful interactive docs from it automatically.

Portfolio project by [Manish Jaiswal](https://github.com/jaiswalwrites).

---

## 🔗 Live API Reference

**[View Interactive API Docs →](https://jaiswalwrites.github.io/openapi-docs-generator/docs/)**

---

## 📋 What This Demonstrates

| Skill | Evidence |
|-------|----------|
| **OpenAPI 3.0 Expertise** | Complete spec with schemas, parameters, examples, webhooks |
| **API Documentation** | All CRUD endpoints documented with request/response examples |
| **Error Documentation** | RFC 7807 Problem Details format, all error codes covered |
| **Spec-First Thinking** | API designed and described before implementation |
| **Docs Automation** | One spec file → full interactive reference via Redoc |
| **Writing Quality** | Endpoint descriptions, parameter docs, usage notes |

---

## 📁 Project Structure

```
openapi-docs-generator/
├── openapi.yaml         ← Full OpenAPI 3.0.3 specification (TaskFlow API)
├── docs/
│   └── index.html       ← Redoc-generated interactive API reference
├── style-guide.md       ← API documentation writing style guide
└── README.md            ← This file
```

---

## 📖 The TaskFlow API Spec

The `openapi.yaml` documents a realistic SaaS REST API — **TaskFlow** — a project management platform.

### Coverage

| Resource | Endpoints | Auth |
|----------|-----------|------|
| Authentication | POST /auth/token | Public |
| Tasks | GET, POST /tasks · GET, PATCH, DELETE /tasks/{id} | Bearer |
| Projects | GET, POST /projects | Bearer |
| Users | GET /users/me | Bearer |
| Webhooks | POST /webhooks | Bearer |

### Spec Features

- ✅ **Schemas** — Full type definitions with examples and constraints
- ✅ **Examples** — Request + response examples for every endpoint
- ✅ **Parameters** — Typed, documented query + path parameters
- ✅ **Security** — Bearer token auth defined and applied globally
- ✅ **Errors** — RFC 7807 Problem Details with field-level validation
- ✅ **Webhooks** — Event subscription documentation
- ✅ **Pagination** — Consistent pagination schema across list endpoints
- ✅ **Rate limits** — Documented in the API description

---

## 🚀 View the Docs Locally

**Option 1: Open directly in browser**

```bash
# Open the Redoc-powered API reference
start docs/index.html
```

> Note: Due to browser CORS policies, `openapi.yaml` may not load from `file://`. Use a local server:

**Option 2: Use a local server (recommended)**

```bash
# Python
python -m http.server 8080
# Open http://localhost:8080/docs/

# Node.js (npx)
npx serve .
# Open http://localhost:3000/docs/
```

---

## 🎨 Style Guide

The `style-guide.md` documents the human layer of API documentation — writing standards for endpoint descriptions, parameter documentation, and examples that the OpenAPI spec can't enforce automatically.

---

## 📖 Related Portfolio Projects

| Project | Description |
|---------|-------------|
| **[Docusaurus Docs Site](../docusaurus-portfolio-site/)** | Full documentation site for NeuralDocs |
| **[AI Doc Workflow](../ai-doc-workflow/)** | AI-assisted writing methodology |

---

## 👤 Author

**Manish Jaiswal** — Technical Writer & AI Documentation Specialist  
GitHub: [@jaiswalwrites](https://github.com/jaiswalwrites)
