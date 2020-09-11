# Responsive Design and SASS

## Responsive Design
### CSS features that can help:
  * Media-queries
  * Percentages
  * EMs
  * Max-width, min-width
  * Viewport
  * Border-box
### Flexbox
### Grid Systems
### Convert sample site to be responsive (demo)

## SASS
### Preprocessor
### SASS Extra Features:
  * Variables
  * Nseting
  * Partials and import
  * Mixins
  * Extend
  * Math
### Use SASS with node project
### Convert CSS to SASS (demo)

[Notes and code here](https://github.com/tborsa/LighthouseLabs/tree/master/lectures/Week3/Day5/Lecture)

**display: inline-block** will cause things to automatically drop down as the screen shrinks

* background-size: contain will make images automatically match dimensions, background-repeat: no repeat means it won't tile within the space

* vw (view-width) and vh (view-height) will take up a percentage of the dimensions of the page (whatever screen you are viewing on)
  * vw/vh behaves very similar to percentages when looking at the whole screen, but this changes when changing a child in which case it looks at the size of the parent and applies the size to a percentage of that instead of a percentage of the screen size

* Don't use percentages for font size because this refers to a percent of the parent font size

* ems === traditional typesetting blocks!! So cool :D
  * M was the biggest letter you could fit in one of these blocks
  * Directly relates to parent font size (will be 100% of the parent font size if 1em)

* Width is most important query for responsive design

* Some devices don't use responsive design so to fix this include a meta tag at the top of html (see viewport meta tag)

* To make logo responsive use a container div and set width and padding properties for that, then add a media query for that (under 500px for example)

**Implement flexwrap!**
  * Like inline-block above

* Can past css files into scss files and they will be valid but will include SASS options
  * Can use variables so they don't need to be repeated throughout the code
  * Applies tree structure formatting so styling becomes more intuitive (you can easily track nesting), selection of elements becomes much clearer and easier to track