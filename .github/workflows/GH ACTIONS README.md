# GitHub Actions Workflows

This repository contains GitHub Actions workflows for automated building and publishing of the Alien Departure Lounge modpack.

## Workflows

### 1. `build-on-push.yml` - Build ZIP on Push
- **Triggers**: Push to `main` or `staging` branches, or pull requests
- **Purpose**: Creates ZIP artifacts for testing and development
- **Retention**: 30 days
- **Output**: Downloadable artifacts in Actions tab

### 2. `release-build.yml` - Full Release
- **Triggers**: When a release is published (not pre-release)
- **Purpose**: Publishes stable releases to all platforms
- **Platforms**: GitHub, CurseForge, Modrinth
- **Release Type**: `release`

### 3. `beta-release.yml` - Beta Release
- **Triggers**: When a pre-release is published
- **Purpose**: Publishes beta versions to all platforms
- **Platforms**: GitHub, CurseForge, Modrinth
- **Release Type**: `beta`

## Required Secrets

To enable publishing to CurseForge and Modrinth, add these secrets to your repository:

### CurseForge Secrets
- `CURSEFORGE_TOKEN`: Your CurseForge API token
- `CURSEFORGE_PROJECT_ID`: Your CurseForge project ID

### Modrinth Secrets
- `MODRINTH_TOKEN`: Your Modrinth API token
- `MODRINTH_PROJECT_ID`: Your Modrinth project ID (slug)

## How to Add Secrets

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Add each secret with its corresponding value

## Release Process

### For Stable Releases
1. Create a new release in GitHub
2. Use version tags like `v1.0.0` (must start with 'v')
3. **Do NOT check "This is a pre-release"**
4. Fill in release notes
5. Click "Publish release"

### For Beta Releases
1. Create a new release in GitHub
2. Use version tags like `v1.0.0-beta1`
3. **Check "This is a pre-release"**
4. Fill in release notes
5. Click "Publish release"

## Features

- ✅ Automatic ZIP creation with proper exclusions
- ✅ Version synchronization between Git tags and manifest.json
- ✅ Multi-platform publishing (GitHub, CurseForge, Modrinth)
- ✅ Separate workflows for stable and beta releases
- ✅ Conditional publishing (only if tokens are configured)
- ✅ Proper Minecraft version and mod loader tagging
