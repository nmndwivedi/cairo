# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build and Development Commands

```bash
pnpm install          # Install dependencies
npx expo start        # Start development server (shows options for iOS/Android/web)
npx expo start --ios  # Start iOS simulator
npx expo start --android  # Start Android emulator
npx expo start --web  # Start web version
pnpm run lint         # Run ESLint (uses expo lint)
```

## Architecture

This is an Expo React Native app using file-based routing via expo-router.

### Key Structure

- **app/**: File-based routing directory
  - `_layout.tsx`: Root layout with ThemeProvider and Stack navigator
  - `(tabs)/`: Tab group with bottom tab navigation
  - `modal.tsx`: Modal screen accessible from anywhere
- **components/**: Reusable UI components with platform-specific variants (`.ios.tsx`)
- **hooks/**: Custom hooks including platform-specific versions (`.web.ts`)
- **constants/theme.ts**: Color definitions for light/dark themes

### Routing

Uses expo-router with typed routes enabled. The `(tabs)` directory creates a tab navigator with Home and Explore tabs. The root layout wraps the app in a ThemeProvider for dark/light mode support.

### Path Aliases

`@/*` maps to the project root (configured in tsconfig.json).

### Platform-Specific Files

Components and hooks use platform extensions:
- `.ios.tsx` for iOS-specific implementations
- `.web.ts` for web-specific implementations
- Base file (no extension) for default/Android
