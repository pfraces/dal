# DAL

DOM Astraction Layer. A DOM manipulator micro-library

## Featuring

*   Less than 200 lines of annotated source
*   Chainable API
*   Dependency-free

# Example

```html
<div id="content">Bad news...</div>
<script src="dal.js"></script>
```

```javascript
var content = dal('content');

content
  .clear()
  .add('h1', 'It works!')
  .color('#F99', 'red')
  .size({ width: '300px', height: '300px' });

while (!content.full()) content.add('h1', 'foo');
content.add('h1', 'bar');
```

If you get

    Bad news...

please, [create an issue](https://github.com/pfraces/dal/issues) ;)

But if it works you'll end with something like this

![it works!](https://github.com/pfraces/dal/raw/master/itworks.png)

# Install

    $ npm install dal

# Status

DAL is a work-in-progress and is only intended for my personal use at this
time. 

# API

The object returned by the `dal` function is composed by an array of the
selected DOM elements and a collection of methods for manage that elements

There are a few boolean methods that obviously are not chainable but the
rest of methods are all chainable

**WIP:**

Currently the object returned by the `dal` function is just **one** DOM element
**augmented** with the collection of methods

## Selectors

### el = dal(selector)

Returns the element `el` selected by `selector` augmented with useful methods

If no `selector` is especified, a `div` element is created and is returned
being detached from the `document.body` (so is invisible)

You can create an empty element and attach it to the `document.body` with
`attach`

    dal().attach();

The `selector` can be

*   `string`: this returns the element with id = `selector`
*   `object`: if an DOM element is received, it will be augmented as well

`el` is augmented with the following methods

### el.sel(selector)

The selection function itself is available as method for do subselections
available

**Work in progress:**

Currently this method only returns an unaugmented DOM element. 

## Boolean methods

### el.inside(target)

Determines if `el` is descendant of `target`.

`target`: DOM Element

### el.full()

Determines if `el` is overflowing its bounds

### el.empty()

Determines if `el` has any child

## Element management methods

### el.attach()

Attaches `el` to the `document.body` if it was not attached yet

### el.detach()

Dettaches `el` from his parent if it has one

### el.add(newEl, content)

Attaches a new element to `el`

`newEl`:

*   String. An element is created and attached

        dal().add('h1', 'Hello world!')

*   DOM Element. An existing DOM element. In this case `newEl` is cloned and
    the clone is attached

### el.del(target)

If `target` is descendant of `el`, `target` is detached from his parent

### el.clear()

Removes all the children of `el`

### el.copy()

Returns a copy of itself excluding its children nodes

### el.clone()

Returns a clone of itself including its children nodes

## CSS layout methods

### el.show()

Makes `el` visible (is if is attached to the `document.body`)

### el.hide()

Makes `el` invisible and ignored by the layout, but behaving as when visible

### el.move(x, y)

Makes the element absotule positioned at `(x, y)`

## CSS style methods

### el.color(opts)

Changes the background and text color of `el`

`opts`: Object

*   `opts.bg`: Determines the backgroud color
*   `opts.fg`: Determines the text color

### el.size(opts)

Changes the size of `el`

`opts`: Object

*   `opts.width`: Determines the width of the element
*   `opts.height`: Determines the height of the element

## Tag attribute methods

### el.class.add(class)

Adds `class` as a CSS class of `el`

`class`: String

## Misc property methods

### el.html(html)

Sets the `innerHTML` value of the element

# Contribute

Get the sources at github: http://github.com/pfraces/dal

# License

(The MIT License)

Copyright (c) 2012 [pfraces](http://github.com/pfraces)

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the 'Software'), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
