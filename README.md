# iOS IPA Archive

A GitHub Pages + GitHub Codespaces-ready web app for hosting and browsing an iOS IPA archive.

The app provides a simple interface to view available IPA files with:

- App Name
- Bundle Identifier
- Version
- Platform
- Minimum iOS Version
- Binary Size
- IPA Download Link

## Features

✅ Static website compatible with GitHub Pages  
✅ Works in GitHub Codespaces  
✅ No backend required  
✅ JSON-based app catalog  
✅ Direct IPA downloads  
✅ Mobile-friendly UI  

## Demo

GitHub Pages:

```
https://YOUR_USERNAME.github.io/ipa-archive/
```

## Project Structure

```
ipa-archive/
│
├── index.html
├── styles.css
├── apps.json
├── README.md
│
├── ipa/
│   ├── ExampleApp.ipa
│   └── AnotherApp.ipa
│
└── .devcontainer/
    └── devcontainer.json
```

## App Archive

| App Name | Bundle ID | Version | Platform | Minimum OS | Binary Size | Download |
|----------|-----------|---------|----------|------------|-------------|----------|
| Example App | com.example.app | 1.0.0 | iOS | iOS 15.0+ | 45 MB | [Download IPA](ipa/ExampleApp.ipa) |
| Demo Player | com.demo.player | 2.3.1 | iOS | iOS 16.0+ | 82 MB | [Download IPA](ipa/DemoPlayer.ipa) |

## apps.json Example

```json
[
  {
    "name": "Example App",
    "bundleId": "com.example.app",
    "version": "1.0.0",
    "platform": "iOS",
    "minimumOS": "15.0",
    "size": "45 MB",
    "ipa": "ipa/ExampleApp.ipa"
  },
  {
    "name": "Demo Player",
    "bundleId": "com.demo.player",
    "version": "2.3.1",
    "platform": "iOS",
    "minimumOS": "16.0",
    "size": "82 MB",
    "ipa": "ipa/DemoPlayer.ipa"
  }
]
```

## GitHub Pages Setup

1. Open repository settings.

2. Go to:

```
Settings → Pages
```

3. Select:

```
Deploy from branch
```

4. Choose:

```
main / root
```

5. Save.

Your archive will be available at:

```
https://YOUR_USERNAME.github.io/ipa-archive/
```

## GitHub Codespaces Setup

Create a Codespace:

```
Code → Codespaces → Create codespace
```

Run a local preview:

```bash
python3 -m http.server 8080
```

Open:

```
http://localhost:8080
```

## Adding a New IPA

1. Upload the IPA:

```
ipa/MyApp.ipa
```

2. Add an entry to `apps.json`:

```json
{
  "name": "My App",
  "bundleId": "com.company.myapp",
  "version": "1.0.0",
  "platform": "iOS",
  "minimumOS": "15.0",
  "size": "120 MB",
  "ipa": "ipa/MyApp.ipa"
}
```

3. Commit and push:

```bash
git add .
git commit -m "Add new IPA"
git push
```

## Requirements

- GitHub account
- GitHub Pages enabled repository
- IPA files hosted in the repository
- Modern web browser

## License

MIT License
