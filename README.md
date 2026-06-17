# Frontend Mentor - Recipe page solution

This is a solution to the [Recipe page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/recipe-page-KiTsR8QQKm). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
    - [Links](#links)
- [My process](#my-process)
    - [Built with](#built-with)
    - [What I learned](#what-i-learned)
    - [Continued development](#continued-development)
    - [AI Collaboration](#ai-collaboration)
- [Author](#author)

## Overview

### Links

- Solution URL: https://github.com/edu-challenges/recipe-page
- Live Site URL: https://edu-challenges.github.io/recipe-page

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- CSS nesting
- Flexbox
- Mobile-first workflow

### What I learned

The most interesting technique I worked through was the **full-bleed image** on mobile. The card has horizontal padding, but the hero image needs to stretch edge to edge. The solution is to counteract the padding with a negative margin and an expanded width, then revert those overrides at the desktop breakpoint:

```css
/* Mobile: escape the container's padding */
main {
    overflow-x: clip;

    img {
        width: calc(100% + 4.8rem);
        max-width: none;
        margin-inline: -2.4rem;
        margin-top: -2.4rem;
    }
}

/* Desktop: back to normal, add border-radius */
@media (min-width: 768px) {
    main img {
        width: 100%;
        margin-inline: 0;
        margin-top: 0;
        border-radius: 0.8rem;
    }
}
```

I also learned the importance of `overflow-x: clip` on the **container** rather than the element itself — `overflow` clips children, not the element it's applied to.

Another thing that clicked was the difference between `&` in CSS nesting and a plain child selector. Using `&:nth-child(3)` inside `main {}` targets `main` itself, not its children — you need `> :nth-child(3)` for that.

On the accessibility side, I learned that `<th>` elements inside a body row need `scope="row"` so screen readers can associate each header with its data cell correctly.

I also got better at styling list bullets in a practical way. For custom list visuals, `::marker` is useful, but it only supports a limited set of properties (such as `color`, `content`, and font-related properties). If you need spacing control, the right place is usually `padding` and `margin` on `ul`/`ol` and `li`, instead of trying unsupported spacing properties directly on `::marker`.

### Continued development

- Deploying projects and setting up a proper live URL workflow
- Exploring more CSS nesting patterns as browser support matures
- Deepening accessibility knowledge, particularly around ARIA roles and keyboard navigation

### AI Collaboration

I used **GitHub Copilot** as a mentor throughout this challenge. Rather than writing code for me, it guided me with explanations, spotted bugs I introduced (like misplaced `overflow-x: clip` and the `&` nesting issue), and reviewed the final HTML and CSS for accessibility improvements. All the code was written by me.

## Author

- Frontend Mentor - [@Yevestevez](https://www.frontendmentor.io/profile/Yevestevez)
