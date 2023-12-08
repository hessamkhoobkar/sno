# Snø - Free Blog Theme

Snø is a free blog theme built with Astro and Tailwind. It offers a clean and modern design, making it easy for bloggers and developers to create stylish and functional blogs.

## Todo list

- [ ] Add side wide search functionality
- [ ] Implement a side wide reponsive design
- [ ] Update the readme to reflect the changes

## Getting Started

### Prerequisites

Make sure you have Node.js and npm installed on your machine.

### Installation

Clone the repository:

```bash
git clone https://github.com/hessamkhoobkar/sno.git
```

Install dependencies:

```bash
cd sno
pnpm install
```

Start the development server:

```bash
pnpm dev
```

Visit http://localhost:3000 in your browser.

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
├── public/
├── src/
│   ├── components/
│   ├── content/
│   ├── layouts/
│   └── pages/
├── astro.config.mjs
├── README.md
├── package.json
└── tsconfig.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

The `src/content/` directory contains "collections" of related Markdown and MDX documents. Use `getCollection()` to retrieve posts from `src/content/blog/`, and type-check your frontmatter using an optional schema. See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) to learn more.

Any static assets, like images, can be placed in the `public/` directory.

## 👀 Want to learn more?

Check out [Astro documentation](https://docs.astro.build).
