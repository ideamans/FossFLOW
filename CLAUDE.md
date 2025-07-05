# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

FossFLOW is a React-based Progressive Web App (PWA) for creating isometric technical diagrams. It's a privacy-first tool that stores all data locally in the browser.

## Essential Commands

```bash
# Install dependencies
npm install

# Start development server (http://localhost:3000)
npm start

# Run tests
npm test

# Build for production
npm run build

# Build with custom deployment path
PUBLIC_URL="https://yourdomain.com/path" npm run build
```

## Architecture Overview

### Core Components

1. **App.tsx**: Main application component managing:
   - Diagram state via `usePersistedDiagram` hook
   - Auto-save functionality (5-second intervals)
   - Import/Export operations
   - Integration with fossflow library

2. **Storage System**:
   - `usePersistedDiagram.ts`: Custom hook for localStorage persistence
   - `StorageManager.tsx`: UI for managing browser storage limits
   - `diagramUtils.ts`: Utilities for diagram data manipulation
   - Session-based storage with 5-10MB browser limits

3. **PWA Support**:
   - `service-worker.js`: Enables offline functionality
   - `manifest.json`: PWA configuration

### Key Dependencies

- **fossflow**: ^1.0.5 - Forked version of isoflow library (core diagramming engine)
- **@isoflow/isopacks**: Icon packs for AWS, Azure, GCP, Kubernetes
- **React 18** with TypeScript and Create React App

### Deployment

GitHub Pages deployment is automated via GitHub Actions on push to master branch. The app is deployed at https://stan-smith.github.io/FossFLOW/

### Development Notes

1. This is a Create React App project (not ejected)
2. TypeScript strict mode is enabled
3. The fossflow library is a custom fork published on NPM
4. All diagram data is stored in browser localStorage - no backend
5. Export/Import functionality provides permanent storage solution