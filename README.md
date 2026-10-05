# iOS App Store Icon Extractor

A lightweight, browser-based **App Store icon extractor** designed to work with GitHub Pages and GitHub Codespaces.

The project provides a simple interface for looking up an iOS app and displaying available App Store artwork, including icons across Apple's historical iOS era from **iOS 1.0 through iOS 26.0** where artwork/data is available.

> **Important:** This is an educational web-app example. It does not extract icons from installed iOS applications or bypass Apple's App Store protections. Artwork remains subject to the rights and terms of its respective owners.

## ✨ Features

- 🔎 Search for App Store apps
- 🖼️ Display App Store application icons
- 📱 Designed around the visual history of iOS 1.0–iOS 26.0
- 🌐 Runs entirely as a web application
- 🚀 GitHub Pages compatible
- 💻 GitHub Codespaces compatible
- 📦 No server required for the basic static version
- 📋 Copy image URLs
- ⬇️ Download displayed artwork when permitted by the source
- 📐 Show icon dimensions and image metadata
- 🌙 Responsive interface suitable for desktop and mobile browsers

## 🖥️ Demo

After enabling GitHub Pages, the application can be hosted at:

```text
https://YOUR-USERNAME.github.io/ios-app-store-icon-extractor/
```

Replace `YOUR-USERNAME` with your GitHub username.

## 📁 Project Structure

```text
ios-app-store-icon-extractor/
├── .devcontainer/
│   └── devcontainer.json
├── .github/
│   └── workflows/
│       └── pages.yml
├── assets/
│   └── icons/
├── index.html
├── style.css
├── app.js
├── README.md
└── LICENSE
```

## 🚀 Run with GitHub Codespaces

### 1. Create the repository

Create a new GitHub repository named:

```text
ios-app-store-icon-extractor
```

### 2. Open Codespaces

From the repository:

**Code → Codespaces → Create codespace on main**

Codespaces will automatically configure the development environment using:

```text
.devcontainer/devcontainer.json
```

### 3. Start a local web server

For a simple static project, run:

```bash
python3 -m http.server 8080
```

Then open port `8080` from the Codespaces **Ports** panel.

Alternatively, if the project uses Node.js:

```bash
npm install
npm run dev
```

## 🌐 GitHub Pages Deployment

The project can be deployed directly from GitHub Actions.

Example workflow:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: .

      - name: Deploy
        id: deployment
        uses: actions/deploy-pages@v4
```

Save this as:

```text
.github/workflows/pages.yml
```

Then push it:

```bash
git add .
git commit -m "Deploy App Store Icon Extractor"
git push origin main
```

GitHub Actions will deploy the site to GitHub Pages.

## 🔎 How the Extractor Works

The basic application can use publicly available App Store metadata to identify an application and retrieve artwork URLs.

A typical metadata response can contain information such as:

```json
{
  "trackName": "Example App",
  "bundleId": "com.example.app",
  "version": "1.0.0",
  "artworkUrl100": "https://example.com/icon100.png"
}
```

The application can then display the artwork:

```html
<img
  src="ICON_URL"
  alt="App Store icon"
  loading="lazy"
/>
```

## 📱 iOS Version History

The application can optionally provide an informational timeline:

| iOS Era | Approx. Period | Icon Design Context |
|---|---:|---|
| iPhone OS 1.x | 2007 | Original iPhone-era icons |
| iPhone OS 2.x | 2008 | App Store introduced |
| iPhone OS 3.x | 2009 | Early App Store ecosystem |
| iOS 4.x | 2010 | Retina-era transition |
| iOS 5.x | 2011 | Notification Center era |
| iOS 6.x | 2012 | Pre-iOS 7 visual design |
| iOS 7.x | 2013 | Major flat-design transition |
| iOS 8.x | 2014 | Modernized flat design |
| iOS 9.x | 2015 | Continued flat-design system |
| iOS 10.x | 2016 | Modern iOS design language |
| iOS 11.x | 2017 | App Store redesign |
| iOS 12.x | 2018 | Refined modern interface |
| iOS 13.x | 2019 | Dark Mode introduced |
| iOS 14.x | 2020 | Widgets and App Library |
| iOS 15.x | 2021 | Focus and redesigned notifications |
| iOS 16.x | 2022 | Lock Screen customization |
| iOS 17.x | 2023 | StandBy and interactive features |
| iOS 18.x | 2024 | Home Screen customization |
| iOS 26.x | 2026 | Current-generation iOS design |

The version timeline is informational. **An App Store metadata service does not necessarily provide historical icons for every iOS release.**

## 🖼️ Icon Sizes

The extractor can normalize artwork for display while preserving the original image URL.

Example:

```text
100 × 100
512 × 512
1024 × 1024
```

If a source provides a higher-resolution artwork URL, the application should prefer the highest available resolution rather than artificially upscaling a smaller image.

## 🧩 Example Interface

```text
┌──────────────────────────────────────────────┐
│        iOS App Store Icon Extractor          │
├──────────────────────────────────────────────┤
│                                              │
│  Search App                                  │
│  ┌────────────────────────────────────────┐  │
│  │ Example App                            │  │
│  └────────────────────────────────────────┘  │
│                         [ Extract Icon ]      │
│                                              │
├──────────────────────────────────────────────┤
│                                              │
│                 ┌──────────┐                 │
│                 │          │                 │
│                 │   ICON   │                 │
│                 │          │                 │
│                 └──────────┘                 │
│                                              │
│              Example App                     │
│              Version 1.0                     │
│                                              │
│       [Copy URL] [Open Image] [Download]     │
│                                              │
└──────────────────────────────────────────────┘
```

## ⚠️ API and CORS Considerations

A purely static browser application may encounter **CORS restrictions** when requesting external APIs directly.

For production deployments, consider one of these approaches:

1. Use an API that explicitly supports browser requests.
2. Use a small server-side proxy.
3. Use a serverless function.
4. Store permitted metadata in a static JSON dataset.

Do **not** attempt to circumvent CORS or access controls.

## 🔐 Privacy

The basic application does not need:

- User accounts
- Passwords
- App Store credentials
- Apple ID credentials
- Personal information
- Installed-app access

Search requests should contain only the information necessary to identify the requested app.

## 🍎 Apple and App Store Notice

Apple, App Store, iOS, iPhone, iPad, and related marks are trademarks of Apple Inc.

This project is an independent educational example and is **not affiliated with, sponsored by, or endorsed by Apple Inc.**

App icons, screenshots, names, and other application artwork may belong to their respective developers or copyright holders.

## 🛠️ Development

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/ios-app-store-icon-extractor.git
cd ios-app-store-icon-extractor
```

Start the local server:

```bash
python3 -m http.server 8080
```

Open:

```text
http://localhost:8080
```

## 📋 Recommended Browser Support

The application is designed for modern browsers supporting:

- ES2020+
- Fetch API
- CSS Grid
- CSS Flexbox
- Async/await
- Clipboard API
- Responsive layouts

Recommended browsers include current versions of:

- Safari
- Chrome
- Firefox
- Edge

## 📦 Optional PWA Support

The project can be extended into a Progressive Web App by adding:

```text
manifest.json
service-worker.js
icons/
```

Example manifest:

```json
{
  "name": "iOS App Store Icon Extractor",
  "short_name": "Icon Extractor",
  "start_url": "./",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

## 🧪 Testing

Before deployment, test:

```text
✓ App search
✓ Icon loading
✓ Broken image handling
✓ Mobile layout
✓ Desktop layout
✓ Clipboard functionality
✓ Download behavior
✓ API failure handling
✓ GitHub Pages routing
```

## 🐛 Troubleshooting

### Icons do not load

Check the browser developer console for:

```text
CORS
404
403
NetworkError
```

The remote artwork provider may restrict direct browser access.

### GitHub Pages shows a 404

Verify:

```text
Settings
→ Pages
→ Build and deployment
→ GitHub Actions
```

Also verify that the workflow completed successfully.

### Codespaces does not show the application

Make sure a web server is running:

```bash
python3 -m http.server 8080
```

Then make port `8080` available through the Codespaces Ports panel.

## 📜 License

The source code can be released under the MIT License:

```text
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files, to deal in the Software
without restriction, including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of the
Software, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
```

## ⭐ Contributing

Pull requests and improvements are welcome.

Possible contributions include:

- Better App Store metadata handling
- Improved icon resolution detection
- Historical icon datasets
- PWA support
- Accessibility improvements
- Dark Mode
- Additional export formats
- Improved mobile UI
- Automated tests

## 📌 Roadmap

- [x] GitHub Pages support
- [x] GitHub Codespaces support
- [x] Responsive UI
- [ ] Historical icon database
- [ ] Multiple icon-resolution comparison
- [ ] Drag-and-drop image inspection
- [ ] PWA installation
- [ ] Offline metadata cache
- [ ] Batch app lookup
- [ ] Icon metadata export
- [ ] ZIP export for user-supplied/publicly permitted artwork

---

**iOS App Store Icon Extractor**  
A GitHub Pages + GitHub Codespaces-ready educational web-app example for exploring App Store application artwork across the iOS era.
