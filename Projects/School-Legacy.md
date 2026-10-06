# Project Legacy (School Legacy)

**Status:** Idea / incomplete (frontend explored, backend mostly planned)
**When:** March 2026
**Code:** Private for now

## The idea

A full-stack EdTech platform for a grassroots school. The goal is to bring national-standard digital education to students who don't usually get access to it.

What I'd like it to become:

- Learning infrastructure that can grow subject by subject, starting with Mathematics, Science and English
- Video lectures, PDFs, worksheets and interactive modules in one place
- A UI that feels premium and engaging but stays accessible

## What I've built (frontend)

- **Next.js App Router + TypeScript + Tailwind CSS v4**
- A **cinematic preloader** using Framer Motion
- An interactive **3D book-style Learning Resources module**: subjects (English, Mathematics, Science, Punjabi, Hindi, Computer, History, EVS) laid out as pages you flip, built with `react-pageflip` and CSS transforms
- Reusable, component-driven React structure, e.g. the hero section and resource pages as separate components

## What's planned (backend)

- **Express.js / Node.js** API
- **Prisma** for the data layer

I made an early start here: a Prisma schema on PostgreSQL with `Student`, `Donor` and `Transaction` models, and create/list endpoints for students. Content delivery (videos, PDFs, worksheets), auth and the rest aren't built.

## Next

Decide what the smallest version the school could actually use looks like, probably one subject with real material in it, then build the backend just far enough to serve that.
