<h2>Redux Toolkit</h2>

```
Must export reducer as well as Function in Slice File

Slice must includes three properties : 

Name: "Any String",

InitialState = {Object for Object based declarations}

reducers for functionality and Properties with state and Actions as Parameter where state is current values and action is passed values to App.

<p>Note 1: We have EXPORT reducer as const with "<SliceVariableName>.action" </p>
<p>Note 2: We have EXPORT reducer as default with "<SliceVariableName>.reducer" </p>


Steps: 
1. Create Store
2. Create const IntialState Object
3. Create Slice with name String, intialState, and reducers with FUNCTIONality and operations.
4.  export {reducers} with Note1
5. export slice with Note 2.

Note 3:
After Storing our IntialState into the "Store", we can access it by using useSelector()
for Example if we have IntialState as follows:

const intialState = {
todos : [ {id: useNanoId(), text: "Hello World"}]
}

then we access it it in some component as follows:

const todos = useSelector(state => state.todos)

now todos variable has value of todos "intialState" and update values of it.



Note 4:

for changing these stored value of object we can do it by use of "useDispatch()"
as follows:

const dispatch = useDispatch()

dispatch(addTodo(input))

```
