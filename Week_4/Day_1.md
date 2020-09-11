# Intro to CSS

## Topics
### Writing Semantic HTML
### Reset/normalize
### Box Sizing: Border-box (non-default)
### CSS Debugging in DevTools
### CSS Specificity
### Writing good CSS Selectors (best practices)
### Intro to Flexbox
### When to use IDs vs Classes

[Notes and Code Here](https://github.com/hafbau/lecture_notes/tree/master/w4d1)

## HTML
* HTML adds **context** (formatting) to content so it is easier to read, you know what you are looking at, gives a sense of organization
* CSS is about **presentation**, branding (color, borders, etc.)
* Semantic tags allow you to be specific about what your tags are doing (what is the content) and helps you avoid div soup, also improves accessibility
* Use HTML tags for reference (ex. if you need a tag about time, google it! There is likely a tag that exists, if not we can find a tag that could work)

## CSS
* Cascading Style Sheets
  * Cascading can mean top down or inheritance (parent to child)
* Best practice is to use an external css file
  * Can also use inline style tags or internal style tags (usually in the head)
* See notes for formatting
* !important will make that rule override all other factors of importance, but this can be dangerous as it has sideeffects (best to avoid for now)
* If things are not changing check specificity order to see why something is being overwritten

## Boxes
* The main content is central, first surrounding box is padding, then border, then margin
* You can set all sides of padding seperately (top, right, bottom, left => trouble!) or create one padding value for all sides
* Check notes for block level vs inline elements => these are important for understanding page layouts

## Layout
* Flexbox!
  * Look into flex direction and axes to change page layout (should be header, left, and right box)
  * Can set margin to 0 to remove automatic margins, body height 100vh to make it automatically the height of the page
  * Create div class container to separate elements, then use flex grow to force elements to share the space in the container
  * Use DevTools to create visible borders on other websites to get a sense of layouts