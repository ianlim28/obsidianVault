#after

[mozilla developer source](https://developer.mozilla.org/en-US/docs/Web/CSS/::after)
checkout the output on the web

`::after` creates a [pseudo-element](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) that is the last child of the selected element. It is often used to add cosmetic content to an element with the [`content`](https://developer.mozilla.org/en-US/docs/Web/CSS/content) property. It is inline by default.

```html
<p>The sailfish is named for its sail-like dorsal fin and is widely considered the fastest fish in the ocean. <a href="https://en.wikipedia.org/wiki/Sailfish">You can read more about it here</a>.</p>

<p>The red lionfish is a predatory scorpionfish that lives on coral reefs of the Indo-Pacific Ocean and more recently in the western Atlantic. <a href="" class="dead-link">You can read more about it here</a>.</p>
```

```css
a::after {
    content: ' (' attr(href) ')';
}

.dead-link {
    text-decoration: line-through;
}

.dead-link::after {
    content: url('../../media/warning.svg');
    display: inline-block;
    width: 12px;
    height: 12px;
}
```


**Single colon and double colon**

The reason why the CSS selector for the placeholder text uses two colons (::) instead of one colon (:) is because it is a pseudo-element selector. Pseudo-elements are used to style parts of an element, such as the placeholder text in an input element. In this case, the placeholder text is being styled with the color rule to set it to semi-transparent white. The double colon (::) is used to differentiate between pseudo-classes (which use a single colon) and pseudo-elements.

```css
.top input:focus {
	color: white;
	font-size: 15px;
}

.top input::placeholder {
	color: rgba(255, 255, 255, .5);
}
```

