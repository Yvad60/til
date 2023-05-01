## 31st March 2023

### When working with Redux toolkit query avoid getting state in your query functions instead select the state in your components and sent them in your query hook

Let’s say you are working with Redux toolkit and you want to fetch a user by their ID. You need the id argument to know which user fetch when sending the query. In this case, it is recommended to avoid accessing the state directly in the query function

```js
// Don't do this
import store from '../store/store.js'

//... other lines of code
endpoints: (builder) => ({
    getUserById: builder.query({
      query: () => {
        const { userId } = store.getState() // This is a mistake.
        return `/users/${userId}`
    }
}),

```

The reason this is not recommended is that Redux uses the argument passed to it to define the cache key and whenever it is called with the same arguments it will not make a fetch
if you access the user id in the query function itself you would always call your query without passing any argument

```js
import { useGetUSerByIdQuery } from '../api/apiSlice'

const MyComponent = () => {
  const { data, isLoading } = useGetUSerByIdQuery() //same as calling useGetUSerByIdQuery(undefined) and you will get data only for the first time 
}
```

Every time the `useGetUSerByIdQuery` will be always called with `undefined` Redux toolkit will assume that nothing changed and doesn’t perform another request.

Instead, it is recommended to select the state in your component and pass it down to your query hook so that every time the id is changed the request will be made successfully

```js
// do this instead
import { useSelector } from 'react-redux'
import { useGetUSerByIdQuery } from '../api/apiSlice'

const MyComponent = () => {
  const { userId } = useSelector(state => state)
  const { data, isLoading } = useGetUSerByIdQuery(userId) //same as calling useGetUSerByIdQuery(undefined) and you will get data only for the first time 
}
```

```js
// update the apiSlice like this 

endpoints: (builder) => ({
    getUserById: builder.query({
      query: (userId) => `/users/${userId}` // userId is being passed in the query 
}),

```
