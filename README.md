# MentorConnect

A platform connecting users with experts and mentors from various fields, enabling quick access to help, idea verification, and mentoring in problem-solving. The platform allows users to check their concepts, verify knowledge from various sources, and receive support from experienced practitioners.

## Table of Contents

- [Project Description](#project-description)
- [Tech Stack](#tech-stack)
- [Getting Started Locally](#getting-started-locally)
- [Available Scripts](#available-scripts)
- [Project Scope](#project-scope)
- [Project Status](#project-status)
- [License](#license)

## Project Description

MentorConnect is a universal platform where anyone can find an expert in any field - from legal advice, document review, music mentoring, to web application security. The platform enables users to:

- Quickly find appropriate experts from various fields
- Book mentoring and consultation sessions
- Communicate between users and experts
- Verify ideas before implementation
- Check knowledge acquired from various sources (AI, internet, books, courses)
- Receive mentoring in solving specific problems

### Vision

The platform aims to be a universal place where everyone can find an expert in any field. In the future, the platform will support paid sessions, but in MVP all sessions are free.

## Tech Stack

### Frontend

- **[Astro](https://astro.build/)** v5.13.7 - Modern web framework for building fast, content-focused websites
- **[React](https://react.dev/)** v19.1.1 - UI library for building interactive components
- **[TypeScript](https://www.typescriptlang.org/)** v5 - Type-safe JavaScript
- **[Tailwind CSS](https://tailwindcss.com/)** v4.1.13 - Utility-first CSS framework
- **[Shadcn/ui](https://ui.shadcn.com/)** - Re-usable components built with Radix UI and Tailwind CSS

### Backend

- **Astro SSR** with Node.js adapter - Server-side rendering
- **[Supabase](https://supabase.com/)** - PostgreSQL database and authentication
- **Supabase Auth** - User authentication and authorization

### Deployment

- **[Vercel](https://vercel.com/)** - Platform hosting and deployment

## Getting Started Locally

### Prerequisites

- **Node.js** v22.14.0 (as specified in `.nvmrc`)
- **npm** (comes with Node.js)
- **Supabase account** - For database and authentication setup

### Installation

1. **Clone the repository:**

```bash
git clone https://github.com/JozefImiolo/mentorconnect.git
cd mentorconnect
```

2. **Install dependencies:**

```bash
npm install
```

3. **Set up environment variables:**

Create a `.env` file in the root directory with the following variables:

```env
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_anon_key
```

4. **Run the development server:**

```bash
npm run dev
```

The application will be available at `http://localhost:3000` (as configured in `astro.config.mjs`).

5. **Build for production:**

```bash
npm run build
```

6. **Preview production build:**

```bash
npm run preview
```

## Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start development server with hot-reload |
| `npm run build` | Build the application for production |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint to check for code issues |
| `npm run lint:fix` | Automatically fix ESLint issues |
| `npm run format` | Format code using Prettier |

## Project Scope

### MVP Features (Included)

- Authentication & Account Management
- Expert Profiles
- Category System
- Expert Search & Browse
- Session Booking
- Dashboard

## Project Status

**Status:** MVP in Development

This project is currently in the MVP (Minimum Viable Product) development phase. The focus is on delivering core functionality that enables users to find experts, book sessions, and communicate through contact information.

### Development Progress

- ✅ Project structure and configuration
- ✅ Tech stack setup (Astro, React, TypeScript, Tailwind)
- 🔄 Core features implementation
- ⏳ Testing (Playwright e2e tests planned)
- ⏳ Deployment (Vercel)

## License

MIT

---

## Additional Resources

- [Product Requirements Document (PRD)](.ai/prd.md) - Detailed product specifications
- [MVP Summary](.ai/mvp-summary.md) - Summary of MVP features and scope

## Contributing

Please follow the AI guidelines and coding practices defined in the AI configuration files when contributing to this project. The project includes AI development tools configuration in:

- `.cursor/rules/` - Cursor IDE rules
