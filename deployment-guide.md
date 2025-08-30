# Text to PowerPoint Generator - Deployment Guide

## Overview

This web application allows users to convert bulk text, markdown, or prose into fully formatted PowerPoint presentations using their own templates and LLM APIs.

## Project Structure

```
text-to-powerpoint/
├── index.html              # Main application HTML
├── style.css               # Application styles
├── app.js                  # Core application logic
├── package.json            # Node.js dependencies
├── vercel.json            # Vercel deployment configuration
├── README.md              # Project documentation
├── LICENSE                # MIT License
└── docs/
    ├── setup.md           # Setup instructions
    └── api-guide.md       # API integration guide
```

## Step-by-Step Deployment Process

### 1. GitHub Repository Setup

Create a new GitHub repository and add these files:

**package.json**
```json
{
  "name": "text-to-powerpoint-generator",
  "version": "1.0.0",
  "description": "Convert text to PowerPoint presentations with custom templates",
  "main": "index.html",
  "scripts": {
    "dev": "serve .",
    "build": "echo 'Static files ready'",
    "start": "serve -s ."
  },
  "keywords": ["powerpoint", "pptx", "ai", "llm", "presentation"],
  "author": "Your Name",
  "license": "MIT",
  "devDependencies": {
    "serve": "^14.0.0"
  },
  "dependencies": {
    "pptxgenjs": "^3.12.0"
  }
}
```

**vercel.json**
```json
{
  "version": 2,
  "name": "text-to-powerpoint-generator",
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/$1"
    }
  ],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cross-Origin-Embedder-Policy",
          "value": "require-corp"
        },
        {
          "key": "Cross-Origin-Opener-Policy", 
          "value": "same-origin"
        }
      ]
    }
  ]
}
```

### 2. Vercel Deployment

#### Option A: Direct GitHub Integration
1. Go to [vercel.com](https://vercel.com)
2. Sign up/Login with your GitHub account
3. Click "New Project"
4. Select your GitHub repository
5. Configure settings:
   - Framework Preset: Other
   - Root Directory: ./
   - Build Command: `npm run build`
   - Output Directory: ./
6. Click "Deploy"

#### Option B: Vercel CLI
```bash
# Install Vercel CLI
npm i -g vercel

# Login to Vercel
vercel login

# Deploy from project directory
vercel --prod
```

### 3. GitHub Pages Deployment

**Add .github/workflows/deploy.yml**
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    permissions:
      contents: read
      pages: write
      id-token: write
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        
    - name: Install dependencies
      run: npm install
      
    - name: Build
      run: npm run build
      
    - name: Setup Pages
      uses: actions/configure-pages@v3
      
    - name: Upload artifact
      uses: actions/upload-pages-artifact@v2
      with:
        path: '.'
        
    - name: Deploy to GitHub Pages
      id: deployment
      uses: actions/deploy-pages@v2
```

### 4. Environment Configuration

Create `.env.example` file:
```env
# Example environment variables (not needed for client-side app)
# Users will enter their own API keys in the app
EXAMPLE_OPENAI_API_KEY=sk-your-key-here
EXAMPLE_ANTHROPIC_API_KEY=sk-ant-your-key-here
EXAMPLE_GEMINI_API_KEY=your-gemini-key-here
```

### 5. Security Considerations

**Important Security Notes:**
- API keys are handled client-side only
- No server-side storage of sensitive data
- All processing happens in the browser
- Template files are processed locally

## Local Development

### Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/text-to-powerpoint-generator.git
cd text-to-powerpoint-generator

# Install dependencies
npm install

# Start development server
npm run dev
```

### Testing
1. Open the application in a browser
2. Test with different LLM providers
3. Upload various PowerPoint templates
4. Verify generated presentations

## Features Implemented

### Core Functionality
- ✅ Text input with markdown support
- ✅ Multiple LLM provider support (OpenAI, Anthropic, Gemini)
- ✅ PowerPoint template upload and analysis
- ✅ Style extraction from templates
- ✅ Slide generation with template styling
- ✅ PPTX file download

### User Experience
- ✅ Drag-and-drop file upload
- ✅ Real-time input validation
- ✅ Progress indicators during generation
- ✅ Error handling and user feedback
- ✅ Responsive design
- ✅ Accessibility features

### Technical Features
- ✅ Client-side processing
- ✅ No server dependencies
- ✅ Secure API key handling
- ✅ File type validation
- ✅ Template style inheritance

## API Integration Details

### OpenAI Integration
```javascript
const callOpenAI = async (text, guidance, apiKey) => {
  const response = await fetch('https://api.openai.com/v1/chat/completions', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${apiKey}`
    },
    body: JSON.stringify({
      model: 'gpt-4',
      messages: [{
        role: 'user',
        content: `Convert this text into a structured presentation outline: ${text}. Guidance: ${guidance}`
      }],
      max_tokens: 2000
    })
  });
  return response.json();
};
```

### Template Processing
```javascript
const processTemplate = (templateFile) => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = (e) => {
      const arrayBuffer = e.target.result;
      // Extract styles, layouts, and theme information
      const templateData = analyzeTemplate(arrayBuffer);
      resolve(templateData);
    };
    reader.readAsArrayBuffer(templateFile);
  });
};
```

## Deployment URLs

After deployment, your application will be available at:
- **Vercel**: `https://your-project-name.vercel.app`
- **GitHub Pages**: `https://username.github.io/repository-name`

## Troubleshooting

### Common Issues
1. **CORS Errors**: Ensure proper headers are set in vercel.json
2. **API Key Issues**: Check API key format and permissions
3. **File Upload Errors**: Verify file size limits and MIME types
4. **Template Processing**: Ensure uploaded files are valid PPTX/POTX

### Browser Compatibility
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## License

MIT License - see LICENSE file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## Support

For issues and questions:
- GitHub Issues: Create an issue in the repository
- Documentation: Check the docs/ folder
- Examples: See the demo data in the application