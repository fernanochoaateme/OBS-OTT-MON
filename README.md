# 📺 OTT Multi-Channel Player

A professional web-based OTT player for monitoring 16 video channels simultaneously with support for both HLS and DASH streaming protocols.

![OTT Player](https://img.shields.io/badge/Channels-16-blue) ![HLS](https://img.shields.io/badge/Protocol-HLS-green) ![DASH](https://img.shields.io/badge/Protocol-DASH-orange)

## Features

- **16 Simultaneous Streams**: Monitor all channels in a responsive 4x4 grid
- **Dual Protocol Support**: Switch between HLS and DASH with one click
- **Editable Configuration**: Customize channel URLs through the UI
- **Auto-Retry**: Automatic reconnection on stream failures
- **Persistent Settings**: Configuration saved to localStorage
- **Keyboard Shortcuts**: Quick access to common functions
- **Modern UI**: Dark theme with glassmorphism effects
- **Responsive Design**: Adapts to any screen size

## Quick Start

> [!IMPORTANT]
> **You must run a local web server** to avoid CORS (Cross-Origin Resource Sharing) restrictions. Opening the HTML file directly (`file://`) will cause playback errors.

### Method 1: Python HTTP Server (Recommended)

1. **Start the server**:
   ```bash
   cd "/Users/fernanochoaamador/Documents/OBS Player"
   python3 -m http.server 8080
   ```

2. **Open in browser**:
   - Navigate to: `http://localhost:8080/index.html`

3. **Select your protocol**: Click **HLS** or **DASH** in the header.

4. **Monitor your channels**: All 16 streams will load automatically.

### Method 2: Alternative Servers

**Using PHP:**
```bash
php -S localhost:8080
```

**Using Node.js (if installed):**
```bash
npx http-server -p 8080
```

## Channel Configuration

### Default Channels

The application comes pre-configured with 16 channels:

- **Channel 01-16**: `debug-video.ovpobs.tv/live/ch{XX}`
- **HLS URLs**: `https://debug-video.ovpobs.tv/live/ch{XX}/hlsclear/index.m3u8`
- **DASH URLs**: `http://debug-video.ovpobs.tv/live/ch{XX}/dashclear/Manifest.mpd`

### Editing URLs

1. Click the **Configure** button (⚙️)
2. Edit any channel's HLS or DASH URL
3. Click **Save Changes** (💾)
4. Streams will reload automatically

## Controls

### Header Controls

- **HLS / DASH**: Switch streaming protocol
- **🔇 Mute All**: Toggle audio for all channels
- **⏸️ Stop All**: Pause/play all streams
- **🔄 Reload All**: Refresh all streams
- **⚙️ Configure**: Show/hide configuration panel

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `M` | Mute/Unmute all channels |
| `S` | Stop/Play all channels |
| `R` | Reload all channels |
| `C` | Toggle configuration panel |
| `H` | Switch to HLS protocol |
| `D` | Switch to DASH protocol |

### Individual Player Controls

Each video player includes:
- Play/Pause button
- Volume control
- Fullscreen mode
- Playback controls

## Technical Details

### Files

- `index.html` - Main application structure
- `style.css` - Styling and responsive layout
- `config.js` - Channel configuration
- `main.js` - Application logic

### Dependencies (CDN)

- [Video.js 8.10.0](https://videojs.com/)
- [DASH.js](https://github.com/Dash-Industry-Forum/dash.js)
- [videojs-contrib-dash 5.1.1](https://github.com/videojs/videojs-contrib-dash)
- [Inter Font](https://fonts.google.com/specimen/Inter)

### Browser Support

- ✅ Chrome/Edge (recommended)
- ✅ Firefox
- ✅ Safari (native HLS support)

## Status Indicators

Each channel displays a colored status indicator:

- 🟢 **Green**: Stream playing successfully
- 🟠 **Orange**: Loading/buffering
- 🔴 **Red**: Error or disconnected

## Responsive Breakpoints

- **Large screens (1600px+)**: 4 columns
- **Medium screens (1200-1600px)**: 3 columns
- **Tablets (768-1200px)**: 2 columns
- **Mobile (<768px)**: 1 column

## Troubleshooting

### CORS Error / "Media could not be loaded"

**Issue**: Error message "The media could not be loaded, either because the server or network failed or because the format is not supported."

**Cause**: Opening `index.html` directly with `file://` protocol triggers browser CORS restrictions.

**Solution**: 
- **Always run a local web server** (see Quick Start above)
- Use `python3 -m http.server 8080` and access via `http://localhost:8080/index.html`
- Never open the file directly by double-clicking

### Video players not loading

**Issue**: Black screens with no playback

**Solution**: 
- Ensure you have an active internet connection
- Check browser console for CDN loading errors
- Verify stream URLs are accessible
- Try switching protocols (HLS ↔ DASH)

### Streams showing errors

**Issue**: Red status indicators

**Solution**:
- The app auto-retries after 5 seconds
- Check if the stream URLs are correct
- Verify the streaming server is online
- Try the alternate protocol

### Configuration not saving

**Issue**: Changes reset on page reload

**Solution**:
- Ensure localStorage is enabled in your browser
- Check browser privacy settings
- Try a different browser

## Customization

### Adding More Channels

Edit `config.js`:

```javascript
const CHANNELS = [
  // ... existing channels
  {
    id: 17,
    name: 'Channel 17',
    hls: 'https://your-server.com/ch17/index.m3u8',
    dash: 'http://your-server.com/ch17/Manifest.mpd'
  }
];
```

### Changing Grid Layout

Edit `style.css`:

```css
.video-grid {
  grid-template-columns: repeat(4, 1fr); /* Change 4 to desired columns */
}
```

### Customizing Colors

Edit CSS variables in `style.css`:

```css
:root {
  --accent-primary: #6366f1; /* Change to your brand color */
  --accent-secondary: #8b5cf6;
}
```

## Performance Tips

- All streams start muted to prevent audio overload
- Use HLS for better browser compatibility
- Use DASH for lower latency when supported
- Close unused browser tabs for better performance
- Consider reducing grid size on lower-end devices

## License

This project is open source and available for personal and commercial use.

## Support

For issues or questions:
1. Check the browser console for error messages
2. Verify stream URLs are accessible
3. Test with a single channel first
4. Try different browsers

---

**Built with ❤️ using Video.js, DASH.js, and modern web technologies**
