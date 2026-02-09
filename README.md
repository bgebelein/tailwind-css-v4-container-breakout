# tailwind-css-v4-container-breakout

A Tailwind CSS v4 plugin for container breakout utility classes.

## Installation

Import the `container-breakout.css` in your stylesheet.

```CSS
@import "./path/to/container-breakout.css"
```

Or copy its content to your stylesheet.

## ⚠️ Important

The `container-breakout.css` uses the CSS custom property `--scrollbar-width` to calculate the correct margin/padding for each breakout utility class. Therefore it is absolutely necessary to set this property in your document.

Since the width of scrollbars can defer, i recommend adding the following script to your page to set the `--scrollbar-width` property dynamically:

```JavaScript
const getScrollbarWidth = () => {
    const prevWidth = document.getAttribute("data-scrollbar-width") || 0;
    const newWidth = window.innerWidth - document.body.clientWidth;

    if (newWidth !== prevWidth) {
        document.setAttribute("style", "--scrollbar-width:" + newWidth + "px;");
    }
};

const setScrollbarWidth = () => {
    window.addEventListener("load", getScrollbarWidth);
    window.addEventListener("resize", getScrollbarWidth);
    getScrollbarWidth();
};

setScrollbarWidth();
```

## Usage

The `container-breakout.css` stylesheet introduces the following 6 new utility classes:

- mx-break-out
- ml-break-out
- mr-break-out
- px-break-out
- pl-break-out
- pr-break-out

You can use them like this:

```HTML
<div class="container">
    <p>This content is inside the.</p>
    <div class="ml-break-out">
        <p>This content will break out on the left of the container.</p>
    </div>
</div>
```

You can also use Tailwind CSS viewports in combination with the container breakout utility classes:

```HTML
<div class="container">
    <p>This content is inside the.</p>
    <div class="lg:ml-break-out">
        <p>This content will break out on the left of the container on large screens and up.</p>
    </div>
</div>
```

## Customization

The `container-breakout.css` is set to work with default Tailwind CSS viewports and default padding for the `.container` class.

If you customized the viewport breakpoints or `.container` padding in your stylesheet, you will have to adjust the `container-breakout.css` accordingly.

## Visualization

