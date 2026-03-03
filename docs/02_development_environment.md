Development Environment
1. Overview

This document describes the local development environment setup for the Israride frontend application.

The project has transitioned from a single static HTML implementation to a modular architecture using Vite.

2. Requirements

Node.js 20 (enforced via .nvmrc)

npm (comes with Node.js)

Git

VS Code

3. Frontend Build Tool

The project uses:

Vite (modern frontend build tool)

Vanilla JavaScript (no framework at current MVP stage)

The build process and development server are managed via npm scripts defined in package.json.

4. Local Development Workflow

(To be documented in detail as the workflow stabilizes.)

5. Production Build

Production builds are generated using:

npm run build


This command creates an optimized production bundle in the dist/ directory.

6. Deployment

The application is currently deployed via:

Firebase Hosting

GitHub Actions (branch-based CI/CD)

7. Node Version Management

The project enforces Node.js version 20 via a .nvmrc file located in the repository root.

To ensure correct version usage:

nvm use

Frontend Architecture (Post-Vite Initialization)
1. Build Tool Introduction

The project migrated from a static HTML structure to a Vite-based build architecture.

Key changes:

The project now relies on Node.js and npm.

JavaScript is structured as ES modules.

The development server and build lifecycle are handled by Vite.

Build and dev-server execution are controlled through package.json scripts.

2. Why index.html Is No Longer a Standalone File

The index.html file remains in the project root and acts as the HTML template entry processed by Vite during development and production builds.

It is no longer a standalone executable HTML file.

This is because:

JavaScript uses ES modules.

Code is imported using import statements.

These imports are resolved and processed by Vite.

Without the Vite dev server or build step, modules will not load correctly in the browser.

Opening index.html directly via double-click bypasses the module processing and will not correctly initialize the application.

3. Role of Vite

Vite is responsible for:

Running the development server

Processing ES modules

Resolving imports

Performing hot module replacement (HMR) during development

Bundling the application for production

Minifying and optimizing assets

Generating the dist/ directory for deployment

During production build (npm run build), Vite outputs optimized static assets into the dist/ directory.

4. Project Structure Overview
src/

The src/ directory contains all application source code.

Files inside src/:

Are written using modern JavaScript (ES modules)

Are processed by Vite

Are bundled during production build

This is where the application logic lives.

src/main.js

src/main.js is the application entry point.

It:

Initializes the application

Imports required modules

Mounts the UI to the root DOM element

public/

The public/ directory contains static assets that are copied as-is to the production build without being processed by Vite.

Examples may include static images, icons, or manifest files.

dist/

The dist/ directory is generated automatically during production build.

It contains:

Optimized

Minified

Production-ready static assets

This directory is the deployment artifact and should be deployed to Firebase Hosting.