## Basics of NPM and Installing Packages

NPM (Node Package Manager) is used to manage JavaScript libraries and dependencies.

### Installing NPM:
- Download and install **Node.js** from [nodejs.org](https://nodejs.org/). NPM comes bundled with Node.js.
- Verify installation:
  ```sh
  node -v   # Check Node.js version
  npm -v    # Check NPM version
  ```

### Installing Packages:
- Install a package globally:
  ```sh
  npm install -g package-name
  ```
- Install a package locally (in project):
  ```sh
  npm install package-name
  ```
- Install all dependencies from `package.json`:
  ```sh
  npm install
  ```

## Setting Up React with Node.js

1. Install Node.js (if not installed already).
2. Create a new React app:
   ```sh
   npx create-react-app my-app
   cd my-app
   npm start
   ```
3. Open `http://localhost:3000/` to view the app.

## Installing React-Vite Boilerplate

Vite is a fast build tool for React applications.

### Steps:
1. Install Vite:
   ```sh
   npm create vite@latest my-vite-app --template react
   ```
2. Navigate into the project folder:
   ```sh
   cd my-vite-app
   ```
3. Install dependencies:
   ```sh
   npm install
   ```
4. Start development server:
   ```sh
   npm run dev
   ```

## Installing and Using React Developer Tools

React Developer Tools is a browser extension for debugging React applications.

### Installation:
- Chrome: Install from [Chrome Web Store](https://chrome.google.com/webstore/detail/react-developer-tools/)
- Firefox: Install from [Firefox Add-ons](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)

### Usage:
- Open **Developer Console** (`F12` or `Ctrl + Shift + I`).
- Navigate to the **React tab**.
- Inspect React components and their state.

## Learning Basic Terminal Commands

| Command | Description |
|---------|------------|
| `pwd`   | Print current working directory |
| `ls`    | List files in directory |
| `cd`    | Change directory |
| `clear` | Clear the terminal screen |
