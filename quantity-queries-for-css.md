# Quantity Queries for CSS

## Dynamic content

* Responsive webdesign variable: space (content is constant)


### :only-child
```html
<!-- Success -->
<div>
	<button></button>
</div>
<!-- No success -->
<div>
	<button></button>
	<button></button>
</div>
```

```css
/*
Means fewer than two
*/
div button:only-child {

}
```

### :not(:only-child)
```html
<!-- No success -->
<div>
	<button></button>
</div>
<!-- Success -->
<div>
	<button></button>
	<button></button>
</div>
```

```css
/*
Means more than one
*/
div button:not(:only-child) {

}
```

### :nth-last-child(n):first-child

Works like js `&&` so what it says is: number away from last child and is also first child

```js
// condition:condition
const firstChild = 'first'
const secondChild = 'second'

if(firstChild && secondChild){
	return 'styling'
}
```



```html
<!-- No success -->
<div>
<!-- 7 buttons -->
	<button></button>
	<button></button>
	<button></button>
	<button></button>
	<button></button>
	<button></button>
	<button></button>
</div>
<!-- Success -->
<div>
<!-- 6 buttons -->
	<button></button>
	<button></button>
	<button></button>
	<button></button>
	<button></button>
	<button></button>
</div>
```

```css
/*
Select only first child if amount of buttons is 6
*/
div button:nth-last-child(6):first-child {

}
/*
Select only first child if amount of buttons is 6 and select all its siblings
*/
div button:nth-last-child(6):first-child,
div button:nth-last-child(6):first-child ~ div button
{

}
```

1n = every1 (select everyone)
2n = every even element
3n = select 3rd 6th 9th etc


```css
/*
Select all from the 6th onward
*/
:nth-child(n+6) {

}

/*
Select all from the 6th backwards so start at the last element and count backwards
*/
:nth-last-child(n+6) {

}

/*
Select all from the 6th backwards so start at the last element and count backwards
This also means dont style the rest
, = &&
So this says: select all from the 6th backwards and all its siblings if there are 6 or more items
The last line of selector says: select the 6th backwards and all its siblings so if the 6th element does not exist, it wont select anything
*/
:nth-last-child(n+6),
:nth-last-child(n+6) ~ button
{

}
/*
Same as above but reverse selection direction
select fewerthan and equal to
*/
:nth-last-child(-n+6),
:nth-last-child(-n+6) ~ button
{

}

/*
Same as above but first-child is also the 6th child
select first child and children before them...(impossible)
and all its siblings from the 6th spot
If there are 7 items the 6th item is not the first-child so it wont work
*/
:nth-last-child(-n+6):first-child,
:nth-last-child(-n+6):first-child ~ button
{

}

/*
Child vs Type

Child = every element
Type = every element of that html-tag
*/

```
