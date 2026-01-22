# Maybe

## From stackoverflow

https://stackoverflow.com/questions/60616353/generate-a-list-of-24-entries-and-check-if-content-is-present-in-object

```
HTML

<div id="app">
  <div v-for="hourNumber in 24" class="hour-entry">
    <div
      class="product"
      v-for="(product, idx) in products"
      v-if="product.startTimeHour === hourNumber"
      key="product.id"
    >
      {{ product.name }}
    </div>
    <div v-if="getProductsNumPerHour(hourNumber) === 0">
      No entry for startTimeHour [{{ hourNumber }}]
    </div>
  </div>
</div>

CSS
.hour-entry {
  border: 1px solid silver;
  border-radius: 3px;
  margin: 5px 0;
  padding: 10px 15px;
}
.product {
  background-color: #d5e7f0;
  padding: 5px 10px;
}

JS VUE
new Vue({
	el: '#app',
  
  data: {
  	products: [
    	{
      	id: 1,
        name: 'Product One',
        startTimeHour: 4
      },
       {
      	id: 2,
        name: 'Product Two',
        startTimeHour: 10
      },
      {
      	id: 3,
        name: 'Product Three',
        startTimeHour: 15
      },
      {
      	id: 4,
        name: 'Product Four',
        startTimeHour: 15
      },
    ]
  },
  
  methods: {
  	getProductsNumPerHour (hourNum) {
    	return this.products.filter(prod => {
      	return prod.startTimeHour === hourNum
      }).length
    }
  }
})

```

## https://thecodingpie.medium.com/how-to-build-a-todo-list-app-with-javascript-and-local-storage-a884f4ea3ec

JS script.js

// select everything

// select the todo-form
const todoForm = document.querySelector('.todo-form');

// select the input box
const todoInput = document.querySelector('.todo-input');

// select the <ul> with class="todo-items"
const todoItemsList = document.querySelector('.todo-items');

// array which stores every todos
let todos = [];

const todo = {
  id: Date.now(),
  name: "any",
  completed: false
  }:
  
