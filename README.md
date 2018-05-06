1.  Semicolons are required, **always**.

```bash
// BAD
const name = 'Eduardo'
```

```javascript
// GOOD
const name = 'Eduardo';
```

2.  **const** and **let** for variable declaration

```javascript
// BAD
var name = 'Eduardo';
var lastname = 'Peredo';
lastname = 'Rivero';
```

```javascript
// GOOD
const name = 'Eduardo';
let lastname = 'Peredo';
lastname = 'Rivero';
```

3.  Prefer **map, filter, reduce** over **forEach** as much as you can

```javascript
// BAD
const values = [1, 2, 3];
let sum = 0;

values.forEach(value => {
	sum += value;
});
```

```javascript
// GOOD
const values = [1, 2, 3];
const sum = values.reduce((acum, value) => (acum += value), 0);
```

4.  Use lowerCamelCase notation to write code

```javascript
// BAD
function GenerateName() {
	const MyName = 'A bad name';
	return MyName;
}
```

```javascript
// GOOD
function generateName() {
	const myName = 'Eduardo';
	return myName;
}
```

5.  Use property shorthand all the time

```javascript
// BAD
const name = 'Eduardo';

const awesomePerson = {
	name: name,
};
```

```javascript
// GOOD
const name = 'Eduardo';

const awesomePerson = {
	name,
};
```

6.  Write object properties in alphabetic order ❗️

```javascript
// BAD
const awesomePerson = {
	weight: 63,
	height: 1.69,
	age: 31,
	name: 'Eduardo',
};
```

```javascript
// GOOD
const awesomePerson = {
	age: 31,
	height: 1.69,
	name: 'Eduardo',
	weight: 63,
};
```

7.  Always use arrow-function for anonymous functions

```javascript
// BAD
axios.get('/users').then(function(res) {
	return res.data;
});
```

```javascript
// GOOD
axios.get('/users').then(res => res.data);
```

8.  Use trailing comma always

```bash
// BAD
const person = {
	name: 'Eduardo',
	age: 20
};
```

```javascript
// GOOD
const person = {
	name: 'Eduardo',
	age: 20,
};
```

9.  Use spread operator for clone/copy objects

```javascript
// BAD
const myObj = { name: 'Eduardo' };
const newObj = myObj;
```

```javascript
// GOOD
const myObj = { name: 'Eduardo' };
const newObj = { ...myObj };
```

10. Prefer ternary operator for short conditionals

```javascript
// BAD
if (number > 10) {
	result = isGreatherThanTen();
} else {
	result = isNotGreatherThanTen();
}
```

```javascript
// GOOD
result = number > 10 ? isGreatherThanTen() : isNotGreatherThanTen();
```

11. Use normal function definitions for functions inside objects

```javascript
// BAD
const person = {
	name: 'Eduardo',
	greeting() {
		return `Hello ${this.name}`;
	},
};
```

```javascript
// GOOD

function greeting() {
	return `Hello ${this.name}`;
}

const person = {
	name: 'Eduardo',
	greeting,
};
```

12. Always define function before they are used

```javascript
// BAD

const person = {
	name: 'Eduardo',
	greeting,
};

function greeting() {
	return `Hello ${this.name}`;
}
```

```javascript
// GOOD

function greeting() {
	return `Hello ${this.name}`;
}

const person = {
	name: 'Eduardo',
	greeting,
};
```

13. Always put **use strict** at the start of the file (nodejs only)

```javascript
// BAD
module.exports = someModule;
```

```javascript
// GOOD
'use strict';

module.exports = someModule;
```

14. Use **object/array destructuring** as much as you can

```javascript
// BAD
const person = {
	age: 20,
	name: 'Eduardo',
	weight: 20,
};

const age = person.age;
const name = person.name;
const weight = person.weight;
```

```javascript
// GOOD
const person = {
	age: 20,
	name: 'Eduardo',
	weight: 20,
};

const { name, age, weight } = person;
```

```javascript
// BAD
const values = [2, 4, 6];
const two = values[0];
const four = values[1];
const six = values[2];
```

```javascript
// GOOD
const values = [2, 4, 6];
const [two, four, six] = values;
```

15. Template literals for concatenate values

```javascript
// BAD
const name = 'Eduardo';
const lastName = 'P. Rivero';

const fullName = name + lastName;
```

```javascript
// GOOD
const name = 'Eduardo';
const lastName = 'P. Rivero';
const fullName = `${name} ${lastname}`;
```

16. Use **Number** over **parseInt** for type casting

```javascript
// BAD
const ageInString = '30';
const ageInNumber = parseInt(ageInString);
```

```javascript
// GOOD
const ageInString = '30';
const ageInNumber = Number(ageInString);
```

17. Use **===** to avoid **automatic coersion**

```javascript
// BAD
if (value == value2) {
}
```

```javascript
// GOOD
if (value === value2) {
}
```

❗️ = There are exceptions over this rule
