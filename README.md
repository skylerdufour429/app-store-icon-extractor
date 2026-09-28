# iOS IPA Archive

A GitHub Pages + GitHub Codespaces-ready web archive for browsing and downloading iOS IPA files.

## Features

- 📱 iOS IPA archive listing
- 🔎 App metadata display
- ⬇️ Direct IPA download links
- 🌐 GitHub Pages compatible
- ☁️ GitHub Codespaces development ready
- 📝 Simple static HTML/CSS/JavaScript structure

## App Archive

| App Name | Bundle ID | Version | Platform | Minimum OS | Binary Size | Download |
|---|---|---|---|---|---|---|
| Animal Sounds | `com.smartbabyapps.animalsounds` | 2.0 | iOS | 3.0 | 19.8 MB | [Download IPA](https://archive.org/download/animal-sounds-2.0/Animal%20Sounds%202.0.ipa) |

## Example App Details

### Animal Sounds

- **App Name:** Animal Sounds
- **Bundle ID:** `com.smartbabyapps.animalsounds`
- **Version:** 2.0
- **Platform:** iOS
- **Minimum OS:** 3.0
- **Binary Size:** 19.8 MB
- **IPA File:** [Animal Sounds 2.0.ipa](https://archive.org/download/animal-sounds-2.0/Animal%20Sounds%202.0.ipa)

## Project Structure

```
ipa-archive/
├── index.html
├── style.css
├── app.js
├── apps.json
├── README.md
└── .devcontainer/
    └── devcontainer.json
```

## Running in GitHub Codespaces

1. Open the repository on GitHub.
2. Select **Code → Codespaces → Create codespace**.
3. Start a local server:

```bash
python3 -m http.server 8080
```

4. Open the forwarded port in your browser.

## Deploy with GitHub Pages

1. Open repository **Settings**.
2. Go to **Pages**.
3. Select:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
4. Save.

Your IPA archive website will be available at:

```
https://YOUR_USERNAME.github.io/ipa-archive/
```

## License

This project is provided as an example archive interface.
