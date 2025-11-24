# Copilot Instructions for RJ Books

## Project Overview
RJ Books is a static author website for Ruchith Jay, showcasing e-books and web novels. Built as a PWA with GitHub Pages hosting, focusing on mobile-responsive design and social media integration.

## Architecture & Structure

### Core Components
- **Single-page application** with section-based navigation (`#ebooks`, `#webnovels`)
- **PWA configuration** via `manifest.json` with offline capabilities
- **Asset organization**: SVG icons in `/assets/`, book covers in `/images/`, optimized WebP format
- **Responsive design**: Mobile-first with breakpoints at 768px and 480px

### Key Sections (in order)
1. **Header** - Navigation between E-books/Web novels + Medium link
2. **Profile** - Author bio with social media links (6 platforms)
3. **Carousel** - Promotional book covers with auto-slide (5s interval)
4. **E-books** - Physical/digital book cards with platform links
5. **Web novels** - Grid layout for web stories with external platform links
6. **Telegram** - Channel promotion
7. **Footer** - Contact info with dynamic copyright year

### State Management Patterns
- **Carousel state**: Manual navigation + auto-advance with pause-on-hover
- **Copyright banner**: Dismissible with body padding adjustment
- **Navigation**: Active state management for nav links
- **Dynamic content**: Year auto-update, coming soon badges

## Development Conventions

### HTML Patterns
- **Semantic structure**: Use `<section>` with meaningful IDs for navigation
- **Image optimization**: WebP format preferred, include alt text
- **Accessibility**: ARIA labels on interactive elements, proper heading hierarchy
- **Meta tags**: Comprehensive SEO with Open Graph and Twitter Card support

```html
<!-- Example book card structure -->
<div class="book-card">
    <div class="book-image">
        <img src="images/cover.webp" alt="Book Cover">
        <!-- Coming soon badge (comment out when not needed) -->
        <div class="coming-soon-badge">Coming Soon</div>
    </div>
    <div class="book-details">...</div>
</div>
```

### CSS Architecture
- **Color scheme**: Primary `#f87171` (red-400), background `#f5f5f0` (warm cream)
- **Typography**: Inter font family with weights 300-700
- **Responsive strategy**: Desktop-first with mobile overrides
- **Component-based**: Each section has dedicated CSS block

```css
/* Section naming convention */
.section-name {
    /* Desktop styles */
}

@media (max-width: 768px) {
    .section-name {
        /* Tablet styles */
    }
}

@media (max-width: 480px) {
    .section-name {
        /* Mobile styles */
    }
}
```

### JavaScript Patterns
- **Event-driven**: DOMContentLoaded for initialization
- **Carousel logic**: Index-based sliding with modular arithmetic for wrapping
- **Touch support**: Swipe gestures for mobile carousel navigation
- **Performance**: Debounced auto-slide with clear/reset on user interaction

## Content Management

### Adding New Books
1. **E-books**: Add new `book-card` div in `#ebooks` section
2. **Web novels**: Add new `novel-card` div in `.novels-grid`
3. **Images**: Use WebP format, consistent naming (novel1.webp, novel2.webp)
4. **Platform links**: Update href attributes for Amazon, Wattpad, Royal Road, Goodreads

### Managing Coming Soon Content
- **Badge**: Comment/uncomment `<div class="coming-soon-badge">Coming Soon</div>`
- **Links**: Use `#` for placeholder links, update when available
- **CSS**: Badge styles marked with "Easy to remove" comments

### Social Media Integration
- **Links**: Update social platform URLs in profile section
- **Icons**: SVG files in `/assets/` with circle variants preferred
- **Meta tags**: Update Twitter handle, Open Graph URLs when social profiles change

## Development Workflow

### Local Development
```bash
# Simple HTTP server options
python -m http.server 8000
npx serve .
php -S localhost:8000
```

### File Optimization
- **Images**: Convert to WebP, maintain aspect ratios
- **Assets**: Use SVG for icons, optimize file sizes
- **Performance**: Minimize inline CSS/JS, leverage font-display: swap

### Common Tasks
- **Update copyright year**: Automatic via `currentYear` span
- **Carousel slides**: Add image to `/images/`, update carousel HTML + dots
- **Platform buttons**: Follow existing pattern with icon + text
- **Mobile testing**: Focus on carousel touch interaction and responsive layout

## External Dependencies
- **Google Fonts**: Inter font family
- **Buy Me a Coffee**: Widget for donations (external script)
- **GitHub Pages**: Automatic deployment from main branch
- **Platform integrations**: Wattpad, Royal Road, Amazon, Goodreads direct linking

## SEO & Performance
- **Meta optimization**: Title, description, keywords for author discovery
- **Social sharing**: Open Graph images sized 1200x630
- **Progressive enhancement**: Base functionality without JavaScript
- **Lazy loading**: Consider for book cover images if collection grows
- **Security**: Content Security Policy (CSP) implemented to prevent XSS attacks

## Security Considerations
- **CSP Policy**: Restricts external resources to trusted domains only
- **External dependencies**: Buy Me a Coffee widget from cdnjs.buymeacoffee.com
- **Safe practices**: `noopener noreferrer` on external links, frame-ancestors 'none'
- **Asset sources**: Google Fonts (fonts.googleapis.com, fonts.gstatic.com), placeholder images (placehold.co)
- **Contact obfuscation**: Email and phone number are JavaScript-generated to prevent bot harvesting

## Common Modifications
- **Theme colors**: Update CSS custom properties and manifest.json
- **New sections**: Follow existing section structure with container > content pattern
- **Book status**: Toggle coming soon badges and update platform links
- **Contact info**: Update footer email, phone, social links consistently