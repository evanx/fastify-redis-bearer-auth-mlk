# fastify-redis-bearer-auth-mlk

Fastify plugin for Redis-based auth via bearer session token.

```javascript
fastify.register(require('fastify-bearer-auth'), {
  auth: async (token, request) => {
    const client = await fastify.redis.hget(`session:${token}:h`, 'client')
    if (client) {
      request.client = client
      return true
    }
    return false
  },
  errorResponse: err => {
    return { code: 401, error: err.message }
  },
})
```

## Related

https://github.com/evanx/fastify-auth-mlk
