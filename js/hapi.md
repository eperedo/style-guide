### Understanding file name nomenclatures

* Modules: Represent a module of the project:

```bash
# Taking japi as example the modules can be:

products
sales
companies
```

* Actions: An action is hardly ligated to one of the CRUD operations

```bash
create
details (read one)
list (read many)
update
delete
```

* Type: The type represents the kind of content a file can have

```bash
route: A hapijs route definition
handler: A hapijs handler
pre: An object with many hapijs pre-handlers
plugin: A hapijs plugin definition
methods: An object with many hapijs server methods
validation: A hapijs validation using Joi
```

Following the above structure you can have the following folder structure for one module

```bash
# [module]-[action].[type].js
# /products folder
-- products-create.route.js
-- products-create.handler.js
-- products.test.js
-- products.methods.js
-- products.plugin.js
```

### Rules

1.  Modules must be created as plugins.

```javascript
function register(server) {
	// define routes, methods, etc
}

const plugin = {
	name: 'products',
	version: '1.0.0',
	register,
};

exports.plugin = plugin;
```

2.  Every endpoint who accepts parameters must be validated with Joi.

```javascript
// PATCH /products/{id}

{
	method: 'PATCH',
	options: {
		validate: {
			params: {
				id: Joi.number().required(),
			},
			payload: {
				// any parameter in the body
			},
			query: {
				// any parameter as a query string
			},
			headers: {
				// header validation
			},
		},
	},
	path: '/products/{id}',
}
```

3.  Any reference to an ID from the client must be validated inside a PRE. This rule also apply
    for any kind of validation which Joi cannot process (eg. async validations)

```javascript
// GET /products/{id}

{
	method: 'GET',
	options: {
		pre: [
			{
				assign: 'product',
				// this function must validate the ID parameter
				method: pre.getProductById,
			},
		],
	},
	path: '/products/{id}',
}
```

4.  Scenarios where you need tu return a 400 request must include an error code.

```javascript
const errorCodes = require('./error-codes');

async function handler(request, h) {
	if (request.param.id > 10) {
		return Boom.badRequest(errorCodes.NOT_GREATER_THAN_10);
	}
}
```
