<p align="center">
  <img src="https://user-images.githubusercontent.com/65585002/118021202-f9721880-b328-11eb-8610-3ea9eda15e25.png">
  <br/>
  <h1 align="center">Simple, elegant, lightweight</h1>
  <p align="center">The Javascript library that lets you copy HTML will full flexibility</p>
</p>

##  Basic Usage

Most simple usage:

```html
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
<cloneHTML data-target="#elementToClone" data-depth="deep" />
```
With configuration comes more flexibility (JavaScript):

```javascript
window.cloner4html = {
    settings: {
        'remove-cid': true
    },
    configuration: {
        "#elementToClone": {
            'header': {
                'type': 'text',
                'content': 'New Heading!'
            },
            'subheader': {
                'type': 'html',
                'content': '<i>In italics</i>'
            }
        }
    }
};
```

## Documentation

➥ [documentation.md](https://github.com/ColonelParrot/cloner4html/blob/main/docs/documentation.md)

## Import

cloner4html is imported via CDN like so:

```html
<script src="https://cdn.jsdelivr.net/gh/ColonelParrot/cloner4html@1.0/src/script.min.js"></script>
```

[MIT License](https://github.com/ColonelParrot/cloner4html/blob/main/LICENSE)
