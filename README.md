# iOS IPA Archive

A GitHub Pages and GitHub Codespaces-ready web archive for hosting and browsing iOS IPA files.

## 📱 App Information

| Field | Details |
|---|---|
| **App Name** | Animal Sounds |
| **Bundle ID** | `com.smartbabyapps.animalsounds` |
| **Version** | 2.0 |
| **Platform** | iOS |
| **Minimum OS** | iOS 3.0 |
| **Binary Size** | 19.8 MB |
| **App Bundle** | `Payload/Animal Sounds.app` |
| **Bundle Contents** | 608 items |

## 📦 IPA Archive Entry

### Animal Sounds

- **Name:** Animal Sounds
- **Bundle Identifier:** `com.smartbabyapps.animalsounds`
- **Version:** 2.0
- **Device Platform:** iPhone / iPod touch
- **Minimum iOS Version:** 3.0
- **Download:** `AnimalSounds.ipa`

## 🗂 Archive Structure

```
ios-ipa-archive/
├── index.html
├── README.md
├── apps/
│   └── animal-sounds/
│       ├── AnimalSounds.ipa
│       ├── icon.png
│       └── metadata.json
├── assets/
│   ├── style.css
│   └── app.js
└── .github/
    └── workflows/
        └── pages.yml
```

## 🚀 GitHub Pages Deployment

This project is designed to run directly on GitHub Pages.

### Enable Pages

1. Open repository settings.
2. Go to **Pages**.
3. Select:

```
Source: GitHub Actions
```

4. Push changes to the `main` branch.

The archive will be available at:

```
https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/
```

## 💻 GitHub Codespaces

Open this repository in GitHub Codespaces:

1. Click **Code**
2. Select **Codespaces**
3. Create a new codespace

Development server:

```bash
python3 -m http.server 8000
```

Open:

```
http://localhost:8000
```

## 📄 App Metadata Example

`apps/animal-sounds/metadata.json`

```json
{
  "name": "Animal Sounds",
  "bundleIdentifier": "com.smartbabyapps.animalsounds",
  "version": "2.0",
  "platform": "iOS",
  "minimumOS": "3.0",
  "size": "19.8 MB",
  "bundlePath": "Payload/Animal Sounds.app",
  "bundleItems": 608,
  "ipa": "AnimalSounds.ipa"
}
```

## 🔗 IPA Installation

Supported installation methods depend on device configuration and signing status.

Possible distribution methods:

- Enterprise signed IPA
- Ad Hoc distribution
- Development provisioning
- Local archive reference

## 🛠 Features

- Static GitHub Pages hosting
- Mobile-friendly app catalog
- IPA metadata display
- Bundle information viewer
- GitHub Codespaces development support
- No backend required

## 📜 License

This archive interface is provided as an example project.

Only distribute IPA files that you have permission to host and share.
