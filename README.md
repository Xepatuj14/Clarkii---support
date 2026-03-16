# Clarkii Outdoors

Clarkii Outdoors is a premium, offline-first iPhone fishing log built for anglers who want a clean and reliable way to track time on the water.

The app helps users log trips, catches, fishing spots, gear, notes, and photos while keeping data local-first and practical for real field use.

## Overview

Clarkii is designed as a personal fishing journal rather than a social app. It focuses on helping one angler build a durable record of fishing history with fast logging, strong detail screens, map context, exports, backups, and polished presentation.

## Core Features

- Offline-first local data storage
- Onboarding with optional permissions
- Trip logging and trip planning fields
- Catch logging with measurements, notes, and multiple photos
- Quick Catch flow for faster entry in the field
- Saved fishing spots and location history
- Map-based browsing for trips, catches, and spots
- Search, filters, and saved recall workflows
- Analytics, personal records, and trophy views
- Data export, backup, and restore workflows

## What Clarkii Tracks

- Trips
- Fishing spots
- Catches
- Gear
- Notes
- Photos

## Screenshots

Add App Store screenshots or simulator captures here so visitors can quickly understand the product.

Suggested screenshots:

- Home dashboard
- Trip detail
- Catch detail
- Map/history view
- Analytics or trophy gallery
- Quick Catch flow

## Tech Stack

- Expo
- React Native
- TypeScript
- Expo Router
- SQLite via `expo-sqlite`
- Zustand
- `react-native-maps`
- `react-native-chart-kit`
- `react-native-svg`
- `react-native-cloud-storage`

## Requirements

- Expo SDK 54
- Node.js and npm
- iPhone + Expo Go for basic testing
- iOS development build for native-only features such as iCloud backup sync

## Getting Started

1. Install dependencies:

   ```bash
   npm install
   ```

2. Start Expo:

   ```bash
   npm run start
   ```

3. If LAN discovery fails, start with tunnel mode:

   ```bash
   npm run start -- --tunnel
   ```

4. Optional checks:

   ```bash
   npm run -s typecheck
   npm run -s lint
   ```

## Available Scripts

```bash
npm run start
npm run ios
npm run android
npm run web
npm run lint
npm run typecheck
npm run start:local
npm run start:tunnel
npm run fixtures:drift
```

## Permissions

Clarkii may request access to the following device capabilities depending on the features a user chooses to use:

- Location, to save catch and trip spots
- Photo library, to attach existing photos
- Photo library save access, to save generated catch cards
- Motion sensors, for local barometric pressure readings when available

## Data and Privacy Notes

- Clarkii is offline-first and stores core user data locally on the device
- Export and backup tools are included for data portability and recovery
- Restore currently uses replace mode rather than merge mode
- iCloud backup behavior is manual on supported iOS native builds

## Project Structure

```text
app/
  (tabs)/
    _layout.tsx
    index.tsx
    trips.tsx
    add-catch.tsx
    analytics.tsx
    settings.tsx
  catches/
    [id].tsx
    edit/[id].tsx
  photos/viewer.tsx
  spots/
    index.tsx
    new.tsx
    [id].tsx
    edit/[id].tsx
  trips/
    [id].tsx
    new.tsx
    edit/[id].tsx
  map.tsx
  quick-catch.tsx
  trophies.tsx
  _layout.tsx
src/
  components/
  constants/
  db/
  features/
  hooks/
  lib/
  services/
  store/
  types/
```

## iOS Native iCloud Sync Setup

Clarkii uses `react-native-cloud-storage` for native iCloud backup sync on iOS development or production builds.

1. Confirm the plugin is present in app config
2. Regenerate the native iOS project after config changes:

   ```bash
   npx expo prebuild -p ios --clean
   ```

3. Install pods:

   ```bash
   npx pod-install
   ```

4. Run an iOS development build:

   ```bash
   npm run ios
   ```

5. In Apple Developer, enable the iCloud capability for the app identifier

## Migrations

- Migrations run automatically at startup via `_migrations`
- Current latest migration is `v4`
- Existing user data is preserved
- Seed data only runs when `trips` is empty

## Export, Backup, and Restore

In the app:

- `Settings -> Data Export`
  - JSON snapshot export
  - Trips CSV export
  - Catches CSV export
  - Spots CSV export
- `Settings -> Backup & Restore`
  - Create local backup files
  - Restore from local backup files
  - Sync latest backup payload to iCloud on supported iOS builds
  - Restore the latest synced payload from iCloud on supported iOS builds

## Data Model

Current SQLite tables include:

- `trips`
- `catches`
- `catch_photos`
- `species`
- `settings`
- `spots`
- `cached_map_regions`
- `offline_tile_packs`
- `_migrations`

## Common Issues

- Metro cache issues:

  ```bash
  npx expo start -c
  ```

- Expo Go SDK mismatch:
  - Confirm the project is on Expo SDK 54
- iCloud sync unavailable in Expo Go:
  - Use an iOS development build after prebuild
- Permissions denied:
  - Use the in-app path to open iOS app settings

## Known Limitations

- Restore currently uses replace mode, not merge mode
- iCloud sync is manual, not automatic multi-device conflict resolution
- Exports include photo URIs and metadata, not binary image files
- CSV exports are flat spreadsheet-oriented exports rather than full relational backups

## Website Pages

The repo also includes simple GitHub Pages files for the public-facing site:

- [Home](./index.html)
- [Support](./support.html)
- [Privacy Policy](./privacy.html)
- [404 Page](./404.html)

## Roadmap

Potential future improvements may include:

- Better screenshot and media documentation
- Expanded public website content
- More refined restore and sync workflows
- Additional fishing insights and analytics surfaces

## License

Add a license here before making the repository public.

If you do not want others to reuse or redistribute the code, make that explicit in a license file and this section.
