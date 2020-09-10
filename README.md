# symbolism
RPC-based HTTP micro-framework by using javascript's symbol magics

Stage: idea

### Demo
```js
function getPosts() {
   return Posts.find({})
}

function createPost(params) {
   const response = await Posts.create(params)
   response[statusCodeSym] = 201
   return response
}

function echoUrl(params) {
   return {
      [bodySym]: params[urlSym],
      [statusCodeSym]: 200
   }
}



symbolism.get('/posts', getPosts)
symbolism.post('/posts', createPost)
symbolism.get('/url', echoUrl)
```

### Why?

- no more `request` - `reply/response` objects and its sucks
- crazy easy to test, beacuse there's no need to mock `request/reply` objects
- everything is just simple functions - no extra dependencies in code
