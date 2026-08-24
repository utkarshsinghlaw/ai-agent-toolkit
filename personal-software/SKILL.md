---
name: personal-software
description: Maps personal software requests to 5 shapes (local, web, native, background, hardware), enforces a 4-file context system (project.md, decisions.md, scenarios.md, agent.md), and mandates plain-English toolchain choices. Use this when the user asks to build "personal software", an app for their own household, or tools for non-technical users. Do NOT use for enterprise or public SaaS products.
---

# Personal Software Builder Skill

You must use this skill when building personal software for non-technical or technical users to strictly map specific requirements to the correct tools, and enforce a rigid context-management system.

## 1. Toolchain & Reason Mapping

You must assess the user's "wish" and map it to exactly one of these 5 shapes, using ONLY these specific tools for the listed reasons.

- **Shape 1: Local Tool** (Only runs on one computer)
  - **Tool:** SQLite
  - **Reason:** Simplest possible choice for local data storage on a laptop or Raspberry Pi.
- **Shape 2: Web App** (Default for most personal software)
  - **Tool:** Lovable
  - **Reason:** The absolute quickest route for beginners from description to interface. Use with Lovable Cloud for zero setup, or Supabase if data portability matters.
  - **Tool:** Replit
  - **Reason:** Use when the project needs more than a web interface (Python scripting, scheduled jobs, always-running server).
  - **Tool:** Bolt
  - **Reason:** Another alternative for a quick full-stack web app inside a single environment.
  - **Tool:** Coding Agent (e.g. Antigravity/Claude Code/Codeex) + Vercel + Supabase + GitHub Desktop
  - **Reason:** Use when the user wants more control, separate services for hosting/data, and version control, while keeping the interface portable. (Vercel for preview links/hosting; Supabase for Postgres DB, auth, and row-level security; GitHub for saving working versions).
  - **Tool:** Render
  - **Reason:** Use specifically if building a Python service.
- **Shape 3: Native Phone App** (Requires deep phone features like Bluetooth/Background location)
  - **Tool:** Expo + Supabase + EAS (Expo Application Services)
  - **Reason:** Allows one project to become iOS and Android apps, while EAS handles signing/packaging.
  - **Tool:** Firebase
  - **Reason:** Alternative backend if it's a mobile-first project or heavily relies on Google services.
- **Shape 4: Background Service** (No screen, wakes up on schedule/event)
  - **Tool:** Cron jobs, Replit, or local servers like Raspberry Pi.
  - **Reason:** Reliably processes data from one place to another without requiring user interaction.
- **Shape 5: Hardware Project** (Touches the physical world)
  - **Tool:** Raspberry Pi + SQLite + Tailscale
  - **Reason:** Pi decodes signals; SQLite stores recent data locally; Tailscale allows household devices to see the interface outside the home without exposing the Pi to the public internet.
  - **Tool:** ESP32 / ESP Home
  - **Reason:** Use when reading a single sensor or controlling one device.
  - **Tool:** Home Assistant
  - **Reason:** Use when smart devices already exist in the house and just need one place to connect.

## 2. Context Management System

You must automatically generate the following 4 required markdown files if they do not exist when you start a project. You must maintain these durable text files and never rely on long chat context.

- `project.md`: Who the software is for, current state, desired state, where it runs, and privacy needs.
- `decisions.md`: Log of options, recommendations, and rationale for choices affecting cost, data, access, or portability.
- `scenarios.md`: Real situations the software must handle (e.g., "photograph an appliance and create the record"). Used strictly as test cases.
- `agent.md` (or `claude.md` / `agy.md`): Agent instructions to force plain-English explanations of choices before acting.

## 3. Negative Constraints & Guardrails

- **Plain English Check:** You must not act on major architectural or database choices immediately. You shall stop, provide 2-3 realistic options, recommend one, and explain the trade-offs (cost, portability) in plain English.
- **Secrets Management:** You must never place API keys, passwords, or secrets in code, GitHub, or chat transcripts. You shall use host secret settings (e.g., Vercel secrets).
- **Security Enforcement:** You must enforce authorization at the database level (e.g., Supabase RLS), not just by hiding UI buttons.
- **Testing Verification:** You shall not declare a project "done" or "bug-free" without explicitly testing against the unhappy paths and real-world scenarios defined in `scenarios.md`.
- **Public Exposure:** You must make apps private by default. Make them available on the public internet only when you actually need public access.

## 4. Worked Example

### Input Request
"I want an app to track when the local ferry arrives. The published timetable is unreliable. I have a Raspberry Pi and an antenna to receive AIS radio signals from the ships."

### Target Output & Procedure
1. **Analyze and Map Shape:** "Based on your requirements, this maps to **Shape 5: Hardware Project** because it requires interacting with the physical world and a physical sensor (AIS antenna)."
2. **Select Toolchain:** "I recommend setting up the **Raspberry Pi** to decode the signals, using **SQLite** to store recent vessel positions locally, and **Tailscale** to allow your approved household devices to see the interface outside the home without exposing the Pi to the public internet."
3. **Establish Context:** "I will now generate the 4 required context files (`project.md`, `decisions.md`, `scenarios.md`, `agent.md`) to manage our progress. Shall we proceed with setting up the Raspberry Pi receiver?"