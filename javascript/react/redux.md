# React redux

Redux est une librairie, un système de centralisation des données et des actions. 
Elle nous permettra de gérer les states qui seront donc accessibles depuis partout dans l'application. les informations sont renvoyés sous forme de props.
Le payload représente les données (un article par exemple) et les actions (poste cet article). Reducer permet de mettre à jour le store.

1. Le component demande une information au store qui est renvoyé sous forme de props
2. On fait une action pour mettre à jour l'information et le dispatcher partout
3. Cette action sera mis à jour par reducer
4. Les selecteurs permettent de choisir l'information qu'on veut obtenir

Fichier todos.js :

````
const initialiseState = {
    allIds: [],
    byIds: {},
};

export const todos = (state = initiaState, action) => {
  switch (action.type) {
    case ADD_TODO: {
      const {id, content} = action.payload;
      return {
        ...state,
        allIds: [...state.allIds, id],
        byIds: {
            ...state.byIds,
            [id]: {
              content,
              completed: false
            }
        }
      }
    }

    case TOGGLE_TODO: {
      const {id} = action.payload;
      return {
        ...state;
        byIds: {
          ...state.byIds,
          [id]: {
              ...state.byIds[id],
              completed: !state.byIds[id].completed,
          },
        }
      }
    }
    default: 
      return state;
  }
};
````

Fichier action.js : 

````
import {ADD_TODO, TOGGLE_TODO} from "./actionTypes";

let nextTodoId = 0;

export const addTodo = content => {
    return {
        type: ADD_TODO?
        payload: {
            id: ++nextTodoId,
            content,
        }
    }
};

export const toggleTodo = id => ({
    return {
        type: TOGGLE_TODO?
        payload: {
            id
        }
});
````

Fichier selector.js :

````
export const getTodoState = store => store.todos;

export const getTodoList = store =>
    getTodoState(store) ? getTodoState(store).allIds : [];

export const getTodoById = (store, id) =>
    getTodoState(store) ? {...getTodoState(store).byIds[id], id} : {};

export const getTodos = store =>
    getTodoList(store).map(id => getTodoById(store, id));
````

Fichier store.js :

````
import {createStore} from 'redux';
import rootReducer from "./reducers";

export default createStore(rootReducer)
````

Fichier index.js :

````
import {combineReducers} from "redux";
import {todos} from "./todos";

export default combineReducers({todos})
````

Pour avoir le store dans toute l'application : 

````
ReactDOM.render(
    Provider store={store}>
        <App/>
    </Provider>,
    document.getElementById('root'));
````

Fichier App.js : 

````
class App extends React.Component {
    render() {
        return <div className="todo-app">
            <h1>Todo List</h1>
            <AddTodo/>
            <TodoList/>
        </div>
    }
}

export default App;
````

Fichier AddTodo :

````
class AddTodo extends Rect.Component {
    constructor(props) {
       super(props);
       this.state = { input "" };
    }
    updateInput = input => {
        this.setState({input})
    }
    handleAddTodo = () => {
        this.props.addTodo(this.state.input);
        this.setState({input: ""});
    }

    render() {
        return (
            <div>
                <input
                    onChange={e => this.updateInput(e.target.value)}
                    value={this.state.input}
                />
                <button className="add-todo" onClick={this.handleAddTodo}>
                    Add Todo
                </button>
            </div>
        );
    }
}

export default connect(
    null,
    {addTodo}
)(AddTodo);
````

Fichier TodoList :

````
const TodoList = ({todos}) => {
    return <div>
        <div>
            {(todos && todos.length ? todos.length : "vide") + ''}
        </div>
        <ul className="todo-list">
            {todos && todos.length
                ? todos.map((todo, index) => {
                    return <Todo key={`todo-${todo.id}`} todo={todo}/>
                })
                : "No todos yay!"
        </ul>
    </div>
};

const mapStateToProps = state => {
    const todos = getTodos(state);
    console.log(todos)
    return {todos};
}

export default connect(mapStateToProps)(TodoList);
````

Fichiet todo.js :

````
const Todo = ({todo, toggleTodo}) => (
    <li className="todo-item" onClick={() => toggleTodo(todo.id)}>
        {todo && todo.completed ? "fait" : "à faire"}{" "}
        {todo.content}
    </li>
);

export default connect(
    null, 
    {toggleTodo}

)(Todo);
````
