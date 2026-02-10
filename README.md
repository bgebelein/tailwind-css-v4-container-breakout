# tailwind-css-v4-container-breakout

A Tailwind CSS v4 plugin/stylesheet for container breakout utility classes.

## Setup

`npm i tailwind-css-v4-container-breakout`

Import the `container-breakout.css` in your stylesheet.

```CSS
@import "./path/to/container-breakout.css"
```

### Set Scrollbar Width

The `container-breakout.css` uses a CSS custom property `--cbo-scrollbar-width` to calculate the correct margin/padding for each breakout utility class.

**For best results it is absolutely necessary to set this property in your document.**

Since the width of scrollbars can defer, i recommend adding the following script to your page to set the `--cbo-scrollbar-width` property dynamically:

```JavaScript
const getScrollbarWidth = () => {
    const prevWidth = document.body.style.getPropertyValue("--cbo-scrollbar-width");
    const newWidth = `${window.innerWidth - document.body.clientWidth}px`;

    if (newWidth !== prevWidth) {
        document.body.setAttribute("style", "--cbo-scrollbar-width:" + newWidth);
    }
};

const setScrollbarWidth = () => {
    window.addEventListener("load", getScrollbarWidth);
    window.addEventListener("resize", getScrollbarWidth);
    getScrollbarWidth();
};

setScrollbarWidth();
```

### Custom Container padding and sizes

If you want to customize `padding` or `width` of the `.container` class, use the following CSS custom properties to set your customizations:

```CSS
@theme {
    --cbo-padding-x: ... ;
    --cbo-padding-x-sm: ... ;
    --cbo-padding-x-md: ... ;
    --cbo-padding-x-lg: ... ;
    --cbo-padding-x-xl: ... ;
    --cbo-padding-x-2xl: ... ;

    --cbo-max-width-sm: ... ;
    --cbo-max-width-md: ... ;
    --cbo-max-width-lg: ... ;
    --cbo-max-width-xl: ... ;
    --cbo-max-width-2xl: ... ;
}
```

## Usage

The `container-breakout.css` stylesheet introduces the following 6 new utility classes:

- `mx-break-out`
- `ml-break-out`
- `mr-break-out`
- `px-break-out`
- `pl-break-out`
- `pr-break-out`

You can use them like this:

```HTML
<div class="container">
    <p>This content is inside the container.</p>
    <div class="ml-break-out">
        <p>This content will break out on the left of the container.</p>
    </div>
</div>
```

## Demo

https://play.tailwindcss.com/bixCZmv4yN?layout=horizontal

## Buy me a coffee

https://buymeacoffee.com/bgebelein