# nudge.

**Status:** Architecture / product work, with a small simulated prototype
**When:** February 2026
**Code:** Private for now

## The idea

nudge. is an AI + IoT ecosystem for wellness and placement readiness. The picture in my head is a real-time mentor that sits on your wrist. Your tasks and prep plan live in an app, and when you're drifting, stressed or slipping into bad habits, the smartwatch gives you a haptic nudge at the right moment instead of another notification you'll ignore.

## Intended AI direction

None of this is implemented yet. This is the design I worked out:

- **Contextual sentiment / stress analysis** from how the user is interacting and responding
- **Adaptive tone**: gentler when stress or anxiety looks high, more direct when it doesn't
- **Adaptive scheduling** that learns from how the user has responded to past nudges
- **An LLM API such as Gemini** as the cognitive backend

## What actually exists

A small prototype to test whether the loop makes sense:

- **Web app** (Express + plain HTML/CSS/JS): takes a student's branch, target role and skills and returns a 30-day prep roadmap plus practice questions. The response is **simulated** right now. The Gemini call is marked as an integration point but isn't wired in.
- **Hardware side** (ESP32 + buzzer, simulated in Wokwi): when it gets a trigger over serial (meant for "filler word detected" during interview practice), it fires a short buzz as stand-in haptic feedback.
- A `/api/trigger` endpoint meant to bridge the two. It currently just logs.

## Next

Wire a real LLM into the plan generation, move from a simulated buzzer to actual vibration hardware, and start on the stress/sentiment side of the design.
