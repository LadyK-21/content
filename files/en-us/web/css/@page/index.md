---
title: "@page"
slug: Web/CSS/@page
page-type: css-at-rule
browser-compat: css.at-rules.page
sidebar: cssref
---

The **`@page`** at-rule is a CSS at-rule used to modify different aspects of printed pages. It targets and modifies the page's dimensions, orientation, and margins. The `@page` at-rule can be used to target all pages in a print-out or a subset using its various pseudo-classes.

## Syntax

```css
/* Targets all the pages */
@page {
  size: 8.5in 9in;
  margin-top: 4in;
}

/* Targets all even-numbered pages */
@page :left {
  margin-top: 4in;
}

/* Targets all odd-numbered pages */
@page :right {
  size: 11in;
  margin-top: 4in;
}

/* Targets all selectors with `page: wide;` set */
@page wide {
  size: a4 landscape;
}

@page {
  /* margin box at top right showing page number */
  @top-right {
    content: "Page " counter(pageNumber);
  }
}
```

### Page properties

The `@page` at-rule can contain only page descriptors and [margin at-rules](#margin_at-rules). The following descriptors have been implemented by at least one browser:

- [`margin`](/en-US/docs/Web/CSS/margin)
  - : Specifies the page margins. Individual margin properties [`margin-top`](/en-US/docs/Web/CSS/margin-top), [`margin-right`](/en-US/docs/Web/CSS/margin-right), [`margin-bottom`](/en-US/docs/Web/CSS/margin-bottom), and [`margin-left`](/en-US/docs/Web/CSS/margin-left) can also be used.
- [`page-orientation`](/en-US/docs/Web/CSS/@page/page-orientation)
  - : Specifies the orientation of the page. This does not affect the layout of the page; the rotation is applied after the layout in the output medium.
- [`size`](/en-US/docs/Web/CSS/@page/size)
  - : Specifies the target size and orientation of the page box's containing block. In the general case, where one page box is rendered onto one page sheet, it also indicates the size of the destination page sheet.

The specification mentions following CSS properties to be applicable to page boxes via @page at-rule. But these have _not been supported_ by any user agent yet.

<details>
<summary>Remaining page properties</summary>

| Feature               | CSS properties        |
| --------------------- | --------------------- |
| bidi properties       | direction             |
| background properties | background-color      |
|                       | background-image      |
|                       | background-repeat     |
|                       | background-attachment |
|                       | background-position   |
|                       | background            |
| border properties     | border-top-width      |
|                       | border-right-width    |
|                       | border-bottom-width   |
|                       | border-left-width     |
|                       | border-width          |
|                       | border-top-color      |
|                       | border-right-color    |
|                       | border-bottom-color   |
|                       | border-left-color     |
|                       | border-color          |
|                       | border-top-style      |
|                       | border-right-style    |
|                       | border-bottom-style   |
|                       | border-left-style     |
|                       | border-short-style    |
|                       | border-top            |
|                       | border-right          |
|                       | border-bottom         |
|                       | border-left           |
|                       | border                |
| counter properties    | counter-reset         |
|                       | counter-increment     |
| color                 | color                 |
| font properties       | font-family           |
|                       | font-size             |
|                       | font-style            |
|                       | font-variant          |
|                       | font-weight           |
|                       | font                  |
| height properties     | height                |
|                       | min-height            |
|                       | max-height            |
| line height           | line-height           |
| margin properties     | margin-top            |
|                       | margin-right          |
|                       | margin-bottom         |
|                       | margin-left           |
|                       | margin                |
| outline properties    | outline-width         |
|                       | outline-style         |
|                       | outline-color         |
|                       | outline               |
| padding properties    | padding-top           |
|                       | padding-right         |
|                       | padding-bottom        |
|                       | padding-left          |
|                       | padding               |
| quotes                | quotes                |
| text properties       | letter-spacing        |
|                       | text-align            |
|                       | text-decoration       |
|                       | text-indent           |
|                       | text-transform        |
|                       | white-space           |
|                       | word-spacing          |
| visibility            | visibility            |
| width properties      | width                 |
|                       | min-width             |
|                       | max-width             |

</details>

## Description

The @page rule defines properties of the page box. The `@page` at-rule can be accessed via the CSS object model interface {{domxref("CSSPageRule")}}.

> [!NOTE]
> The W3C is discussing how to handle viewport-related {{cssxref("&lt;length&gt;")}} units, `vh`, `vw`, `vmin`, and `vmax`. Meanwhile do not use them within a `@page` at-rule.

### Related properties

The `@page` at-rule, allows the user to assign a name to the rule, which is then called in a declaration using the `page` property.

- {{Cssxref("page")}}
  - : Allows a selector to use a user defined **named page**

## Formal syntax

{{csssyntax}}

Where the `<page-body>` includes:

- page-properties
- page-margin properties

and `<pseudo-page>` represents these pseudo-classes:

- {{Cssxref(":blank")}}
- {{Cssxref(":first")}}
- {{Cssxref(":left")}}
- {{Cssxref(":right")}}

## Margin at-rules

The margin at-rules are used inside of the `@page` at-rule. They each target a different section of the document printed page, styling the area of the printed page based on the property values set in the style block:

```css
@page {
  @top-left {
    /* page-margin-properties */
  }
}
```

**`@top-left`** targets the top-left of the document and applies the changes based on the page-margin-properties set.

Other margin-at rules include:

```css-nolint
@top-left-corner
@top-left
@top-center
@top-right
@top-right-corner
@bottom-left-corner
@bottom-left
@bottom-center
@bottom-right
@bottom-right-corner
@left-top
@left-middle
@left-bottom
@right-top
@right-middle
@right-bottom
```

### Page-margin properties

The page-margin properties are the set of CSS properties can be set in any individual margin at-rule. They include:

<details>
<summary>Page-margin properties</summary>

| Feature               | CSS properties        |
| --------------------- | --------------------- |
| bidi properties       | direction             |
| background properties | background-color      |
|                       | background-image      |
|                       | background-repeat     |
|                       | background-attachment |
|                       | background-position   |
|                       | background            |
| border properties     | border-top-width      |
|                       | border-right-width    |
|                       | border-bottom-width   |
|                       | border-left-width     |
|                       | border-width          |
|                       | border-top-color      |
|                       | border-right-color    |
|                       | border-bottom-color   |
|                       | border-left-color     |
|                       | border-color          |
|                       | border-top-style      |
|                       | border-right-style    |
|                       | border-bottom-style   |
|                       | border-left-style     |
|                       | border-short-style    |
|                       | border-top            |
|                       | border-right          |
|                       | border-bottom         |
|                       | border-left           |
|                       | border                |
| counter properties    | counter-reset         |
|                       | counter-increment     |
| content               | content               |
| color                 | color                 |
| font properties       | font-family           |
|                       | font-size             |
|                       | font-style            |
|                       | font-variant          |
|                       | font-weight           |
|                       | font                  |
| height properties     | height                |
|                       | min-height            |
|                       | max-height            |
| line height           | line-height           |
| margin properties     | margin-top            |
|                       | margin-right          |
|                       | margin-bottom         |
|                       | margin-left           |
|                       | margin                |
| outline properties    | outline-width         |
|                       | outline-style         |
|                       | outline-color         |
|                       | outline               |
| padding properties    | padding-top           |
|                       | padding-right         |
|                       | padding-bottom        |
|                       | padding-left          |
|                       | padding               |
| quotes                | quotes                |
| text properties       | letter-spacing        |
|                       | text-align            |
|                       | text-decoration       |
|                       | text-indent           |
|                       | text-transform        |
|                       | white-space           |
|                       | word-spacing          |
| vertical alignment    | vertical-align        |
| visibility            | visibility            |
| width properties      | width                 |
|                       | min-width             |
|                       | max-width             |
| z-index               | z-index               |

</details>

## Named pages

Named pages enable performing per-page layout and adding [page-breaks](/en-US/docs/Web/CSS/CSS_fragmentation) in a declarative manner when printing.

Named pages can be applied using the {{Cssxref("page")}} property. This allows the user to create different page configurations for use in print layouts.

An example of this can be found on the [`page`](/en-US/docs/Web/CSS/page#examples) examples.

## Examples

### Using the size property to change the page orientation

This example shows how to split the `<section>`s into individual pages in `landscape` format with each page having a 20% margin when printed.
Clicking the print button will launch a print dialog with the HTML sections split into individual pages.

```html live-sample___page-size
<button>Print page</button>
<article>
  <section>
    <h2>Header one</h2>
    <p>Paragraph one.</p>
  </section>
  <section>
    <h2>Header two</h2>
    <p>Paragraph two.</p>
  </section>
  <section>
    <h2>Header three</h2>
    <p>Paragraph three.</p>
  </section>
</article>
```

```js live-sample___page-size
const button = document.querySelector("button");

button.addEventListener("click", () => {
  window.print();
});
```

```css live-sample___page-size
@page {
  size: landscape;
  margin: 2cm;
}

section {
  page-break-after: always;
  break-after: page;
}

@media print {
  button {
    display: none;
  }
}
```

```css hidden live-sample___page-size
body {
  font-family: "Helvetica", sans-serif;
  background-color: silver;
}

article {
  width: 100%;
}

section {
  display: grid;
  background-color: white;
  border-radius: 0.6rem;
  justify-items: center;
  padding: 1rem;
  width: 50%;
  print-color-adjust: exact;
  -webkit-print-color-adjust: exact;
  margin: 0 auto;
  margin-block-end: 1rem;
  border: 1px dashed;
}
```

{{EmbedLiveSample('page-size', '100%', '540', , , , , "allow-modals")}}

### @page pseudo-class examples

See the various [pseudo-classes](/en-US/docs/Web/CSS/Pseudo-classes) of `@page` for examples.

- {{Cssxref(":blank")}}
- {{Cssxref(":first")}}
- {{Cssxref(":left")}}
- {{Cssxref(":right")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The {{cssxref("page")}} property
- The `@page` [`size`](/en-US/docs/Web/CSS/@page/size) descriptor
- [CSS paged media](/en-US/docs/Web/CSS/CSS_paged_media) module
- [\[META\] CSS Paged Media Module Level 3](https://bugzil.la/286443) Bugzilla for tracking progress on the subject (page-based counters, etc.)
