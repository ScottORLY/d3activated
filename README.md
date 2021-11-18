# __d3activated__

![](https://github.com/scottorly/d3activated/workflows/d3activated/badge.svg)
[![npm version](https://badge.fury.io/js/d3activated.svg)](https://badge.fury.io/js/d3activated)

Small javascript library for transpiling [JSX](https://reactjs.org/docs/react-api.html#createelement) to [DOM Elements](https://developer.mozilla.org/en-US/docs/Web/API/Element) and optionally wrapping the element in d3-selection.

## Installation

`npm i -D d3activated`

__d3activated__ provides functions for use with bundlers to transpile JSX to plain DOM elements.

## Usage

The following JSX
```javascript
<div />
```
transpiles to [HTMLDIVElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLDivElement).

Add classes, ids, & common attributes
```javascript
<ul className={styles.list} />

<img src={imgSrc} />
```

The eventListener attribute takes an array that contains exactly 2 elements: the event type and the function.
```javascript
<span eventListener={['click', e => {
    console.log(e)
}]} />
```

Use a function as an element type to create functional components with custom attributes.
```javascript
const Component = ({ attributes: { items }}) => (
    <ul>
        {items.map(item => <li>{item.name}</li>)}
    </ul>
)

const items = ['foo' 'bar']

<Component items={items} />
```

Pass children to any element
```javascript
const Component = ({ children }) => (
    <div>
    { children }
    </div>
)

<Component>
    <div></div>
    Hey! These divs aren't going to nest themselves!
</Component>
```
