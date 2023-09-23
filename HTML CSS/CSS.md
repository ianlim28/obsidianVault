#selector #inline #block #margin #padding #zindex #focus #valid #invalid #buttons


![[Screenshot 2023-08-01 at 20.22.46.png]]

## Inline elements
sits next to each other for as far as it can go
buttons is also inline
![[Screenshot 2023-08-01 at 20.35.48.png]]

## Block element 
h1 is block element 
![[Screenshot 2023-08-01 at 20.37.08.png]]


## Margin and padding 
Block elements have margin around them, and inline elements only have margins to the left and right 

Block element with margin and padding 
![[Screenshot 2023-08-01 at 20.43.16.png]]

Inline element with margin and padding 
![[Screenshot 2023-08-01 at 20.43.56.png]]

## Inline-block

mix the best of both worlds, it will still sit next to other elements on the page but itll behave like a block

```css
span{
	display:inline-block;
	margin: 20px;
	padding: 20px;
}
```

## Z index 
The `z-index` property in CSS determines the stacking order of positioned elements. It specifies the order in which elements are displayed when they overlap on the z-axis (depth). Elements with a higher z-index value will appear on top of elements with a lower z-index value. AKA Brings things forwards or backwards

The z-index property only takes effect for elements that have a position value of relative, absolute, or fixed. By default, all elements have a z-index value of auto, which means they will be stacked according to the order they appear in the HTML document.

## Focus & Valid:Invalid
```css
.content form label input:focus:invalid {
	font-size: 1.6rem;
	border-bottom: 2px solid var(--color-sec);
}
```

## Sibling ~
 the code targets three different elements with unique IDs: `login`, `register`, and `reset`. The code applies the CSS selector `:checked` to these elements, which are typically used for checkboxes or radio buttons.

The code utilizes the general sibling combinator `~` to select the sibling elements that come after the checked elements. In this case, it selects the `label` elements with class names `login`, `register`, and `reset` which are inside the `nav` element.
```css
#login:checked ~ nav label.login,
#register:checked ~ nav label.register,
#reset:checked ~ nav label.reset {
	color: #fff;
}
```

this is the html for the above css
```html
<h1>Google Direct Download Link Generator</h1>
<input type="radio" id="login" name="tab" checked>
<input type="radio" id="register" name="tab">
<input type="radio" id="reset" name="tab">
<nav>
	<label for="login" class="login">
	<i class="fas fa-sign-in-alt"></i>
	
	Paste Link
	</label>
	<label for="register" class="register">
	<i class="fas fa-headphones-alt"></i>
	
	Embed Audio
	</label>
	<label for="reset" class="reset">
	<i class="fas fa-photo-video"></i>
	
	Embed Video/Docs
	</label>
	<div class="slide"></div>
</nav>
```
