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
      { id = "now", title = "Now", category = "now", style = "now-column" },
      { id = "write", title = "Writing", category = "write", style = "write-column" },
      { id = "quote", title = "Quotes", category = "quotes", style = "quote-column" },
      { id = "read", title = "Reading", category = "read", style = "read-column" },
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

This decoupled design allows:
- Same content category can be displayed in different styles
- Different categories can share the same display style
- Flexible mapping between content organization and visual presentation

## License

MIT License

## Credits

Created by [Yibie](https://github.com/yibie)

