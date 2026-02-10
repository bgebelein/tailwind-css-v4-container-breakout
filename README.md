# tailwind-css-v4-container-breakout

A Tailwind CSS v4 plugin for container breakout utility classes.

## Installation

Import the `container-breakout.css` in your stylesheet.

```CSS
@import "./path/to/container-breakout.css"
```

Or copy its content to your stylesheet.

### Set Scrollbar Width

The `container-breakout.css` uses a CSS custom property `--cbo-scrollbar-width` to calculate the correct margin/padding for each breakout utility class. **Therefore it is absolutely necessary to set this property in your document.**

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

## Basic Usage

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

## Advanced Usage / Customization

It is very likely, that you customized your container to have some inline padding.

If you do so, in order for the calculations to be correct, you have to overwrite the following variables to match your containers inline padding inside your `@theme{ ... }` function:

```CSS
@theme {
    --cbo-padding-x: ... ;
    --cbo-padding-x-sm: ... ;
    --cbo-padding-x-md: ... ;
    --cbo-padding-x-lg: ... ;
    --cbo-padding-x-xl: ... ;
    --cbo-padding-x-2xl: ... ;
}
```

### Example

```CSS
@utility container {
  padding: 0 1rem;

  @variant md {
    padding: 0 1.5rem;
  }
}

@theme {
    --cbo-padding-x: 1rem;
    --cbo-padding-x-sm: 1rem;
    --cbo-padding-x-md: 1.5rem;
    --cbo-padding-x-lg: 1.5rem;
    --cbo-padding-x-xl: 1.5rem;
    --cbo-padding-x-2xl: 1.5rem;
}
```

⚠️ **Important:** Note, that due to the mobile first approach of Tailwind CSS, a customization for one breakpoint will also take effect on all following / bigger breakpoints.

## Demo

https://play.tailwindcss.com/pX1ZE5Lubu?layout=horizontal&file=css