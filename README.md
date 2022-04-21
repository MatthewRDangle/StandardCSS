# FoundationCSS
A dead-simple CSS boilerplate; it only uses element selectors to standardize styling across 
browsers and reduce unnecessary class construction. Think NormalizeCSS or ResetCSS, but 
customizable.

## How does it work?
The boilerplate provides styling for commonly utilized features: scrollbar, anchors, 
form input groups, validation, quote boxes, code, etc. They're applied with element selectors 
only to reduce overhead. Stylesheet `props` `var()` is used so the boilerplate can be scaled 
and customized easily.

Example of `:root` `props`.
```
--fontSize: 16px;
--lineHeight: 1.75; /* Keep this number unitless to avoid overlap and inheritance issues. */

--headerFont: 'Geneva';
--bodyFont: 'Arial';
--monoFont: 'Lucida Console';

--font: #000000;
--foreground: #EAEAEA;
--background: #FFFFFF;
...
```

Example of cross-browser standardization using `props`.
```
...
html, body {
    padding: 0; /* Remove unnecessary padding. */
    margin: 0; /* Remove unnecessary margin. */
}
body {
    -webkit-text-size-adjust: 100%; /* Prevent adjustments of font size after orientation changes in iOS. */

    /* Default Background */
    background-color: var(--background, #FFFFFF);

    /* Global Inherited Defaults */
    font-family: var(--headerFont, 'Geneva'), 'Helvetica', serif;
    font-size: var(--fontSize, 16px);
    line-height: var(--lineHeight, 1.75);
    color: var(--font, #000000);
}
html:focus, body:focus {
    outline: none; /* Remove default agent outline focus from most browsers. */
}
...
```

Example of Input Validation using `props`.
```
fieldset:invalid {
    border-color: var(--warning, #E86363);
}
fieldset:invalid > legend {
    color: var(--warning, #E86363);
}
input:not([value='']):not(:focus):invalid, select:not(:focus):invalid, textarea:not(:focus):invalid {
    border-color: var(--warning, #E86363);
}
input:not(:focus):required:valid, select:not(:focus):required:valid, textarea:not(:focus):required:valid {
    border-color: var(--success, #7CDC7C)
}
```

## Why Use This?
FoundationCSS is designed to act as a bedrock / foundational layer for new themes and frameworks. If you are building
your stylesheets from scratch and want a customizable cross-browser supported boilerplate, then FoundationCSS is for you.
If importing a framework or extending one, then FoundationCSS is not for you.

## What is included in the Foundation layer?
The foundation layer includes only few groups at the moment. However, there are plans to expand this has HTML and CSS
adopts more commonly built features. However, everything here is fully customizable via props or by messing with their
properties. Yes that also means custom checkbox, radio, quotes and search without any extra HTML markup. CSS handles
it all.

* Page Building (Containers)
  * Headers
  * Main, Article, Sections
  * Footers
* Content Handling
  * Header
  * Paragraph, Span, 
  * Image
  * Delete, Emphasis, Strong, etc.
  * Citations
  * Anchors
  * Preformatted Text (ex. pre, code, sample)
  * Quotes and Blockquotes
  * etc...
* Scrollbar (webkit browsers only)
* Form Control
  * Various Inputs
    * Text, Textarea, Select, Search, Radio, Checkbox, etc.
  * Input Groups
  * Validation & Invalidation

## Compatability
This HTML boilerplate is designed to work with some of the latest technology that is accepted by all modern browsers.
As of 4/20/2022, 94% of all users browsers', according to CanIUse, support everything in document. Except the scrollbar,
as only webkit supported browsers support this.

## Accessibility
All styling following the recommendations of W3C or integrates a commonly used browser style agent implementation. Since
all elements being modified are still displayed by default, even if their appearance and aesthetic is overwritten 
(ex. checkbox and radio), they still retain the accessible properties.

## Licencing
Please see the legal directory for this project regarding use.

## Release
All releases will use the following format `v{major}.{minor}.{patch}`. 
*Major = break backwards compatability.
*Minor = additional features.
*Patch = bug fixes, and simple changes.

