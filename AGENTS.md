# AGENT.md - Frontend Mobile (React Native + Expo)

## Project Overview
This is the mobile application built with React Native, Expo, and NativeWind.
It shares the same backend API as the web frontend.

## Tech Stack
- **Framework**: React Native + Expo (SDK 51)
- **Navigation**: Expo Router
- **Language**: TypeScript
- **Styling**: NativeWind (Tailwind CSS for React Native)
- **UI Components**: Custom shadcn-inspired components
- **State Management**: Zustand
- **Server State**: TanStack Query (React Query)
- **Forms**: React Hook Form + Zod
- **HTTP Client**: Axios
- **Storage**: Expo Secure Store (for tokens)
- **Icons**: Lucide React Native

## Important Note About UI
shadcn/ui does NOT work in React Native.
We use NativeWind instead which gives us the same Tailwind CSS syntax.
We build our own shadcn-inspired components using:
- NativeWind (Tailwind classes)
- class-variance-authority (CVA for variants)
- clsx + tailwind-merge (cn() utility)

## Project Setup

### Create Project
```bash
npx create-expo-app@latest frontend-mobile --template blank-typescript
cd frontend-mobile
```

### Install All Dependencies
```bash
# Core Expo packages
npx expo install expo-router expo-linking expo-constants expo-status-bar expo-secure-store

# UI & Navigation
npx expo install react-native-safe-area-context react-native-screens react-native-reanimated react-native-svg

# NativeWind (Tailwind for React Native)
npm install nativewind
npm install --save-dev tailwindcss

# shadcn-like utilities
npm install class-variance-authority clsx tailwind-merge

# Icons
npm install lucide-react-native

# API & State
npm install axios zustand @tanstack/react-query

# Forms & Validation
npm install react-hook-form zod @hookform/resolvers

# Notifications
npm install react-native-toast-message
```

## Run Locally
```bash
npm install
npx expo start
```
- Press `a` for Android emulator
- Press `i` for iOS simulator
- Scan QR code with Expo Go app for physical device

## Build for Production
```bash
# Install EAS CLI
npm install -g eas-cli
eas login

# Configure
eas build:configure

# Build
eas build --platform android
eas build --platform ios
```

## Code Style Rules
- All components must be TypeScript
- No any types - define proper interfaces
- Use NativeWind className (not StyleSheet) for all styling
- All API calls go through src/lib/api/ folder
- All forms must have Zod validation
- Tokens must always use SecureStore (never AsyncStorage)
- All shared types must match backend response exactly