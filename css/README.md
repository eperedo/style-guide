1.  Use kebab case for naming your css code

```css
/* BAD */

.myClass {
	cursor: pointer;
	height: 200px;
	width: 100px;
}
```

```css
/* GOOD */

.my-class {
	cursor: pointer;
	height: 200px;
	width: 100px;
}
```

2.  Use **css** variables instead **scss** ones

```css
/* BAD */
$colors = (
	myColor: #f829ff,
)
```

```css
/* GOOD */
:root {
	my-color: #f829ff;
}
```

3.  Order css properties in alphabetically order

```css
/* BAD */
.my-class {
	width: 100px;
	cursor: pointer;
	height: 200px;
}
```

```css
/* GOOD */
.my-class {
	cursor: pointer;
	height: 200px;
	width: 100px;
}
```

4.  Keep nested classes at two/three levels maximun

```css
/* BAD */
.my-module {
	.nested-module {
		.another-nested-module {
			.other-more {
			}
		}
	}
}
```

```css
/* GOOD */
.my-module {
	.nested-module {
	}
}
```

5.  Avoid ID selectors

```css
/* BAD */
#my-module {
}
```

```css
/* GOOD */
.my-module {
}
```
