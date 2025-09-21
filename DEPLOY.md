# Firebase Deployment Guide

## ✅ Setup Complete

Your Firebase hosting is now configured with **zero duplication risk**:

- `public/index.html` is a **symbolic link** to `../index.html`
- There is only **one source file** - the root `index.html`
- Any edits to root `index.html` are automatically reflected in `public/`

## 🚀 Deploy Steps

1. **Create Firebase project** (if you haven't already):
   - Go to https://console.firebase.google.com/
   - Click "Create a project"
   - Note your project ID

2. **Update project ID**:
   - Edit `.firebaserc` file
   - Replace `"your-project-id-here"` with your actual Firebase project ID

3. **Login to Firebase** (first time only):
   ```powershell
   firebase login
   ```

4. **Deploy**:
   ```powershell
   firebase deploy --only hosting
   ```

## 🔒 Safety Measures in Place

- **Symbolic link**: `public/index.html` → `../index.html` (no duplication)
- **Ignored files**: Specs, scripts, and dev files won't be deployed
- **Single source**: Root `index.html` is the only editable version
- **Cache headers**: Optimal caching for performance

## 📝 Important Notes

- **ONLY edit** `index.html` in the root folder
- `public/index.html` is just a link - changes there affect the root file
- Firebase will serve only what's needed, ignoring dev files
- Your game will be available at: `https://your-project-id.web.app`

## 🛠️ Optional Commands

```powershell
# Test locally before deploying
firebase serve --only hosting

# View deployment history
firebase hosting:clone

# Use specific project
firebase use your-project-id
```