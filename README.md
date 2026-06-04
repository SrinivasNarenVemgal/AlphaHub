# 🔥 AlphaHub
> **Community Discussion Platform — Built by Alphabuilders HQ**

<div align="center">

![AlphaHub](https://img.shields.io/badge/AlphaHub-Live-ff4800?style=for-the-badge&logo=firefoxbrowser&logoColor=white)
![Built With](https://img.shields.io/badge/Built%20With-Vibe%20Coding-ff4800?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Shipped%20✓-3dd68c?style=for-the-badge)
![Made By](https://img.shields.io/badge/Made%20By-Alphabuilders%20HQ-ff8c00?style=for-the-badge)

### 🌐 [View Live Demo →](https://srinivasnarenvemgal.github.io/AlphaHub/)

*A Reddit-style community platform — real, live, working. Not a tutorial. Not a clone. A product.*

</div>

---

## 📖 What is AlphaHub?

**AlphaHub** is a full-featured community discussion platform inspired by Reddit — built entirely from scratch as a real portfolio project under **Alphabuilders HQ**.

Users can create communities, post content (text, images, links), vote on posts, comment, and manage their own profiles — all inside a beautifully designed dark UI with a custom SVG logo and premium typography.

This project was built using **Vibe Coding** — using AI as an accelerator, not a replacement. Every feature was planned, every design decision was made, and every bug was debugged by me.

---

## 🚀 Live Demo

| | Link |
|---|---|
| 🌐 **Live Site** | https://srinivasnarenvemgal.github.io/AlphaHub/ |
| 📂 **GitHub Repo** | https://github.com/srinivasnarenvemgal/AlphaHub |

---

## ✨ Features

| Feature | Description | Status |
|---|---|---|
| 🔐 Authentication | Sign up, log in, log out with session management | ✅ |
| 🏘️ Communities | Create, browse & join communities | ✅ |
| 📝 Post Types | Text, Image (drag & drop), Link posts | ✅ |
| ⬆️ Voting System | Upvote / Downvote with Reddit Hot Score algorithm | ✅ |
| 💬 Comments | Add & view comments on any post | ✅ |
| 👤 User Profiles | Karma system, post history, joined communities | ✅ |
| 🔍 Live Search | Search posts & communities in real-time | ✅ |
| 📊 Sort Posts | Hot / New / Top sorting | ✅ |
| 🖼️ Image Upload | Drag & drop image upload with preview | ✅ |
| 📱 Responsive | Fully mobile responsive design | ✅ |
| 💀 Skeleton Loaders | Loading states for better UX | ✅ |
| 🎨 Custom Logo | Hand-crafted SVG hexagon logo | ✅ |

---

## 🧰 Tech Stack

| Layer | Technology | Why |
|---|---|---|
| **Language** | Vanilla JavaScript | No framework needed for MVP |
| **Markup** | HTML5 | Semantic, clean structure |
| **Styling** | CSS3 + Custom Variables | Full design system |
| **Architecture** | SPA (Single Page Application) | Fast, no page reloads |
| **Font — Headings** | Bricolage Grotesque | Editorial, high-end feel |
| **Font — Body** | Outfit | Clean, modern, readable |
| **Font — Labels** | Space Grotesk | Technical precision |
| **Logo** | Custom SVG | Unique, scalable, brand-ready |
| **Hosting** | GitHub Pages | Free, fast, reliable |

---

## 📁 Project Structure

```
AlphaHub/
├── index.html        ← Entire application (SPA)
├── README.md         ← You are here
└── screenshot.png    ← Project preview
```

---

## ▶️ Run Locally

```bash
# Option 1 — Simplest way
# Just double-click index.html — works in any browser instantly

# Option 2 — Local dev server (recommended)
npx serve .

# Option 3 — Python server
python3 -m http.server 3000

# Then visit → http://localhost:3000
```

No installs. No npm. No build step. Just open and run.

---

## 🗄️ Database Schema (Production Ready)

When scaling to full-stack, here's the production Prisma schema:

```prisma
model User {
  id        String    @id @default(cuid())
  email     String    @unique
  username  String    @unique
  posts     Post[]
  comments  Comment[]
  votes     Vote[]
  joinedAt  DateTime  @default(now())
}

model Community {
  id        String   @id @default(cuid())
  name      String   @unique
  slug      String   @unique
  desc      String
  color     String
  members   Int      @default(0)
  posts     Post[]
  createdAt DateTime @default(now())
}

model Post {
  id          String    @id @default(cuid())
  title       String
  content     String?
  imageUrl    String?
  link        String?
  type        String    // text | image | link
  communityId String
  authorId    String
  community   Community @relation(fields: [communityId], references: [id])
  author      User      @relation(fields: [authorId], references: [id])
  comments    Comment[]
  votes       Vote[]
  createdAt   DateTime  @default(now())
}

model Comment {
  id        String   @id @default(cuid())
  content   String
  postId    String
  authorId  String
  post      Post     @relation(fields: [postId], references: [id])
  author    User     @relation(fields: [authorId], references: [id])
  votes     Int      @default(0)
  createdAt DateTime @default(now())
}

model Vote {
  id     String @id @default(cuid())
  type   String // up | down
  userId String
  postId String
  user   User   @relation(fields: [userId], references: [id])
  post   Post   @relation(fields: [postId], references: [id])
  @@unique([userId, postId])
}
```

---

## 🏗️ Production Architecture

```
┌─────────────────────────────────────┐
│         Frontend (Next.js)          │
│         Tailwind CSS + TypeScript   │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│       API Layer (Express.js)        │
│       REST APIs + Middleware        │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│     Database (PostgreSQL)           │
│     ORM: Prisma                     │
└──────────────┬──────────────────────┘
               │
    ┌──────────┼──────────┐
    │          │          │
  Auth      Storage    Deploy
  Clerk   Cloudinary   Vercel
```

---

## 📅 How It Was Built — 2 Week Plan

| Day | What was built |
|---|---|
| Day 1 | Project setup, design system, CSS variables, fonts, logo |
| Day 2 | Full SPA architecture, routing, state management |
| Day 3 | Auth system — sign up, login, logout, session |
| Day 4 | Communities — create, browse, join, detail page |
| Day 5 | Posts — text, image, link creation + feed |
| Day 6 | Voting system — upvote, downvote, Hot Score algorithm |
| Day 7 | Comments — add, display, vote on comments |
| Day 8 | User profiles — karma, post history, communities tab |
| Day 9 | Live search — posts & communities |
| Day 10 | Sort system — Hot / New / Top |
| Day 11 | Image upload — drag & drop + preview |
| Day 12 | UI polish — skeleton loaders, empty states, animations |
| Day 13 | Mobile responsive — full layout overhaul |
| Day 14 | Deploy to GitHub Pages + README + LinkedIn post |

---

## 📈 Future Roadmap

- [ ] Nested / threaded comments
- [ ] Real-time updates via WebSockets
- [ ] Push notifications system
- [ ] Bookmark & save posts
- [ ] Admin moderation dashboard
- [ ] Community flairs & post tags
- [ ] Awards & recognition system
- [ ] OAuth login (Google, GitHub)
- [ ] Dark / Light theme toggle
- [ ] Full Next.js + PostgreSQL migration

---

## 🔐 Security Considerations

- Input validation on all forms
- XSS prevention via proper escaping
- Protected routes — auth required for posting/voting/commenting
- SQL injection safe (Prisma ORM in production)
- Rate limiting on API routes (production)

---

## 💡 What I Learned

```
✅ Building real products is 10× harder than following tutorials
✅ Design decisions are just as hard as technical ones
✅ Shipping imperfect > perfecting forever
✅ AI tools amplify your speed — they don't replace your thinking
✅ Every feature is a product decision, not just a coding task
```

---

## 👤 About the Builder

**Srinivas Naren Vemgal**
Student Developer @ Alphabuilders HQ

Building real products to grow as a full-stack developer.
This project was built using **Vibe Coding** — AI as the tool, me as the architect.

| | |
|---|---|
| 🔗 LinkedIn | [Connect with me](https://www.linkedin.com/in/srinivasnarenvemgal) |
| 🌐 Live Project | [AlphaHub](https://srinivasnarenvemgal.github.io/AlphaHub/) |
| 📂 GitHub | [srinivasnarenvemgal](https://github.com/srinivasnarenvemgal) |

---
