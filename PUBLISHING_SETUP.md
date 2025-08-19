# Publishing Setup Guide

This guide will help you set up automated publishing for your Alien Departure Lounge modpack to CurseForge and Modrinth.

## 🚀 Quick Start

1. **Set up your projects** on CurseForge and Modrinth
2. **Get API tokens** from both platforms
3. **Add secrets** to your GitHub repository
4. **Create releases** and watch the magic happen!

## 📋 Step-by-Step Setup

### 1. CurseForge Setup

#### Create/Find Your Project
1. Go to [CurseForge](https://www.curseforge.com/) and log in
2. Either create a new modpack project or find your existing one
3. Note your **Project ID** (found in the project URL: `curseforge.com/minecraft/modpacks/your-project/files` - the number)

#### Get API Token
1. Go to [CurseForge API Console](https://console.curseforge.com/)
2. Create a new API token
3. Copy the token (you won't see it again!)

### 2. Modrinth Setup

#### Create/Find Your Project
1. Go to [Modrinth](https://modrinth.com/) and log in
2. Either create a new modpack project or find your existing one
3. Note your **Project ID** (the slug in the URL: `modrinth.com/modpack/your-project-slug`)

#### Get API Token
1. Go to [Modrinth Settings](https://modrinth.com/settings/pats)
2. Create a new Personal Access Token
3. Select the appropriate scopes (at minimum: `WRITE_PROJECT`)
4. Copy the token

### 3. GitHub Repository Setup

#### Add Repository Secrets
1. Go to your GitHub repository
2. Navigate to **Settings** → **Secrets and variables** → **Actions**
3. Click **"New repository secret"** and add each of these:

| Secret Name | Description | Example |
|-------------|-------------|---------|
| `CURSEFORGE_TOKEN` | Your CurseForge API token | `$2a$10$...` |
| `CURSEFORGE_PROJECT_ID` | Your CurseForge project ID | `123456` |
| `MODRINTH_TOKEN` | Your Modrinth Personal Access Token | `mrp_...` |
| `MODRINTH_PROJECT_ID` | Your Modrinth project slug | `alien-departure-lounge` |

## 🎯 How to Release

### Stable Release
1. Go to your GitHub repository
2. Click **"Releases"** → **"Create a new release"**
3. **Tag version**: Use format `v1.0.0` (must start with 'v')
4. **Release title**: Something like "Alien Departure Lounge v1.0.0"
5. **Description**: Write your changelog/release notes
6. **DO NOT** check "This is a pre-release"
7. Click **"Publish release"**

### Beta Release
1. Follow the same steps as stable release
2. **Tag version**: Use format `v1.0.0-beta1` or `v1.0.0-rc1`
3. **CHECK** the "This is a pre-release" box
4. Click **"Publish release"**

## 🔧 What Happens When You Release

### Automatic Process
1. **Version Update**: Updates `manifest.json` with the release version
2. **ZIP Creation**: Creates a clean ZIP file excluding development files
3. **GitHub Upload**: Attaches ZIP to your GitHub release
4. **CurseForge Upload**: Publishes to CurseForge (if token provided)
5. **Modrinth Upload**: Publishes to Modrinth (if token provided)

### File Exclusions
The following files/folders are automatically excluded from releases:
- `.git/` - Git repository data
- `.github/` - GitHub Actions workflows
- `STAGING.md` - Development documentation
- `*.log`, `*.tmp` - Temporary files

## ✅ Testing Your Setup

### Test Without Publishing
1. Make any small change to your modpack
2. Commit and push to the `main` or `staging` branch
3. Check the **Actions** tab - a build should start automatically
4. Download the generated ZIP artifact to verify it works

### Test Publishing (Recommended)
1. Create a pre-release with version like `v0.0.8-test`
2. Check that it appears on both CurseForge and Modrinth as a beta
3. If successful, you can delete the test release

## 🛠️ Troubleshooting

### Common Issues

**"Repository secret not found"**
- Make sure secret names are exactly: `CURSEFORGE_TOKEN`, `CURSEFORGE_PROJECT_ID`, `MODRINTH_TOKEN`, `MODRINTH_PROJECT_ID`
- Secrets are case-sensitive

**"Invalid project ID"**
- CurseForge project ID should be a number (e.g., `123456`)
- Modrinth project ID should be the slug (e.g., `my-modpack-name`)

**"API token invalid"**
- CurseForge tokens expire - generate a new one if needed
- Modrinth tokens need `WRITE_PROJECT` scope

**"Game version not supported"**
- Update the workflows if you change Minecraft versions
- Currently configured for Minecraft 1.20.1 with Forge

### Getting Help
If you encounter issues:
1. Check the **Actions** tab for detailed error logs
2. Verify your project IDs and tokens
3. Make sure your projects exist and are set up correctly on both platforms

## 🎉 You're Ready!

Your modpack will now automatically:
- ✅ Build on every push
- ✅ Publish to GitHub, CurseForge, and Modrinth on release
- ✅ Handle both stable and beta releases
- ✅ Keep version numbers in sync

Happy modpacking! 🎮
