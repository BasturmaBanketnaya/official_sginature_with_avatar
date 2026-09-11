# SPREAD Email Signature Generator

A web-based email signature generator built specifically for SPREAD GmbH employees. This application creates professional, branded HTML email signatures that are compatible with Outlook and other email clients.

## Features

- **Interactive Form**: Simple form interface to input employee details
- **Photo Upload**: Upload any headshot; it is cropped to a centered square and resized in the browser, so the bitmap Outlook receives is already the right shape and size
- **HEIC support**: iPhone HEIC/HEIF photos are converted to JPEG in the browser (heic2any, loaded on demand) before cropping, so they no longer break the preview
- **Live Preview**: Real-time preview of the signature as you type
- **One-Click Copy**: Copy signature directly to clipboard in HTML format
- **Email-Optimized**: Uses inline styles and table-based layout for maximum email client compatibility
- **Brand Consistent**: Includes SPREAD logo and brand colors (orange accent: #FF6F47)
- **Embedded Icons**: SVG icons encoded as data URIs for reliable rendering
- **Responsive Design**: Clean, modern interface for creating signatures

## Technologies Used

- **React 19.1.1** - UI framework
- **Vite 7.1.7** - Build tool and development server
- **ESLint** - Code linting
- **CSS3** - Styling

## Installation

1. Clone the repository or navigate to the project directory:
```bash
cd official_signature
```

2. Install dependencies:
```bash
npm install
```

## Usage

### Development Mode

Start the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

### Build for Production

Create an optimized production build:
```bash
npm run build
```

Preview the production build:
```bash
npm run preview
```

### Linting

Run ESLint to check code quality:
```bash
npm run lint
```

## How to Use the Generator

1. **Upload Photo**: Click "Photo Upload" and select a professional headshot (any shape; the generator crops it to a centered square)
2. **Fill in Details**:
   - Full Name (e.g., "Constanze Hüppe")
   - Job Title (e.g., "Enterprise Lead")
   - Phone Number (e.g., "+49 151 55380231")
   - Email Address (e.g., "yourname@spread.ai")
3. **Preview**: Review your signature in real-time
4. **Copy**: Click "Copy Signature for Outlook" to copy the HTML to your clipboard

## Adding Signature to Outlook

### Outlook Desktop (Windows/Mac)

1. Open Outlook
2. Go to **File** > **Options** > **Mail** > **Signatures**
3. Click **New** to create a new signature
4. Name your signature
5. In the signature editor, press **Ctrl+V** (Windows) or **Cmd+V** (Mac) to paste
6. Click **OK** to save

### Outlook Web

1. Open Outlook on the web
2. Click the **Settings** gear icon > **View all Outlook settings**
3. Go to **Mail** > **Compose and reply**
4. Under **Email signature**, paste your signature with **Ctrl+V** or **Cmd+V**
5. Click **Save**

## Project Structure

```
official_signature/
├── src/
│   ├── App.jsx           # Main application component
│   ├── App.css           # Application styles
│   ├── main.jsx          # React entry point
│   ├── index.css         # Global styles
│   └── assets/
│       ├── Spread_Logo_Orange.png    # master logo (1842x396)
│       └── spread-logo-184x40.png    # signature logo, 2x display size, inlined as a data URI
├── public/               # Static assets
├── index.html            # HTML template
├── package.json          # Dependencies and scripts
├── vite.config.js        # Vite configuration
└── eslint.config.js      # ESLint configuration
```

## Signature Specifications

The generated signature includes:

- **Dimensions**: 600px × 200px
- **Layout**: Two-column table structure
- **Left Column**: Employee photo (100x100px, JPEG shipped at exactly 100x100) + SPREAD logo (92x20px JPEG data URI on the signature's white background; PNG and SVG data URIs were converted to blocked external images by new Outlook on send)
- **Right Column**: Employee details and company information
- **Accent Color**: Orange (#FF6F47)
- **Font**: DIN Pro (fallback: Arial)
- **Icons**: Phone, Email, LinkedIn (embedded as SVG data URIs)
- **Image sizing**: every `<img>` carries HTML `width`/`height` attributes plus the same CSS size, and every image file is exactly its display size. Outlook does not support `object-fit`, so the crop has to happen in the bitmap; and new Outlook / Outlook on the web strip `width`, `height` and `style` from pasted `<img>` tags, so the image then renders at its native pixel size, which is why the native size must equal the display size (a 2x photo rendered at 200px in new Outlook for Mac)
- **Company Info**: SPREAD GmbH address and legal details

## Customization

To customize the signature template, edit the signature table structure in [src/App.jsx](src/App.jsx) starting at line 156. Key areas you might want to modify:

- **Colors**: Change `#FF6F47` to your brand color
- **Dimensions**: Adjust width/height in the table styles
- **Company Info**: Update company address and legal text (lines 301-325)
- **Fonts**: Modify the `fontFamily` style properties
- **LinkedIn URL**: Update the link at line 279

## Browser Compatibility

The application works in all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari

Note: The clipboard copy feature requires a secure context (HTTPS or localhost).

## License

Private - SPREAD GmbH internal use only.

## Support

For issues or questions, contact the SPREAD IT team.
