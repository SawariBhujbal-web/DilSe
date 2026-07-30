DilSe — Your AI Companion for Mental Well-being

"Dil Se" — Straight From the Heart

DilSe is a single-page web app that provides a warm, compassionate chat interface for emotional support and mindful guidance. The conversational AI is powered by IBM watsonx Orchestrate, embedded directly into the page via the watsonx Orchestrate web chat widget.

✨ Features
Compassionate Listening — an empathetic AI agent for emotional support conversations
Relationship & Communication Guidance — tips for navigating personal relationships
Mindfulness & Stress Relief — practical, calming techniques
Motivational Conversations — encouragement and positivity
Personal Growth & Reflection — prompts for self-development
Cultural & Heartfelt Storytelling — culturally resonant, story-driven responses
Quick Prompts — one-tap conversation starters (e.g. "I'm feeling overwhelmed today", "Help me stay motivated")
Always-On Availability — designed for 24/7 access
🖥️ Tech Stack
Layer	Details
Markup/Styling	Plain HTML5 + CSS (no build step, no framework)
Fonts	Fraunces (display/headings), Inter (body) — loaded via Google Fonts
Conversational AI	IBM watsonx Orchestrate Web Chat widget
Layout	CSS Grid (sidebar + chat panel), responsive down to mobile
📁 Project Structure
.
└── index.html   # Entire application: markup, styles, and watsonx Orchestrate embed

This project is intentionally a single self-contained HTML file — no build tools, package manager, or server-side code required.

🚀 Getting Started
Clone or download this repository.
Open index.html directly in a browser, or serve it with any static file server:
bash
   npx serve .
   # or
   python3 -m http.server 8000
The watsonx Orchestrate chat widget will load asynchronously into the #root element inside the chat panel.

No local dependencies to install — the watsonx Orchestrate loader script is fetched from IBM Cloud at runtime.

⚙️ Configuration

The chat agent is configured at the bottom of index.html via window.wxOConfiguration:

js
window.wxOConfiguration = {
  orchestrationID: "<your-orchestration-id>",
  hostURL: "<your-watsonx-orchestrate-host-url>",
  rootElementID: "root",
  deploymentPlatform: "ibmcloud",
  crn: "<your-instance-crn>",
  chatOptions: {
    agentId: "<your-agent-id>"
  }
};

To point this app at your own watsonx Orchestrate instance and agent, replace the following values with the ones from your IBM Cloud project:

Field	Description
orchestrationID	Your watsonx Orchestrate orchestration/environment ID
hostURL	The regional host URL for your watsonx Orchestrate instance
crn	The Cloud Resource Name (CRN) of your watsonx Orchestrate service instance
chatOptions.agentId	The ID of the specific agent you want the widget to load

The widget script itself (wxoLoader.js) is loaded dynamically at runtime from hostURL, so no local SDK installation is needed.

🎨 Customization

All visual styling is driven by CSS custom properties defined in :root, making it easy to re-theme:

css
:root {
  --ivory: #faf6f2;
  --rose: #b3543f;
  --rose-deep: #96402e;
  --plum: #5c4356;
  --peach: #e2a06f;
  --sage: #7a9b76;
  /* ...etc */
}

Other easy customization points:

Quick prompt chips — edit the .chip elements inside .quick-prompts
Sidebar feature list — edit the <ul class="feature-list"> items
Wellness meter values — adjust the width percentages on .bar-fill elements
Quote card — swap the text/author inside .quote-card
⚠️ Disclaimer

DilSe is an AI companion intended for supportive, everyday conversation — it is not a substitute for professional mental health care. If you or someone you know is in crisis or experiencing a mental health emergency, please contact a qualified mental health professional or local emergency/crisis services immediately.
