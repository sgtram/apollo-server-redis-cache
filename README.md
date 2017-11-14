# apollo-server-redis-cache

## Installation

```
$ npm install apollo-server-redis-cache
```

## Usage

Start redis server
```
$ redis-server
```

```javascript
import express from 'express'
import { graphqlExpress } from 'apollo-server-express'
import apolloServerRedisCache from 'apollo-server-redis-cache'

const _schema = /* your schema */
const PORT = 3000;

const app = express();

const redisCache = new apolloServerRedisCache({ cache: true, key: 'asrc', ttl: 60 });

app.use(
  '/graphql',
  bodyParser.json(),
  redisCache.middleware(),
  graphqlExpressRedis({ schema: _schema })
);

app.listen(PORT);
```