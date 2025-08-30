# Text to PowerPoint Generator

![Text to PowerPoint Generator](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![JavaScript](https://img.shields.io/badge/javascript-ES6+-yellow)

A powerful web application that converts bulk text, markdown, or prose into fully formatted PowerPoint presentations using custom templates and AI language models.

## 🚀 Live Demo

- **Vercel**: [https://text-to-powerpoint.vercel.app](https://text-to-powerpoint.vercel.app)
- **GitHub Pages**: [https://yourusername.github.io/text-to-powerpoint](https://yourusername.github.io/text-to-powerpoint)

## ✨ Features

### 🎯 Core Functionality
- **Text-to-Slides Conversion**: Transform any text or markdown into structured presentation slides
- **Custom Template Support**: Upload your own PowerPoint templates (.pptx/.potx) to maintain brand consistency
- **Multi-LLM Integration**: Supports OpenAI GPT, Anthropic Claude, and Google Gemini APIs
- **Style Preservation**: Automatically extracts and applies colors, fonts, and layouts from your templates
- **Smart Content Analysis**: AI-powered text breakdown optimized for presentation format

### 💡 User Experience
- **Drag-and-Drop Interface**: Easy template upload with visual feedback
- **Real-time Processing**: Live progress indicators during generation
- **Responsive Design**: Works seamlessly on desktop and tablet devices
- **Error Handling**: Clear, actionable error messages and recovery options
- **No Account Required**: Pure client-side processing with no data storage

### 🛡️ Security & Privacy
- **Client-Side Processing**: All operations happen in your browser
- **Secure API Handling**: API keys never leave your device
- **No Data Storage**: Templates and content are processed locally only
- **HTTPS Support**: Encrypted communication with AI providers

## 🛠️ How It Works

1. **Input Your Content**: Paste your text, markdown, or long-form prose
2. **Configure AI Provider**: Select your preferred LLM (OpenAI, Anthropic, or Gemini) and enter your API key
3. **Upload Template**: Drag and drop your PowerPoint template file
4. **Generate**: AI analyzes your text and creates structured slide content
5. **Download**: Get your professionally formatted .pptx file

## 📋 Requirements

### For Users
- Modern web browser (Chrome 80+, Firefox 75+, Safari 13+, Edge 80+)
- API key from one of the supported providers:
  - [OpenAI API Key](https://platform.openai.com/api-keys)
  - [Anthropic API Key](https://console.anthropic.com/)
  - [Google AI API Key](https://makersuite.google.com/app/apikey)
- PowerPoint template file (.pptx or .potx format)

### For Developers
- Node.js 16+ (for local development)
- Modern code editor
- Git for version control

## 🚀 Quick Start

### Option 1: Use the Live Version
Simply visit the [live demo](https://text-to-powerpoint.vercel.app) and start creating presentations immediately.

### Option 2: Run Locally
```bash
# Clone the repository
git clone https://github.com/yourusername/text-to-powerpoint-generator.git
cd text-to-powerpoint-generator

# Install dependencies
npm install

# Start development server
npm run dev

# Open http://localhost:3000 in your browser
```

### Option 3: Deploy Your Own

#### Deploy to Vercel (Recommended)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/yourusername/text-to-powerpoint-generator)

#### Deploy to GitHub Pages
1. Fork this repository
2. Go to repository Settings > Pages
3. Set source to "Deploy from a branch"
4. Select "main" branch and "/ (root)" folder
5. Your site will be available at `https://yourusername.github.io/text-to-powerpoint-generator`

## 📖 Usage Guide

### Step 1: Prepare Your Content
```markdown
# Company Overview
Our innovative platform revolutionizes data processing with 75% faster speeds.

## Key Benefits
- Reduced processing time
- Improved accuracy by 40%
- Cost-effective solution

## Market Opportunity
Target market includes mid-size tech companies and enterprises.
```

### Step 2: Set Up AI Provider
1. Choose your preferred LLM provider
2. Enter your API key (stored locally only)
3. Test the connection

### Step 3: Upload Template
- Drag and drop your .pptx template file
- System analyzes layouts, colors, and fonts
- Preview detected template elements

### Step 4: Configure Generation
- Set maximum number of slides (5-20)
- Choose presentation style
- Add optional guidance (e.g., "investor pitch deck")

### Step 5: Generate and Download
- Click "Generate Presentation"
- Watch real-time progress
- Download your formatted .pptx file

## 🏗️ Technical Architecture

### Frontend Stack
- **HTML5**: Semantic structure and accessibility
- **CSS3**: Modern styling with CSS Grid and Flexbox
- **JavaScript (ES6+)**: Core application logic
- **File API**: Client-side file processing
- **Fetch API**: HTTP requests to LLM providers

### Key Libraries
- **PptxGenJS**: PowerPoint generation in JavaScript
- **JSZip**: Template file processing
- **File API**: Browser file handling

### API Integration
```javascript
// OpenAI Example
const response = await fetch('https://api.openai.com/v1/chat/completions', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${apiKey}`
  },
  body: JSON.stringify({
    model: 'gpt-4',
    messages: [{ role: 'user', content: prompt }],
    max_tokens: 2000
  })
});
```

## 🎨 Customization

### Supported Template Elements
- **Slide Layouts**: Title slides, content slides, section dividers
- **Typography**: Font families, sizes, and styles
- **Colors**: Theme colors, accent colors, backgrounds
- **Images**: Logo placement and background images
- **Shapes**: Geometric elements and design components

### Style Options
- **Professional**: Clean, business-focused design
- **Creative**: Colorful, modern layouts
- **Technical**: Data-heavy, detailed presentations
- **Minimal**: Simple, text-focused slides
- **Academic**: Research and educational content

## 📊 Examples

### Business Pitch Deck
Input a company overview, and get slides for:
- Title slide with company name
- Problem statement
- Solution overview
- Market opportunity
- Business model
- Financial projections
- Team introduction
- Call to action

### Project Status Report
Transform project updates into:
- Executive summary
- Progress overview
- Key achievements
- Challenges and solutions
- Timeline and milestones
- Next steps
- Resource requirements

## 🐛 Troubleshooting

### Common Issues

**Q: My API key doesn't work**
- Verify the key format matches your provider
- Check API key permissions and rate limits
- Ensure you have sufficient credits/quota

**Q: Template upload fails**
- Confirm file is .pptx or .potx format
- Check file size (max 10MB)
- Try re-saving template from PowerPoint

**Q: Generated slides look incorrect**
- Verify template has proper master slides
- Check for complex animations or unsupported elements
- Try with a simpler template design

**Q: Browser compatibility issues**
- Update to latest browser version
- Enable JavaScript
- Check for browser extensions blocking content

## 🤝 Contributing

We welcome contributions! Here's how to get started:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make your changes**
   - Follow existing code style
   - Add comments for complex logic
   - Test your changes thoroughly

4. **Commit your changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```

5. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```

6. **Open a Pull Request**

### Development Guidelines
- Use semantic HTML and ARIA labels
- Follow responsive design principles
- Add error handling for all user interactions
- Test with multiple browsers and devices

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **PptxGenJS** for PowerPoint generation capabilities
- **OpenAI, Anthropic, Google** for AI language model APIs
- **Vercel** for hosting and deployment platform
- **GitHub Pages** for static site hosting
- The open-source community for inspiration and tools

## 📞 Support

- 📧 **Email**: support@your-domain.com
- 🐛 **Issues**: [GitHub Issues](https://github.com/yourusername/text-to-powerpoint-generator/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/yourusername/text-to-powerpoint-generator/discussions)
- 📖 **Documentation**: [Wiki](https://github.com/yourusername/text-to-powerpoint-generator/wiki)

## 🗺️ Roadmap

### Version 1.1 (Coming Soon)
- [ ] Speaker notes generation
- [ ] Multi-language support
- [ ] Template marketplace
- [ ] Batch processing

### Version 1.2 (Future)
- [ ] Real-time collaboration
- [ ] Advanced template editor
- [ ] Integration with Google Slides
- [ ] Mobile app version

---

**Made with ❤️ by developers who believe presentations shouldn't be painful**

[![GitHub stars](https://img.shields.io/github/stars/yourusername/text-to-powerpoint-generator)](https://github.com/yourusername/text-to-powerpoint-generator/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/yourusername/text-to-powerpoint-generator)](https://github.com/yourusername/text-to-powerpoint-generator/network)
[![GitHub issues](https://img.shields.io/github/issues/yourusername/text-to-powerpoint-generator)](https://github.com/yourusername/text-to-powerpoint-generator/issues)
