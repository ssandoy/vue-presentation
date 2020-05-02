
## General info
- v-directives. v-for, v-if etc in HTML.
- v-model directive that makes two-way binding between form input and app state a breeze:
```
Vue.component('todo-item', {
    // The todo-item component now accepts a
    // "prop", which is like a custom attribute.
    // This prop is called todo.
    props: ['todo'],
    template: '<li>{{ todo.text }}</li>'
  })
  
<div id="app-7">
       <ol>
         <!--
           Now we provide each todo-item with the todo object
           it's representing, so that its content can be dynamic.
           We also need to provide each component with a "key",
           which will be explained later.
         -->
         <todo-item
           v-for="item in groceryList"
           v-bind:todo="item"
           v-bind:key="item.id"
         ></todo-item>
       </ol>
     </div>
```


## GOOD
- Scoped css?
- Two-way databinding?
- Virtual DOM? Why is this good.

## BAD
- JavaScript and HTML separated. Hard to grasp context.
- Need to learn an extra DSL (Domain-Specific Language). HTML-templates
- React -> onClick={customFunction()} 
- Vue -> v-on:click="reverseMessage" Er det noe forskjell?..

## TODO
- How does typescript integrate with HTML?
- State, context, hooks etc.?
- TypeScript and Vue - props