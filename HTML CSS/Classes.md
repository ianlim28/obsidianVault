#class #cascade
Its a hook 

## descendent selector
```css
// parent to the left, child to the right

div p{
	color:purple;
}
```
`div .error` is different from `div.error`
`div .error` looks for the parent div and get any `error` class 
`div.error` gets the div with `error` class tag

## Attribute
Finding via tags with certain attributes
```css
a[href]{
	background-color: blue;
}
```

look for every anchor tag with an href attribute

or more specific
```css
a[href="https://wwww.theninja.co.uk"]{
	background-color: blue;
	text-transform: uppercase;
}
```

`*`  -> this will look for any href with the value

```css
a[href*="theninja"]{
	background-color: blue;
	text-transform: uppercase;
}
```

`$` -> this will look for anything that ends with it
```css
a[href$=".com"]{
	background-color: blue;
	text-transform: uppercase;
}
```

## The Cascade
inheritance and specificity
**Inheritance**
HTML elements can inherit CSS properties that are applied to their parents. Only fonts and text styles or colors are inherited, not margin and paddings


If you want to force inheritance like border or margin
```css
div p {
	border:inherit;
	margin: inherit;
	color: red;
}

p{
	color: orange;
}
```
the color of the p tag will be red due `specificity` because its more specific due to `div p` 