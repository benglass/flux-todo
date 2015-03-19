# Flux Todo Tutorial

Just `npm install` and `npm run build` when you're done. 

Use `npm start` to continuously build.

# How it Works

1. The TodoStore registers a callback with the AppDispatcher. It switches based on the action object's type and uses its private methods to modify the todo data and emit a change event.
2. When it mounts, the top level TodoApp component registers a change listener with the TodoStore
3. Whenever the TodoStore emits a change event, the TodoApp component sets its state using methods on the TodoStore to pull data (all todos, etc.)
4. Individual sub components use their event handlers to call methods on TodoActions class. 
	* For example the TodoTextField in the Header ends up calling TodoActions.create(text) when the enter key is pressed
5. TodoAction.create calls AppDispatcher.dispatch to dispatch an action of type TodoConstants.TODO_CREATE, passing along the text as part of the action object
6. AppDispatcher iterates over the registered callbacks (See step 1) and passses the action to each one,
