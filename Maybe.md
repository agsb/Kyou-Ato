# Maybe

## Internal Storage WEB

https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage

The following snippet accesses the current domain's local Storage object and adds a data item to it using Storage.setItem().
js

localStorage.setItem("myCat", "Tom");

The syntax for reading the localStorage item is as follows:
js

const cat = localStorage.getItem("myCat");

The syntax for removing the localStorage item is as follows:
js

localStorage.removeItem("myCat");

The syntax for removing all the localStorage items is as follows:
js

localStorage.clear();

## Geolocation

The GeolocationCoordinates interface doesn't inherit any methods.

GeolocationCoordinates.toJSON()

Returns a JSON representation of the GeolocationCoordinates object and enables serialization with JSON.stringify().


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
  };

  // add an eventListener on form, and listen for submit event
  todoForm.addEventListener('submit', function(event) {

  // prevent the page from reloading when submitting the form
  event.preventDefault();

  // call addTodo function with input box current value
  addTodo(todoInput.value); 
  });

  // function to add todo
function addTodo(item) {
  // if item is not empty
  if (item !== '') {
    // make a todo object, which has id, name, and completed properties
    const todo = {
      id: Date.now(),
      name: item,
      completed: false
    };

// then add it to todos array
    todos.push(todo);
	// then renders them between <ul>
    // renderTodos(todos); 	
	// then add to local storage
	addToLocalStorage(todos);

// finally clear the input box value
    todoInput.value = '';
  }
}

// function to render given todos to screen
function renderTodos(todos) {
  // clear everything inside <ul> with class=todo-items
  todoItemsList.innerHTML = '';
// run through each item inside todos
  todos.forEach(function(item) {
    // check if the item is completed
    const checked = item.completed ? 'checked': null;
// make a <li> element and fill it
    // <li> </li>
    const li = document.createElement('li');
    // <li class="item"> </li>
    li.setAttribute('class', 'item');
    // <li class="item" data-key="20200708"> </li>
    li.setAttribute('data-key', item.id);
    /* <li class="item" data-key="20200708"> 
          <input type="checkbox" class="checkbox">
          Go to Gym
          <button class="delete-button">X</button>
        </li> */
    // if item is completed, then add a class to <li> called 'checked', which will add line-through style
    if (item.completed === true) {
      li.classList.add('checked');
    }
li.innerHTML = `
      <input type="checkbox" class="checkbox" ${checked}>
      ${item.name}
      <button class="delete-button">X</button>
    `;
    // finally add the <li> to the <ul>
    todoItemsList.append(li);
  });
}

/*
 <li class="item" data-key "1594003233171">
 <input class="checkbox" type="checkbox"> Go to Gym
 <button class="delete-button"> X </button>button>
 </li>li>
 if (item.completf = true) { li.classList.add('checked'); }
*/

// function to add todos to local storage
function addToLocalStorage(todos) {
  // conver the array to string then store it.
  localStorage.setItem('todos', JSON.stringify(todos));
  // render them to screen
  renderTodos(todos);
}

  }:
  
// function helps to get everything from local storage
function getFromLocalStorage() {
  const reference = localStorage.getItem('todos');
  // if reference exists
  if (reference) {
    // converts back to array and store it in todos array
    todos = JSON.parse(reference);
    renderTodos(todos);
  }
}
// initially get everything from localStorage
getFromLocalStorage();

// after that addEventListener <ul> with class=todoItems. Because we need to listen for click event in all delete-button and checkbox
todoItemsList.addEventListener('click', function(event) {
  // check if the event is on checkbox
  if (event.target.type === 'checkbox') {
    // toggle the state
    toggle(event.target.parentElement.getAttribute('data-key'));
  }
// check if that is a delete-button
  if (event.target.classList.contains('delete-button')) {
    // get id from data-key attribute's value of parent <li> where the delete-button is present
    deleteTodo(event.target.parentElement.getAttribute('data-key'));
  }
});

// toggle the value to completed and not completed
function toggle(id) {
  todos.forEach(function(item) {
    // use == not ===, because here types are different. One is number and other is string
    if (item.id == id) {
      // toggle the value
      item.completed = !item.completed;
    }
  });
addToLocalStorage(todos);
}
// deletes a todo from todos array, then updates localstorage and renders updated list to screen
function deleteTodo(id) {
  // filters out the <li> with the id and updates the todos array
  todos = todos.filter(function(item) {
    // use != not !==, because here types are different. One is number and other is string
    return item.id != id;
  });
// update the localStorage
  addToLocalStorage(todos);
}



