---
name: charm-hyper
description: How to implement AI models from Hyper (by Charm) into any project easily. Make sure to use this skill whenever the user mentions Hyper, Charm, or wants to use Hyper inference in their project using cURL, Python, Node.js, or Go.
---

# Hyper (by Charm) Integration Guide

Hyper is an AI inference solution developed by Charmbracelet. It is specifically designed to support AI coding workflows and provides high-performance, cost-effective inference for open-source models.

When a user asks you to implement Hyper into a project, use the following guidelines to integrate it properly.

## Authentication
To use Hyper, you generally need a `HYPER_API_KEY`. It operates much like an OpenAI-compatible endpoint, making it easy to drop into existing tools and SDKs. Make sure to instruct the user to set their `HYPER_API_KEY` environment variable.

## Integration Methods

Depending on the language or tool the user is working with, read the corresponding reference file to get the correct integration instructions and examples:

| Language / Tool | Reference File |
|---|---|
| cURL | `references/curl.md` |
| Python | `references/python.md` |
| Node.js | `references/nodejs.md` |
| Go | `references/go.md` |

Do not assume the implementation details without reading the relevant reference file first.
