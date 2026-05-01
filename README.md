# Progress Report: AI-Mediated Serious-Game Web App for Improving Habits and Perceptions

**Selected Reference Paper for Conceptual Grounding:**  
*CoEmpaTeam: Enhancing Cognitive Empathy using LLM-based Avatars and Dynamic Role Play in Virtual Reality* (CHI 2026)

## 1. Conceptual Grounding: Why We Referenced This Paper

Project 1 aims to build an **AI-mediated web serious game** that helps users rehearse self-regulation and socially constructive choices in everyday scenarios, specifically targeting doomscrolling, impulsive spending, stereotyping, and hostile cross-group conversations.

*CoEmpaTeam* offers one of the cleanest recent examples of using **LLM-driven multi-character role-play** to train cognitive empathy. Its core design insight is simple but powerful: give each AI character a distinct personality profile (Big Five traits, lifestyle log, hidden motivation) and let users practice perspective-taking through natural dialogue.

We found this idea highly relevant to Project 1’s goals of “adaptive role-play” and “cooperative dialogue,” but we did **not** adopt its VR setting, house-rule scenario, or backend implementation. Instead, we took the **broad concept** of personality-grounded AI friends as training partners and built an original web prototype for habit formation and intergroup understanding.

## 2. What We Built: A Fully Original Web Demo

We designed and implemented from scratch a **single-page browser application** (HTML/CSS/JavaScript) that functions as an interactive behavior-practice chat game. The demo requires no backend server and runs entirely in the user’s browser.

<div style="break-after: page;"></div>

### 2.1 Core Mechanics

The game presents social scenarios where **the AI plays two friends** exhibiting problematic behaviors. The human user joins the conversation and attempts to guide the friends toward more reflective, empathetic choices through natural language.

After each user message, **two independent AI operations** run in parallel:

1. **Behavioral Scoring Engine:** Evaluates the user’s latest message on three dimensions - non-impulsive response, calm analysis, and perspective-taking - and returns a structured score with actionable feedback.

2. **Adaptive Roleplay Response:** Generates the next friend reply. Critically, the AI friends’ tone and defensiveness **adapt in real time** based on whether the user is lecturing or genuinely attempting perspective-taking. This creates a closed-loop training dynamic in which users learn through social consequences, not abstract instruction.

Both engines are driven by **original system prompts** we authored specifically for this project, and all LLM calls go directly to the DeepSeek API from the browser.

---

### 2.2 Scenario Design: Directly Targeting Project 1’s Behavioral Goals

We designed two levels, each mapping to a core Project 1 intervention target:

| Level | Theme | Target Behaviors | Primary Training Focus |
|-------|-------|------------------|------------------------|
| 1 | Clickbait & Impulsive Spending | Doomscrolling, impulsive consumption | Non-impulsive response, delayed decision-making |
| 2 | Intergroup Bias & Polarized Talk | Stereotyping, hostile cross-group rhetoric | Perspective-taking, fact-based dialogue |

Each scenario features two AI friends with **distinct, psychologically motivated personality traits** — e.g., one who habitually shares sensational headlines, another who uses labels for out-groups. The opening dialogue sets up a realistic social tension that the user must navigate.

<div style="break-after: page;"></div>

### 2.3 Key Technical Features

- **Zero backend / zero deployment:** All logic is implemented in `index.html`, `index.css`, and `index.js`. LLM calls are sent directly from the browser via `fetch` to `api.deepseek.com`.
- **Privacy-aware API key management:** Users provide their own DeepSeek key, stored in browser `localStorage`, with explicit warnings against use on shared or public devices.
- **Multi-language support:** Full UI and prompt localization in Chinese, English, and Japanese.
- **Robust input handling:** A diagnostic function detects empty, aggressive, gibberish, and prompt-injection inputs and adjusts the AI’s response behavior accordingly.
- **Dynamic round management:** A level can end early if both friends are persuaded, or continue until a configurable maximum round count.

## 3. How This Demo Serves Project 1

| Project 1 Requirement | Our Implementation |
|-----------------------|--------------------|
| Short narrative quests | Level-based scenarios with escalating difficulty |
| Reflective dialogues | AI-generated score explanations and level-end summaries |
| Personalized feedback | Per-message, three-dimensional behavioral scoring |
| Adaptive role-play | Friend AI adjusts defensiveness based on user’s detected behavior pattern |
| Low-stakes rehearsal | Safe, private environment to fail and retry |
| Doomscrolling / stereotyping intervention | Level themes directly address these exact behaviors |
| Safeguards against unintended AI influence | System prompt strictly prohibits the AI from generating coaching meta-text or breaking character |

<div style="break-after: page;"></div>

## 4. Planned Extensions

1. **Longitudinal Progress Tracking:** A `localStorage`-based journal that stores scores and user-written reflections across sessions, with a visual dashboard.
2. **Adaptive Difficulty:** Auto-adjust scenario intensity and friend stubbornness based on cumulative performance.
3. **Transparency Dashboard:** “Why this score?” explainer panels and full user control over stored data.
4. **Expanded Scenario Library:** Additional levels covering impulse spending, misinformation sharing, and hostile intergroup dialogue.
5. **Offline Behavior Prompts:** Concrete “real-life missions” after each level with optional next-day check-ins.
6. **Progressive Web App Packaging:** Offline access and mobile installation for device-agnostic deployment.

## 5. Conclusion

We have built a fully functional, browser-based behavior-practice game that targets the core intervention goals of Project 1. While our design draws **conceptual inspiration** from *CoEmpaTeam*’s personality-grounded multi-character role-play approach, all code, system prompts, scenario designs, and scoring mechanisms are our **original work**, developed specifically for habit formation and intergroup understanding.

The prototype is self-contained, requires no server infrastructure, and demonstrates adaptive role-play, real-time behavioral scoring, and multi-scenario training in three languages. It is intended as a research and educational demo, not a clinical intervention tool.

**Demo / Code:** *https://github.com/roeyqian/WithAIChat*

Siyu Qian
*Email: Siyu.Qian24@student.xjtlu.edu.cn*