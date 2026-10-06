# Smart QA Recorder

> A Chrome Extension for capturing browser interactions and generating AI-powered QA test scripts.

Built for the **Certa AI Hackathon** by **Hitesh Chouhan & Lakhan Adewar**.

---

## Features

- 🔴 **Interaction Recording** — Capture clicks, inputs, form fills, and navigations in real-time across page navigations.
- 🤖 **AI Test Script Generation** — Convert recorded steps into natural language automation prompts using your chosen LLM.
- 🔍 **Deep Scan** — AI-driven browser automation that autonomously explores and tests web workflows.
- 🧪 **Faker Data Support** — Generate realistic test data using `@faker-js/faker` for form interactions.
- 🎯 **Smart Locators** — Automatically generates reliable CSS/XPath selectors for each recorded element.
- 🔄 **Multi-LLM Support** — Works with Google Gemini, OpenAI, Anthropic Claude, and OpenRouter.

---

## Supported AI Providers

| Provider | Models | Notes |
|----------|--------|-------|
| **Google Gemini** | `gemini-2.0-flash`, `gemini-1.5-pro` | Recommended |
| **OpenAI** | `gpt-4o`, `gpt-4-turbo`, `gpt-3.5-turbo` | |
| **Anthropic Claude** | `claude-3-5-sonnet`, `claude-3-opus` | |
| **OpenRouter** | Any supported model | Access to multiple providers |

---

## Prerequisites

- **Node.js** v18+ and **pnpm** installed
- **Chrome** (or any Chromium-based browser)
- An API key from your chosen AI provider

---

## Installation

### 1. Clone & Install Dependencies

```shell
git clone https://github.com/hiteshchouhan22/Smart-QA-Recorder.git
cd Smart-QA-Recorder
pnpm install
```

### 2. Build the Extension

```shell
# Production build (output goes to /dist)
pnpm run build

# Development build with file watching
pnpm run dev

# Verbose build with detailed webpack output
pnpm run build:verbose
```

### 3. Load Extension in Chrome

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer mode** (toggle in the top-right corner)
3. Click **Load unpacked**
4. Select the `dist/` folder from this project
5. The **Smart QA Recorder** extension will appear in your toolbar

---

## Configuration

1. Click the **Smart QA Recorder** icon in the Chrome toolbar to open the sidebar
2. Click the ⚙️ **Settings / Options** icon
3. Configure:
   - **AI Provider** — Choose your provider (Google Gemini recommended)
   - **API Key** — Paste your API key
   - **Model** — Select the model to use
4. Click **Save**

### Getting API Keys

- **Google Gemini** → [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
- **OpenAI** → [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- **Anthropic Claude** → [console.anthropic.com](https://console.anthropic.com/)
- **OpenRouter** → [openrouter.ai/keys](https://openrouter.ai/keys)

---

## Usage

### Recording Interactions

1. Open the sidebar by clicking the extension icon
2. Navigate to the page you want to test
3. Click **▶ Start Recording** — the extension begins capturing interactions
4. Perform the actions you want to record (clicks, form inputs, navigations)
5. Click **⏹ Stop Recording** — the extension generates a test script from captured steps

<<<<<<< Updated upstream
- "Open a Website Record Clicks & Action, Then Generate Script for it in (JS,PY,Java)"
- "Navigate to Gmail and compose an email"
- "Fill the Workflow in Certa tenent with URL given to QA Bot"
- "Search Google for Certa and bookmark the result"
=======
### Deep Scan (AI Automation)
>>>>>>> Stashed changes

1. Open the sidebar
2. Enter a natural language task description in the prompt area, e.g.:
   - *"Log in with test credentials and verify the dashboard loads"*
   - *"Fill out the contact form and submit"*
   - *"Navigate to settings and update email preferences"*
3. Click **Run** — Eko AI autonomously completes the workflow and logs each step

---

## Project Structure

```
Smart QA Recorder/
├── src/
│   ├── background/        # Service worker — manages recording state, debugger, LLM calls
│   │   ├── index.ts       # Main background script
│   │   ├── main.ts        # Eko AI agent setup
│   │   └── fakerTool.ts   # Faker.js tool for generating test data
│   ├── content/           # Content scripts injected into web pages
│   │   └── locator-generator.ts  # Smart CSS/XPath locator generation
│   ├── options/           # Extension settings/options UI
│   └── sidebar/           # Main extension sidebar UI (React)
│       └── index.tsx
├── public/
│   ├── manifest.json      # Chrome Extension Manifest V3
│   ├── sidebar.html       # Sidebar entry point
│   └── options.html       # Options page entry point
├── dist/                  # Built extension (load this in Chrome)
├── webpack.js             # Webpack build config
├── tsconfig.json
└── package.json
```

---

## Available Scripts

| Command | Description |
|---------|-------------|
| `pnpm run build` | Production build to `dist/` |
| `pnpm run dev` | Development build with file watching |
| `pnpm run build:verbose` | Build with detailed webpack progress |
| `pnpm run start` | Alias for `pnpm run build` |

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Extension not loading | Ensure `dist/` folder exists (run `pnpm run build`), then reload the extension |
| API errors (401) | Check your API key is correct and has the right permissions |
| Rate limited (429) | Switch AI provider or wait for limits to reset |
| Access denied (403) | Your API key may not have access to the selected model |
| Recording stops on navigation | This is expected — cross-origin navigations may require re-attaching the debugger |

---

## Tech Stack

- **React 18** + **TypeScript** — Sidebar UI
- **Ant Design 5** — UI components
- **Eko AI** (`@eko-ai/eko`) — AI agent orchestration for Deep Scan
- **Faker.js** — Synthetic test data generation
- **Webpack 5** — Extension bundling
- **Chrome Extensions Manifest V3**

---

## Version

Current version: **1.2.0** — see [CHANGELOG.md](./CHANGELOG.md) for release history.

---

## License

MIT License — see [LICENSE](./LICENSE) for details.

**Authors**: Hitesh Chouhan & Lakhan Adewar
