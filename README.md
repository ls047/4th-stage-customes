# Vue TypeScript SOA Project

A modern Vue 3 application built with TypeScript, featuring Service-Oriented Architecture (SOA) principles. This project includes advanced UI components, state management, and routing capabilities.

## Features

- 🚀 **Vue 3** with Composition API
- 📘 **TypeScript** for type safety
- 🎨 **Modern UI** with PrimeVue and Ant Design Vue
- 🗺️ **Interactive Maps** with Leaflet integration
- 🔐 **JWT Authentication** support
- 📱 **QR Code** generation capabilities
- 🎭 **Animations** with Motion-V
- 🎯 **State Management** with Pinia
- 🛣️ **Routing** with Vue Router

## Tech Stack

- **Frontend**: Vue 3, TypeScript, Vite
- **UI Libraries**: PrimeVue, Ant Design Vue
- **Styling**: Tailwind CSS
- **State Management**: Pinia
- **Routing**: Vue Router
- **Maps**: Leaflet
- **Authentication**: JWT
- **Build Tool**: Vite

## Prerequisites

- Node.js (version 18 or higher)
- npm or yarn package manager

## Installation

1. Clone the repository:
```bash
git clone <your-new-repository-url>
cd vue-ts-soa
```

2. Install dependencies:
```bash
npm install
```

## Development

### Start Development Server
```bash
npm run dev
```

### Type Checking
```bash
npm run type-check
```

### Linting
```bash
npm run lint
```

### Code Formatting
```bash
npm run format
```

## Production

### Build for Production
```bash
npm run build
```

### Preview Production Build
```bash
npm run preview
```

## Project Structure

```
src/
├── pages/          # Application pages
├── routers/        # Vue Router configuration
├── App.vue         # Root component
├── main.ts         # Application entry point
└── style.css       # Global styles
```

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## License

This project is private and proprietary.
