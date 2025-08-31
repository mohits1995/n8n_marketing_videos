# 🎬 VideoCraft Studio

A modern, AI-powered marketing video generation platform that transforms your visual assets into professional marketing videos through an intuitive web interface.

![VideoCraft Studio](https://img.shields.io/badge/VideoCraft_Studio-React-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue)
![Tailwind](https://img.shields.io/badge/Tailwind-CSS-06B6D4)
![License](https://img.shields.io/badge/License-MIT-green)

## ✨ Features

### 🎯 Core Functionality
- **Drag & Drop File Upload** - Seamless upload for marketing assets (images, logos, graphics)
- **Intelligent Form Handling** - Comprehensive project brief with validation
- **Real-time Progress tracking** - Visual feedback during video generation
- **Video Preview & Download** - Instant preview of generated marketing videos
- **Responsive Design** - Works perfectly on desktop, tablet, and mobile devices

### 🎨 User Experience
- **Cinematic UI/UX** - Movie-industry inspired design with gradients and animations
- **Progressive Enhancement** - Multi-step workflow (form → processing → results)
- **Smart Validation** - Real-time form validation with helpful error messages
- **Toast Notifications** - User-friendly success and error notifications
- **Loading States** - Engaging progress indicators with contextual messages

### 🔧 Technical Features
- **File Type Validation** - Supports JPG, PNG, GIF, WebP (up to 25MB)
- **Webhook Integration** - Seamless connection to n8n automation workflows
- **Error Handling** - Robust error handling with fallback mechanisms
- **Type Safety** - Full TypeScript implementation
- **Performance Optimized** - Code splitting and optimized bundle size

## 🚀 Technology Stack

### Frontend Framework
- **React 18** - Modern React with hooks and functional components
- **TypeScript** - Full type safety and developer experience
- **Vite** - Lightning-fast build tool and development server

### Styling & Design
- **Tailwind CSS** - Utility-first CSS framework
- **Custom Design System** - Consistent theming with CSS variables
- **shadcn/ui** - High-quality, accessible UI components
- **Lucide Icons** - Beautiful, consistent iconography

### Form Management
- **React Hook Form** - Performant forms with easy validation
- **Zod Validation** - Runtime type checking and validation
- **React Dropzone** - Drag and drop file upload functionality

### Backend Integration
- **n8n Webhook** - Serverless video generation workflow
- **FormData API** - Multipart form submission for file uploads
- **Fetch API** - Modern HTTP client with error handling

## 📦 Installation & Setup

### Prerequisites
- Node.js 18.0.0 or higher
- npm or yarn package manager
- Modern web browser

### Quick Start

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd videocraft-studio
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Start development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. **Open in browser**
   Navigate to `http://localhost:8080`

### Build for Production

```bash
npm run build
# or
yarn build
```

The build artifacts will be stored in the `dist/` directory.

## 🔧 Configuration

### Webhook Configuration
The application connects to an n8n webhook for video processing. Update the webhook URL in:

```typescript
// src/components/ProductForm.tsx
const WEBHOOK_URL = "your-n8n-webhook-url-here";
```

### Environment Setup
For production deployments, consider using environment variables:

```env
VITE_WEBHOOK_URL=https://your-n8n-instance.com/webhook/your-webhook-id
```

## 🎯 Usage Guide

### For End Users

1. **Upload Assets** 📸
   - Drag and drop or click to upload marketing materials
   - Supported formats: JPG, PNG, GIF, WebP (max 25MB)
   - High-resolution images recommended for best results

2. **Fill Project Details** 📝
   - **Video Title**: Give your project a descriptive name
   - **Creative Brief**: Describe your vision, target audience, and requirements
   - **Email**: Receive notifications and final video delivery

3. **Generate Video** 🎬
   - Click "Launch Video Project" to start processing
   - Monitor real-time progress updates
   - Receive completion notification

4. **Preview & Download** 📥
   - Watch your generated video directly in the browser
   - Copy the video URL for sharing
   - Create additional videos with different assets

### For Developers

#### Component Structure
```
src/
├── components/
│   ├── ProductForm.tsx     # Main form component
│   ├── FileUpload.tsx      # Drag & drop file upload
│   └── ui/                 # shadcn/ui components
├── pages/
│   ├── Index.tsx           # Main page
│   └── NotFound.tsx        # 404 page
├── lib/
│   └── utils.ts            # Utility functions
└── hooks/
    └── use-toast.ts        # Toast notification hook
```

#### Key Functions
- `onSubmit()` - Handles form submission and API calls
- `simulateProgress()` - Manages loading progress simulation
- `resetForm()` - Clears form state for new submissions

## 🎨 Design System

### Color Palette
The application uses a custom design system with semantic color tokens:

```css
/* Cinematic Theme */
--primary: 299 100% 60%        /* Purple */
--accent-video: 265 100% 60%   /* Blue-purple */
--gradient-primary: linear-gradient(135deg, ...)
--gradient-cinema: radial-gradient(...)
```

### Components
- **Buttons**: Multiple variants (primary, outline, ghost)
- **Cards**: Glassmorphism effect with backdrop blur
- **Forms**: Consistent styling with focus states
- **Progress**: Animated progress bars with contextual colors

## 🔒 Security Considerations

### Input Validation
- File type and size restrictions
- Email format validation
- Required field validation
- XSS protection through React's built-in escaping

### API Security
- FormData for secure file transmission
- HTTPS enforcement for webhook calls
- Error message sanitization
- No sensitive data exposure in console logs (production)

## 🚀 Deployment

### Recommended Platforms
- **Vercel** - Optimal for React/Vite applications
- **Netlify** - Great for static site deployment
- **GitHub Pages** - Free hosting for public repositories

### Build Configuration
```json
{
  "scripts": {
    "build": "vite build",
    "preview": "vite preview"
  }
}
```

### Environment Variables
Set the following for production:
- `VITE_WEBHOOK_URL` - Your n8n webhook endpoint

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes and test thoroughly
4. Commit your changes: `git commit -m 'Add amazing feature'`
5. Push to the branch: `git push origin feature/amazing-feature`
6. Open a Pull Request

### Code Standards
- TypeScript for all new code
- Follow existing component patterns
- Use semantic commit messages
- Add JSDoc comments for complex functions
- Ensure responsive design compatibility

### Testing Checklist
- [ ] Form validation works correctly
- [ ] File upload handles edge cases
- [ ] Progress tracking displays properly
- [ ] Video preview functions correctly
- [ ] Error states are handled gracefully
- [ ] Mobile responsiveness verified

## 📚 API Documentation

### Webhook Payload
The application sends the following data to the n8n webhook:

```javascript
{
  file: File,                    // Uploaded image file
  videoTitle: string,            // Project title
  videoDescription: string,      // Creative brief
  email: string,                 // User email
  timestamp: string,             // ISO timestamp
  projectType: "marketing-video" // Fixed project type
}
```

### Expected Response Format
The webhook should return video URL in one of these formats:

```javascript
// Format 1: Simple array
["https://video-url.com/video.mp4"]

// Format 2: Nested object
{
  body: {
    body: ["https://video-url.com/video.mp4"]
  }
}

// Format 3: Legacy format
[{
  response: {
    body: ["https://video-url.com/video.mp4"]
  }
}]
```

## 🐛 Troubleshooting

### Common Issues

**File Upload Not Working**
- Check file size (max 25MB)
- Verify file format (JPG, PNG, GIF, WebP only)
- Ensure stable internet connection

**Video Generation Fails**
- Verify webhook URL is accessible
- Check n8n workflow is active
- Validate API response format

**Form Validation Errors**
- Email must be valid format
- All fields are required
- File must be uploaded before submission

### Debug Mode
Enable debug logging by checking the browser console for detailed error messages and API responses.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **shadcn/ui** for the beautiful component library
- **Lucide** for the comprehensive icon set
- **Tailwind CSS** for the utility-first styling approach
- **React Hook Form** for efficient form management
- **n8n** for workflow automation capabilities

## 📧 Support

For support, feature requests, or bug reports:
- Create an issue on GitHub
- Check existing documentation
- Review the troubleshooting section

---

**Built with ❤️ using React, TypeScript, and modern web technologies**

*Transform your marketing materials into professional videos with the power of AI and automation.*
