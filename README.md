# Hugo Theme Deck

A clean, column-based Hugo theme inspired by TweetDeck. Perfect for personal websites that want to present different types of content in an organized, visually appealing way.

![screenshot](/static/demo.png)

## Features

- 🎯 Column-based layout for different content types
- 🔄 Flexible mapping between content and display styles
- 🎨 Clean and minimal design
- 📱 Responsive design for desktop and mobile
- 🎭 Multiple column styles for content display
- ⚡ Fast and lightweight

## What's New in v2 (Major Upgrade)

A comprehensive UI/UX overhaul focusing on modern aesthetics, performance, and interaction fluidity.

### 🎨 Visual & UI Overhaul
- **Glassmorphism Design**: Implemented a sophisticated frosted glass effect across the sidebar and cards, supported by a dynamic ambient background animation.
- **Deep Glass Hover**: Cards feature a "Deep Glass" effect on hover, creating a premium depth perception with subtle color tinting based on column type.
- **Typography Upgrade**: Migrated to a modern font stack (Inter, SF Pro) with fluid typography scaling for better readability on all devices.
- **Dark Mode Perfected**: Fully optimized dark theme with refined color palettes, shadow depth, and contrast adjustments.
- **Clean Sidebar**: Polished sidebar layout with better alignment, simplified footer (removed visual noise), and improved mobile responsiveness.
- **Refined Layout**: Fixed column gaps (`2rem`), removed intrusive dividers, and ensured perfect alignment between headers and content.
- **New Link Column**: Added a specialized `link` column style for sharing curated links with rich previews (title, domain, thumbnail) and commentary.

### ⚡ Interaction & Experience
- **Physics-Based Animations**: All transitions now use spring physics (`cubic-bezier`) for a natural, snappy feel.
- **Full Card Clickability**: Cards are now fully clickable (via `stretched-link`) with `pointer` cursor throughout, functioning as large, cohesive touch targets.
- **Native Scrolling**: Restored system-native scrollbars for consistent OS feel, while ensuring smooth momentum scrolling (`-webkit-overflow-scrolling`) on iOS.
- **Scroll Improvements**: Fixed "double scrollbar" issues, page jumping bugs, and background bleeding. The horizontal column scroll is now locked to the container, preventing body scroll conflicts.

### 🛠 Technical Improvements
- **CSS Modularization**: Refactored monolithic CSS into modular files (`base.css`, `layout.css`, `cards.css`, etc.) for better maintainability.
- **CSS Variables**: Extensive use of CSS Custom Properties for theming, spacing, and animations, making customization easier.
- **Clean Code**: Removed redundant styles, legacy hacks, and unused assets.

## Installation

1. In your Hugo site directory, run:
```bash
git submodule add https://github.com/yibie/hugo-theme-deck themes/hugo-theme-deck
```

2. In your site's `hugo.toml`, set the theme:
```toml
theme = "hugo-theme-deck"
```

3. Copy `hugo.toml` from `themes/hugo-theme-deck` to your site's root directory.

## How it works

Hugo Theme Deck works by decoupling three key components:

1. **Column Names**: Define what columns appear in your layout
2. **Column Styles**: Determine how content is displayed
3. **Posts**: Content with standard structure

### Configuration

In `hugo.toml`, you configure your site and columns:

```toml
# Basic site configuration
baseURL = 'https://example.org/' # Your site URL  
languageCode = 'en-us' # Your site language
title = 'Your Site Title' # Your site title
theme = 'hugo-theme-deck' # Your theme

# Theme parameters
[params]
  # Site header information
  author = "Your Name" # Your name
  subtitle = "Your Subtitle" # Your subtitle
  bio = "Your bio text here. You can use **markdown** formatting." # Your bio text

  # Column configuration
  [params.sections]
    columns = [
      # Each column needs:
      # - id: Unique identifier
      # - title: Display name in header
      # - category: Content category to display
      # - style: Visual style to apply
      { id = "now", title = "Now", category = "now", style = "now" },
      { id = "write", title = "Writing", category = "write", style = "write" },
      { id = "quote", title = "Quotes", category = "quotes", style = "quote" },
      { id = "read", title = "Reading", category = "read", style = "read" },
      { id = "link", title = "Links", category = "link", style = "link" },
      # Example of reusing a style
      { id = "til", title = "TIL", category = "til", style = "write-column" }  # TIL column is also use write-column style
    ]

# Optional menu configuration
[[menu.main]]
name = "About"
url = "/about/"
weight = 10

[[menu.main]]
name = "Archive"
url = "/posts/"
weight = 20
```

Key configuration concepts:
1. `category` in column config matches with post's front matter categories
2. `style` determines the visual presentation (now-column, write-column, quote-column, read-column)
3. Different categories can use the same style (like TIL using write-column)
4. Column order in config determines display order

### Post Structure
All content posts share the same basic structure:
```yaml
---
title: "Post Title"
date: 2024-03-14
categories: ["write"]  # Determines which column the post appears in, must be one of the column names in the config, otherwise it will not be displayed
source: James          # Quote source (optional), will be displayed in the quote column as quote source 
---
Post content goes here...
```

### Column Styles
The theme provides different styles for displaying post in different columns. Each style processes the post content differently:

- `write-column`: 
  - Title → Card header
  - First paragraph → Card summary
  - Rest of content → Only visible in single page

- `quote-column`:
  - Title → Quote text with decorative marks
  - Content → Not displayed
  - Date → Not displayed

- `now-column`:
  - Title → Not displayed
  - Content → Bubble message content
  - Date → Timestamp in bubble

- `read-column`:
  - Title → Overlay text on hover
  - First image in content → Grid item cover
  - Content → Not displayed
  - Date → Not displayed

- `link-column`:
  - Rich Preview Card with title, domain, description, and optional image
  - Clicking the preview card opens the external link directly
  - Post content acts as commentary below the card
  - Date → Card footer

This decoupled design allows:
- Same content category can be displayed in different styles
- Different categories can share the same display style
- Flexible mapping between content organization and visual presentation

## License

MIT License

## Credits

Created by [Yibie](https://github.com/yibie)

