# Documentation

## The `cloneHTML` element

The `cloneHTML` element specifies the target to clone, where to clone it, and the depth at which to clone.

The following table demonstrates the configurable attributes in the tag:

| Attribute | Description |
| ------------- | ------------- |
| data-target  | The selector of the element to clone (retrieves the first one matching) |
| data-depth  | Either **deep** or **shallow**. **deep** copies all children.  |

For example, the following:

```html
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
<cloneHTML data-target="#elementToClone" data-depth="deep" />
```

Is translated to:

```html
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
```

## The `window.cloner4html` JS configuration object (optional)

The `window.cloner4html` object specifies the configuration for cloner4html.

2 attributes are supported:

| Attribute | Description |
| ------------- | ------------- |
| settings  | General settings for cloner4html to follow |
| configuration  | Individual configurations for each `cloneHTML` element |

### configuration

The configuration attribute does not have fixed attributes, but instead supports sub-attributes. These subattributes control individual/grouped `cloneHTML` elements.

For example, if you have a cloneHTML element like so:

```
<cloneHTML data-target="#elementToClone" data-depth="deep" />
```

You would select it inside the configuration like so:

```javascript
window.cloner4html = {
  configuration:{
    "#elementToClone":{
      //do some configuring
    }
  }
}
```

Once selected, you can select inner elements. This is when the **data-cid** attribute comes in.

Suppose you have the following:

```html
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
<cloneHTML data-target="#elementToClone" data-depth="deep" />
```

If you wanted copy but also change the `h1` element to show something like "Heading 2", you would do the following:
```javascript
window.cloner4html = {
    configuration: {
        "#elementToClone": {
            'header': {
                'type': 'text',
                'content': 'Heading 2'
            },
        }
    }
};
```

Which results in:

```html
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 1</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
<div id="elementToClone">
    This is a cool div!
    <h1 data-cid="header">Heading 2</h1>
    <h2 data-cid="subheader">Subheading 1</h2>;
</div>
```

Similarly, if you want to change the HTML of the element, set the `type` to HTML. For example, if you want to make the copied header in *italics*, use:

```javascript
window.cloner4html = {
    configuration: {
        "#elementToClone": {
            'header': {
                'type': 'html',
                'content': '<i>Heading 2</i>'
            },
        }
    }
};
```

### settings

The settings accepts 1 attribute: `remove-cid`. If `remove-cid` is set to `true`, it will remove all elements with the `data-cid` after cloning.
