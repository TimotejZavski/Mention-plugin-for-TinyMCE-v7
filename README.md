# Mention Plugin for TinyMCE v7

A free and open-source mention plugin for TinyMCE v7 that supports rich citations with customizable formatting styles.

## Features

- Smart inline citations with detailed hover previews
- Citation styles: APA 7th edition, Harvard, and custom styles
- Connect to any data source
- Non-editable citation elements
- Rich popover tooltips
- Seamless integration with TinyMCE v7

## Installation

1. Get TinyMCE:
```html
<script src="path/to/tinymce/js/tinymce/tinymce.min.js"></script>
```

2. Add Popper.js for tooltips:
```html
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js"></script>
```

3. Add your citation data (check the Data Structure section)

4. Include some CSS:
```css
.mention-name { 
    background-color: #f0f7ff; 
    border: 1px solid #c2d8f2; 
    border-radius: 3px; 
    padding: 2px 4px; 
    color: #2271b1; 
    cursor: pointer; 
}
```

## Usage Examples

### Default

```javascript
tinymce.init({
    selector: '#your-textarea',
    plugins: 'mention'
});
```

### APA 7th Edition Citation Style

```javascript
tinymce.init({
    selector: '#your-textarea',
    plugins: 'mention',
    mention: {
        citationFormat: 'apa'
    }
});
```

### Harvard Citation Style

```javascript
tinymce.init({
    selector: '#your-textarea',
    plugins: 'mention',
    mention: {
        citationFormat: 'harvard'
    }
});
```

### Custom Citation Style (For The Control Freaks)

```javascript
tinymce.init({
    selector: '#your-textarea',
    plugins: 'mention',
    mention: {
        citationFormat: 'custom',
        formatCitation: function(item) {
            // Do your magic here
            return {
                short: `(${item.author.split(',')[0]}, ${item.year})`,
                full: `Custom citation for "${item.title}" by ${item.author}`
            };
        }
    }
});
```

## How It Works

1. Type `@` in the editor to trigger the mention dropdown
2. Select an item from the dropdown
3. A short citation gets inserted in your document
4. Hover over it to see the full citation

## Data Structure

Here's what your data should look like:

```javascript
window.mentionData = [
    {
        title: "The Impact of AI on Modern Software Development",
        author: "John Smith",
        year: "2024",
        sourceType: "article",
        publisher: "Tech Review Quarterly",
        volume: "15",
        pages: "45-52",
        doi: "10.1234/ai.2024.1234"
    },
    {
        title: "UX Design Principles for the Modern Web",
        author: "Jane Doe, Robert Wilson",
        year: "2023",
        sourceType: "book",
        publisher: "Web Design Press",
        edition: "2nd Edition",
        isbn: "978-0-123456-78-9"
    }
    // Add more brilliant citations here
];
```

### Supported Source Types

The plugin formats citations based on the `sourceType` field because not all sources are created equal:

- `article`: For those peer-reviewed journal articles you probably didn't read fully
- `book`: Books and textbooks that look good on your shelf
- `conference`: Conference papers where networking was the real value
- `website`: Web resources that may or may not exist tomorrow
- `report`: Reports, white papers, and other official-sounding documents

## Demos

Check out these demo files to see the plugin in action:

- `demo.html`: Default configuration
- `demo-APA7.html`: APA 7th edition citation style
- `demo-Harvard.html`: Harvard citation style

## License

This project is MIT licensed - free to use in both personal and commercial projects.

Created by Timotej Zavski