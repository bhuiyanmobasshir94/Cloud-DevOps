```
redis.exceptions.ReadOnlyError: You can't write against a read only replica.

> docker-compose exec cache redis-cli -h 127.0.0.1 -p 6379 slaveof no one
```
