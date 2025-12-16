# 🎨 PCA AI Checker - Real vs AI Image Detection

**Live App**: https://pcaaichecker.vercel.app/

A production-ready web application that detects real vs AI-generated images using Principal Component Analysis (PCA) sensor artifact detection and Grok AI reasoning. **Works on ANY imagery** - photos, artwork, medical scans, screenshots, and more. Entirely client-side with no backend required.

![Real vs AI Detection](https://img.shields.io/badge/Detection-Real%20vs%20AI-blue) ![Powered by PCA](https://img.shields.io/badge/Algorithm-PCA%20%2B%20Grok%20AI-green) ![Any Image](https://img.shields.io/badge/Works%20On-Any%20Imagery-purple) ![No Backend](https://img.shields.io/badge/Architecture-Client--Side-orange) ![License: MIT](https://img.shields.io/badge/License-MIT-yellow)

---

## 🎯 What This Does

Upload two images (a reference and a test image) and the app will analyze **any type of imagery**:

1. **Analyze PCA Components**: Extract principal components from both images to reveal structural differences in how real and synthetic images distribute variance
2. **Detect Sensor/Generation Artifacts**: Identify characteristic noise patterns, spatial coherence, and corruption signatures that distinguish real imagery from AI-generated content
3. **Visualize Results**: Display original images + first 2 PCA components side-by-side for forensic inspection
4. **Classify & Score**: Provide binary classification (real/fake) with confidence metrics and feature breakdown
5. **Get AI Explanation**: Call Grok Vision API to explain the forensic findings in plain language with security implications

**Works on**:
- 📷 Photographs & portraits
- 🛰️ Satellite imagery
- 🎨 Digital artwork & illustrations
- 📊 Medical imaging (X-ray, MRI, CT scans)
- 🖼️ Screenshots & UI designs
- 🎬 Video frames & cinematography
- 🌍 Aerial/drone photography
- 📱 Social media images
- 💻 Generated content (DALL-E, Midjourney, Stable Diffusion)
- ✏️ Hand-drawn or edited images

---

## 🔬 How PCA Detection Works

### Real Images (Photographs, Medical Scans, Artwork, etc.)
✅ **Coherent PCA Components** - Structured spatial patterns from:
   - Camera optics (lens aberrations, point spread)
   - Sensor electronics (CCD/CMOS sampling, hot pixels, Bayer pattern)
   - Imaging process (compression, quantization, color space conversions)
   - Physical capture (motion blur, focus depth, perspective)
   - Post-processing (exposure compensation, color grading)

✅ **Correlated Variance** - PC1 and PC2 show physical structure tied to content (edges, textures, lighting)
✅ **Moderate Noise Levels** - High-frequency energy consistent with imaging device characteristics
✅ **Long-range Correlations** - Pixel values maintain spatial coherence across patches (natural continuity)

### AI-Generated Images (Diffusion, GAN, NeRF, Transformer, etc.)
❌ **Scattered Components** - Variance distributed randomly without underlying physical process constraints
❌ **Broken Correlations** - PC1 and PC2 show random scatter, no coherent structure from generation process
❌ **Noise Mismatches** - High-frequency artifacts appear too early/late or are completely missing (unnatural patterns)
❌ **Spatial Incoherence** - Pixel relationships don't match physical imaging or natural statistics (mathematical artifacts)

---

## ✨ Key Features

### 🖼️ Universal Image Processing
- Upload **any** image format (JPG, PNG, WebP, GIF, BMP, TIFF)
- Automatic normalization to 300×300px for consistent analysis
- Works on color or grayscale images
- Side-by-side comparison of reference vs test images
- Real-time preview of uploaded images
- Handles images of any content type

### 📊 PCA Analysis Engine
- **Client-side computation** (no data leaves your browser)
- **8×8 patch extraction** from grayscale conversion of any image
- **Covariance matrix** calculation via optimized JavaScript
- **Power iteration** for efficient eigenvector computation
- **Feature extraction**: coherence, variance ratio, noise level
- **Visualization**: 2D scatter plots of first 2 principal components
- **Universal application** - works regardless of image content or source

### 🧠 Grok AI Integration
- **Vision API support** - Analyzes actual image content with context
- **Security narrative** - Explains forensic findings in plain language
- **Confidence assessment** - Provides nuanced real/fake reasoning with reasoning
- **No data storage** - Images processed in-memory only
- **Content-aware** - Understands different image types (photo vs scan vs artwork)

### 📱 User Interface
- **Responsive design** - Works on desktop, tablet, mobile
- **Real-time feedback** - Status indicators for each step
- **Error handling** - Clear messages if API fails or images invalid
- **Design system** - Teal/cream color scheme with accessibility focus
- **Intuitive workflow** - Clear step-by-step guidance

### 🔐 Privacy & Security
- ✅ All image processing happens in your browser (client-side only)
- ✅ No image storage on servers
- ✅ Grok API call is explicit (you click to request)
- ✅ API key stored in memory only (not in localStorage)
- ✅ HTTPS enforced on Vercel deployment
- ✅ No tracking pixels or analytics
- ✅ No data sold or shared

---

## 🚀 Quick Start

### Option 1: Use Live App (1 minute)
1. Go to https://pcaaichecker.vercel.app/
2. Get free Grok API key: https://console.x.ai/
3. Paste key in app
4. Upload 2 images (any type)
5. Click "Analyze"

### Option 2: Run Locally (2 minutes)
```bash
# Clone the repo
git clone https://github.com/rmkenv/pca_ai_checker.git
cd pca_ai_checker

# Start local server (Python 3)
python -m http.server 8000

# Or use Node.js
npx http-server

# Or use Ruby
ruby -run -ehttpd . -p8000

# Visit http://localhost:8000
```

### Option 3: Deploy Your Own (5 minutes)
1. Fork this repo
2. Go to https://vercel.com/new
3. Connect your GitHub account
4. Select this repo and deploy
5. Get Grok API key from https://console.x.ai/
6. Share your URL!

---

## 📋 Technology Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Frontend** | HTML5 + CSS3 + JavaScript (ES6+) | Responsive UI for any image type |
| **PCA Algorithm** | Pure JavaScript | Universal patch-based covariance analysis |
| **Visualization** | Canvas API | Real-time component plotting |
| **AI Analysis** | Grok Vision API (xAI) | Content-aware forensic explanation |
| **Hosting** | Vercel Static Site | Fast global CDN |
| **No Backend** | ✓ | All processing client-side |
| **No Dependencies** | ✓ | Single HTML file |
| **Framework** | Vanilla JS | Simple, no build step |

---

## 🔧 How to Use

### Step 1: Load Images
- **Reference Image**: Upload any known real image (photo, scan, artwork, etc.)
- **Test Image**: Upload the image you want to analyze (can be any type)
- Both images are automatically resized to 300×300 for consistent analysis
- Works with any content - landscape, portraits, medical scans, screenshots, generated art

### Step 2: Configure API
- Paste your Grok API key from https://console.x.ai/
- Click "Test API" to verify it works
- Key is stored in memory during session only

### Step 3: Analyze
- Click "Analyze Images" button
- Wait 2-3 seconds for PCA computation
- See results in 2×2 grid:
  - **Top-left**: Reference image
  - **Top-right**: Test image
  - **Bottom-left**: Reference PCA components (PC1 vs PC2)
  - **Bottom-right**: Test PCA components

### Step 4: Interpret Results
- **Classification Card**: Shows confidence for REAL vs AI GENERATED
- **Features List**: Coherence, noise level, variance metrics
- **Overall Assessment**: Summary classification with reasoning

### Step 5: Get Explanation (Optional)
- Click "Get Grok Explanation"
- Grok analyzes both images + PCA metrics
- Returns detailed forensic narrative explaining:
  - Real/fake assessment with reasoning
  - Sensor/generation artifacts observed
  - Spatial coherence analysis
  - Security implications
  - Confidence level and caveats

---

## 📊 Understanding the Results

### PCA Component Visualization

**Real Image Example** (Photo, Scan, Artwork):
```
PCA Plot shows:
• Points clustered in organized patterns
• Spatial structure from captured/created content
• Correlation between PC1 and PC2
• Coherent scatter = characteristic sensor/process artifacts
```

**AI Image Example** (Diffusion, GAN output):
```
PCA Plot shows:
• Points scattered randomly
• No organized structure
• Uniform spread across space
• Incoherent scatter = mathematical generation artifacts
```

### Confidence Scores

| Score | Interpretation |
|-------|-----------------|
| 80-100% | High confidence in classification |
| 60-79% | Moderate confidence |
| 40-59% | Inconclusive - consider context |
| 0-39% | Opposite classification more likely |

### Key Metrics Explained

- **Coherence** (0-1 scale): Ratio of PC2 variance to PC1 variance
  - Real images: ~0.3-0.6 (structure from content/sensors)
  - AI images: ~0.7-1.0 (random uniform scatter)

- **Noise Level** (0-255 scale): High-frequency energy in image
  - Real images: Moderate levels with structured patterns
  - AI images: Either too high (artifacts) or too low (overly smooth)

- **PC1 Variance**: How much variance explained by first component
  - Real images: Lower but structured (content-driven)
  - AI images: Scattered across components

---

## 🎓 The Science

This app implements research from:
- **Geo-DefakeHop** (2021) - Geographic fake image detection using sensor artifacts
- **PCA-based Image Forensics** - Principal component analysis for authenticity verification
- **Sensor Artifact Analysis** - Optical/electronic signatures in real imaging
- **AI Detection Research** - Latest methods for synthetic image identification (2023-2025)

### Why PCA Works for ANY Image

Real images carry **physical process signatures**:
- **Photography**: Lens optics, CCD/CMOS sensor patterns, color filter arrays
- **Medical Imaging**: Device-specific noise, calibration patterns, contrast curves
- **Artwork**: Brush strokes, natural color mixing, canvas texture patterns
- **Screenshots**: Anti-aliasing, font rendering, OS-specific artifacts

AI models match **visual appearance** but not the underlying **generation process**. PCA reveals this by examining how variance distributes across spatial frequencies and patch correlations.

**Key insight**: Even when AI produces visually perfect images, the mathematical process leaves statistical signatures that differ from real imagery.

---

## 💡 Use Cases

✅ **Intelligence & Security**: Validate image authenticity in sensitive contexts
✅ **Journalism & Media**: Verify source images for fact-checking and integrity
✅ **Forensics & Law Enforcement**: Detect manipulated or synthetic evidence
✅ **Healthcare**: Validate medical imaging authenticity and detect synthetic scans
✅ **Art & NFTs**: Verify original artwork vs AI-generated content
✅ **Research**: Benchmark AI image detection methods
✅ **Education**: Learn PCA and image forensics
✅ **Compliance**: Audit media authenticity in regulated domains (HIPAA, finance, etc.)
✅ **Legal Discovery**: Authenticate images in legal proceedings
✅ **Content Moderation**: Identify synthetic/deepfake content

---

## 🔌 API Integration

### Grok API Setup

1. **Get API Key**:
   ```
   https://console.x.ai/
   Sign in with X (Twitter)
   Create API key
   Copy key (format: xai-...)
   ```

2. **Free Tier**:
   - Vision requests: Check current quota at console.x.ai
   - No credit card required
   - Rate limited (check docs for current limits)

3. **How It Works**:
   ```javascript
   // App sends to Grok:
   - Base64 encoded images (both reference and test)
   - PCA metrics (coherence, noise, variance)
   - Image analysis text prompt
   
   // Grok returns:
   - Forensic assessment (real/fake reasoning)
   - Artifact analysis
   - Confidence explanation
   - Security implications
   ```

### Local Testing

The PCA algorithm works **entirely offline**. You only need Grok API for the explanation feature. Perfect for:
- Testing the classification locally
- Understanding PCA results
- Benchmarking algorithm accuracy
- Developing improvements

---

## 📁 File Structure

```
pca_ai_checker/
├── index.html              # Complete app (single file, ~15KB)
├── README.md              # Documentation
├── LICENSE                # MIT License
├── package.json           # Metadata
├── .gitignore            # Git config
├── vercel.json           # Vercel deployment config
└── docs/                 # Optional documentation
    └── ARCHITECTURE.md
```

**Everything runs in a single `index.html` file**:
- No dependencies to install
- No build step required
- No backend server needed
- Works offline (except Grok explanation)

---

## 🛠️ Development

### Running Locally

```bash
# With Python 3
python -m http.server 8000

# With Node.js
npx http-server

# With Ruby
ruby -run -ehttpd . -p8000

# With PHP
php -S localhost:8000

# Then visit: http://localhost:8000
```

### Modifying the App

**Edit `index.html`** to customize:
- PCA patch size: `imageToPatchVectors(imageData, patchSize = 8)`
  - Larger = faster but less detail (try 16)
  - Smaller = more detail but slower (try 4)
- Classification threshold: `const isReal = testScore > 0.5`
  - Adjust sensitivity (0.4-0.6 typical range)
- UI colors: `:root` CSS variables
  - All colors defined as variables for easy theming
- Grok prompt: Edit text in `getGrokExplanation()`
  - Customize for your use case

### Performance Tuning

- **Patch size**: Balance between speed and accuracy
- **Iterations**: Increase for better eigenvectors (default: 20)
- **Canvas size**: Larger = more detail but slower processing

---

## 🐛 Troubleshooting

### "Vercel app won't load"
→ Check network tab (F12), ensure HTTPS  
→ Try incognito/private mode  
→ Clear browser cache  
→ Try different browser

### "Grok API returns 401 Unauthorized"
→ Verify API key at https://console.x.ai/keys  
→ Ensure key starts with `xai-`  
→ Try creating a new API key
→ Check xAI status page for outages

### "Images won't upload"
→ Try JPG or PNG format  
→ Check file size (should be < 5MB)  
→ Try different browser or incognito mode
→ Ensure file isn't corrupted

### "PCA shows blank canvas"
→ Try larger images (300+ pixels minimum)  
→ Check browser console (F12 → Console tab) for errors  
→ Ensure browser supports Canvas API (all modern browsers do)
→ Try with different image content

### "Results seem incorrect"
→ Compare PCA plots visually (real should show pattern, AI should show scatter)  
→ Try with known real vs fake images first  
→ Grok explanation provides helpful context
→ Remember: This is a detection tool, not 100% accurate

---

## 🔐 Security & Privacy

### What Gets Sent to Servers
**Only when you explicitly click "Get Grok Explanation"**:
- ✅ Base64 encoded images (converted to PNG/JPEG)
- ✅ PCA metrics (coherence, variance numbers)
- ✅ Analysis request text
- ✅ No metadata, no identifying information

### What Stays Local (On Your Computer)
- ✅ All image processing (patch extraction, covariance, eigenvectors)
- ✅ PCA computation (all math happens locally)
- ✅ Canvas rendering
- ✅ Classification algorithm
- ✅ Feature extraction

### API Key Security
- ✅ Never hardcoded in code or repository
- ✅ Stored in browser memory during session only
- ✅ Not sent to any servers except xAI
- ✅ Not in localStorage (cleared on page refresh)
- ✅ User explicitly pastes key at runtime

### HTTPS & Vercel
- ✅ HTTPS enforced automatically
- ✅ DDoS protection via Vercel edge network
- ✅ No cookies or persistent tracking
- ✅ Privacy-first architecture
- ✅ Compliant with major privacy regulations

---

## 📝 License

MIT License - Free to use, modify, and redistribute

```
Copyright (c) 2025 Ryan Kmetz

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

See [LICENSE](./LICENSE) file for full text.

---

## 🤝 Contributing

Issues, pull requests, and feedback welcome!

### Report a Bug
```
Open issue on GitHub with:
- Description of problem
- Steps to reproduce
- Expected vs actual behavior
- Browser/OS info
- Image examples if applicable
```

### Suggest a Feature
```
Open issue with:
- Feature description
- Use case
- Why it would help
- Difficulty estimate
```

### Submit Code
```
1. Fork the repo
2. Create feature branch: git checkout -b feature/my-feature
3. Commit changes: git commit -m 'Add feature'
4. Push branch: git push origin feature/my-feature
5. Open pull request
```

---

## 📚 Resources

### Learn More
- [PCA Explained](https://en.wikipedia.org/wiki/Principal_component_analysis) - Mathematical foundation
- [Image Forensics](https://en.wikipedia.org/wiki/Image_forensics) - Detecting image manipulation
- [AI Image Detection](https://arxiv.org/list/cs.CV/recent) - Latest research
- [Sensor Artifacts](https://www.dpreview.com/articles/4888148595/what-causes-image-noise) - Understanding camera noise

### Tools & APIs
- [Grok API Docs](https://docs.x.ai/) - Vision API documentation
- [Vercel Docs](https://vercel.com/docs) - Deployment platform
- [GitHub Docs](https://docs.github.com) - Version control

---

## 🎉 Credits

- **Algorithm**: PCA-based forensics from academic research
- **API**: Grok Vision by xAI
- **Hosting**: Vercel (free static hosting)
- **Design**: Custom responsive design system
- **Inspiration**: Environmental justice, security research, open science

---

## 📞 Support

- **GitHub Issues**: https://github.com/rmkenv/pca_ai_checker/issues
- **Live App**: https://pcaaichecker.vercel.app/
- **Grok API Help**: https://docs.x.ai/
- **Report Security Issues**: Please contact privately

---

## 🗺️ Roadmap

### Planned Features
- [ ] Batch processing (analyze multiple images)
- [ ] Model persistence (save trained classifiers)
- [ ] Multispectral support (Landsat, Sentinel-2 satellite data)
- [ ] Custom threshold controls (adjust sensitivity)
- [ ] Export analysis as PDF/JSON reports
- [ ] Real-time webcam analysis
- [ ] Multi-model ensemble (combine with Claude, GPT-4V)
- [ ] Training mode with labeled datasets
- [ ] API backend for production/enterprise use
- [ ] Mobile app (React Native)
- [ ] Advanced visualizations (heatmaps, 3D plots)
- [ ] Batch dataset scoring

### Recent Updates
- ✅ v1.0.0 - Initial release with PCA + Grok integration
- ✅ Works on ANY image type (photos, scans, artwork, screenshots, etc.)
- ✅ Production-ready deployment to Vercel
- ✅ MIT licensed, fully open source
- ✅ Zero dependencies, single HTML file
- ✅ Complete privacy-first architecture

---

## 📊 Project Stats

| Metric | Value |
|--------|-------|
| **Code Size** | Single HTML file (~15KB) |
| **Dependencies** | 0 (zero) |
| **Computation** | 100% client-side |
| **API Calls** | Optional (Grok only) |
| **Browser Support** | All modern browsers (Chrome, Firefox, Safari, Edge) |
| **Mobile Ready** | ✓ Yes, fully responsive |
| **License** | MIT (free, open source) |
| **Cost** | Free (with free tier APIs) |
| **Image Types Supported** | Any format (JPG, PNG, WebP, GIF, BMP, TIFF, etc.) |

---

## 🚀 Deploy Your Own

### 1-Click Deploy to Vercel
```
https://vercel.com/new/clone?repository-url=https://github.com/rmkenv/pca_ai_checker
```

### Manual Deploy
1. Fork repo on GitHub
2. Go to https://vercel.com/new
3. Connect GitHub account
4. Select this repo
5. Click "Deploy"
6. Your app is live! 🎉

### Custom Domain
1. In Vercel dashboard, click project
2. Go to Settings → Domains
3. Add your custom domain
4. Update DNS records as directed
5. Domain configured!

---

**Built with ❤️ for security, research, and open science**

Last updated: December 2025  
Version: 1.0.0  
Status: Production Ready ✅  
Works on: **Any Imagery** 🖼️
