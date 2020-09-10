# symbolism
RPC-based HTTP micro-framework with using javascript's symbol magics

Stage: idea

### Demo
```js
import { statusCodeSym, bodySym, urlSym } from 'symbolism'

export function getPosts() {
   return Posts.find({})
}

export function createPost(params) {
   return Posts.create(params)
}

export function echoUrl(params) {
   return {
      [bodySym]: params[url],
      [statusCodeSym]: 200
   }
}

export function echoHeaders(params) {
   return {
      [bodySym]: params[headersSym],
   }
}



symbolism.get('/posts', getPosts)
symbolism.post('/posts', createPost)
symbolism.get('/url', echoUrl)
symbolism.get('/headers', echoHeaders)

```

### Why?

- no more `request` - `reply/response` objects and its sucks
- crazy easy to test, beacuse there's no need to mock `request/reply` objects
- everything is just simple functions - no extra dependencies in code
