#name #form #input #label #select #dropdown #textField #submit #required 


### Input form
email would have automatic validation ie checking for @
```html
<form action="">
<label for="username">Enter Username</label>
	<input type="text" id="username" name="username" required>
<br><br>
<label for="email">Enter email</label>
<input type="text" id="email" name="email">
<br><br>
<label for="password">Enter password</label>
<input type="password" id="password" name="password">

<p>Select your age</p>
<input type="radio" name="age" id="option-1" value="0-25">
<label for="option-1">0-25</label>
<br>
<input type="radio" name="age" id="option-2" value="26-50">
<label for="option-2">26-50</label>
</form>
```

### Radio Button
name has its purpose, if you want to have radio buttons and all their names are the same, then users can only choose 1 option

```html
<form action="">
<p>Select your age</p>
<input type="radio" name="age" id="option-1" value="0-25">
<label for="option-1">0-25</label>
<br>
<input type="radio" name="age" id="option-2" value="26-50">
<label for="option-2">26-50</label>
</form>
```


### Drop down menu
```html
<label for="question">Security questions:</label>
<select name="question" id="question">
	<option value="q1">What colour are your favourite pair of socks?</option>
	<option value="q2">If you could be a vegetable, what would it be?</option>
	<option value="q3">What is your best ever security questions?</option>
</select>
```

### Text field

```html
<textarea name="bio" id="bio" cols="30" rows="10"></textarea>
```

### Submit form
```html
<input type="submit" value="submit the form">
```