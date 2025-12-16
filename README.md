# 🛰️ Satellite Real vs AI Image Detector

A production-ready web application that detects real vs AI-generated satellite imagery using PCA (Principal Component Analysis) sensor artifact analysis combined with Grok AI reasoning.

## 🎯 Features

✅ **Image Upload**: Compare reference images with test images (any image format)  
✅ **PCA Analysis**: Client-side Principal Component Analysis in JavaScript  
✅ **Visualization**: 2x2 grid showing original images + first 2 PCA components  
✅ **Classification**: Binary real/fake detection with confidence scores & sensor metrics  
✅ **Grok Integration**: AI-powered security narrative using xAI's vision model  
✅ **No Backend Required**: All processing happens in the browser  
✅ **Responsive Design**: Works on desktop, tablet, mobile  
✅ **Production Ready**: Error handling, API validation, loading states  

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR-USERNAME/satellite-real-vs-ai-detector.git
cd satellite-real-vs-ai-detector
```

### 2. Deploy to Vercel (Recommended)

#### Option A: Via Vercel CLI
```bash
npm install -g vercel
vercel
```
Follow the prompts to connect your GitHub repo and deploy.

#### Option B: Via Vercel Dashboard
1. Go to [vercel.com/new](https://vercel.com/new)
2. Click "Import Git Repository"
3. Paste your GitHub repo URL
4. Click "Import"
5. Vercel will auto-detect it's a static site
6. Click "Deploy"

#### Option C: Direct GitHub Integration (Recommended)
1. Push this repo to GitHub
2. Visit [vercel.com/new](https://vercel.com/new)
3. Select your GitHub repository
4. Vercel auto-deploys on every push to main branch

### 3. Get Grok API Key

1. Visit [console.x.ai](https://console.x.ai/)
2. Sign up / log in with X (Twitter) account
3. Create API key
4. Copy the key (you'll paste it in the app)

### 4. Use the App

1. Open your deployed URL: `https://YOUR-PROJECT.vercel.app`
2. Paste Grok API key in the "API Configuration" section
3. Upload two images (reference + test image)
4. Click "Analyze Images"
5. Click "Get Grok Explanation" for AI security analysis

## 📁 Repository Structure

```
satellite-real-vs-ai-detector/
├── index.html                 # Main app (all-in-one file)
├── vercel.json               # Vercel static site config
├── package.json              # Project metadata
├── README.md                 # This file
├── DEPLOYMENT.md             # Detailed deployment guide
├── .gitignore                # Git ignore rules
└── docs/
    ├── ARCHITECTURE.md       # Technical architecture
    ├── PCA-EXPLANATION.md    # How PCA analysis works
    └── API-KEYS.md          # API setup guide
```

## 🔧 Local Development

### Option 1: Simple HTTP Server (Recommended)
```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server

# Or use any other HTTP server
```
Then visit `http://localhost:8000` in your browser.

### Option 2: VSCode Live Server
1. Install "Live Server" extension in VSCode
2. Right-click `index.html` → "Open with Live Server"
3. Browser opens at `http://127.0.0.1:5500`

## 📊 How It Works

### PCA Analysis
1. **Image Processing**: Converts uploaded images to grayscale patches
2. **Covariance Computation**: Calculates covariance matrix of patch vectors
3. **Eigenvector Extraction**: Finds first 2 principal components using power iteration
4. **Projection**: Projects patches onto component space
5. **Feature Extraction**: Computes sensor artifact metrics:
   - PC variance ratio (real images: coherent, AI images: scattered)
   - Spatial coherence (autocorrelation of PC1)
   - Noise level (high-frequency energy)

### Classification Logic
```
Real Images:
  ✓ Coherent PC components (structured sensor noise)
  ✓ Spatial correlations across components
  ✓ Moderate high-frequency energy

AI-Generated Images:
  ✗ Incoherent component variance
  ✗ Broken spatial correlations
  ✗ Excessive or missing noise patterns
```

### Grok Explanation
The app sends:
- Both images (as base64)
- Computed PCA metrics
- Classification result

Grok analyzes and provides:
- Real/fake assessment with reasoning
- Sensor artifact breakdown
- Security/military implications
- Confidence assessment

## 🔐 Security Notes

- **No data sent to servers** (except Grok API call with user consent)
- **API keys stored locally only** (not in code or git)
- **HTTPS recommended** for Vercel deployment (automatic)
- **No image storage** (processed in-memory, discarded after analysis)
- **Grok calls explicit** (user clicks "Get Explanation" button)

## 📋 System Requirements

- Modern browser with:
  - Canvas API support
  - FileReader API
  - Fetch API
  - ES6+ JavaScript support
  
Tested on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## 🛠️ Customization

### Modify PCA Parameters
Edit `index.html`, search for `patchSize = 8`:
```javascript
// Increase for faster processing, decrease for more detail
function imageToPatchVectors(imageData, patchSize = 8) { ... }
```

### Change Classification Threshold
Edit the scoring logic in `analyzeImages()`:
```javascript
const testScore = (testCoherence * 0.6 + (1 - Math.abs(...)) * 0.4);
const isReal = testScore > 0.5;  // Adjust threshold here
```

### Customize UI Colors
Edit CSS variables in `<style>` section:
```css
:root {
    --color-primary: var(--color-teal-500);
    --color-error: var(--color-red-500);
    /* ... etc ... */
}
```

## 📚 Documentation

- **[DEPLOYMENT.md](./DEPLOYMENT.md)** - Step-by-step Vercel + GitHub setup
- **[docs/ARCHITECTURE.md](./docs/ARCHITECTURE.md)** - Technical deep dive
- **[docs/PCA-EXPLANATION.md](./docs/PCA-EXPLANATION.md)** - PCA theory
- **[docs/API-KEYS.md](./docs/API-KEYS.md)** - Getting API keys

## 🤝 Contributing

1. Fork the repo
2. Create feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m 'Add feature'`
4. Push branch: `git push origin feature/your-feature`
5. Open Pull Request

## 📝 License

MIT License - see LICENSE file for details

## 🙋 Support

- **Issues**: Open a GitHub issue
- **Discussions**: Use GitHub Discussions
- **Grok API Help**: Visit [xAI docs](https://docs.x.ai)

## 🎓 Research References

- **PCA in Remote Sensing**: Turk & Pentland (1991) - Eigenfaces
- **Satellite Imagery Forensics**: Geo-DefakeHop (2021)
- **AI Image Detection**: ArXiv methods survey (2024)
- **Sensor Artifacts**: NASA USGS documentation

## 🚀 Next Steps

- [ ] Deploy to Vercel
- [ ] Get Grok API key from console.x.ai
- [ ] Test with sample satellite images
- [ ] Share feedback / report issues
- [ ] Star ⭐ if you find this useful!

---

**Built with ❤️ for environmental justice, security, and open science**

Questions? Open an issue or start a discussion!
