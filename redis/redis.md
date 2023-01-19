# Redis Cheat Sheet

## Installation
Installation on macOS (using home brew)
```zsh
brew install redis
```
Check installation (run redis server)
```zsh
redis-server
```

## Basic commands
Testing these commands could be done by opening a new terminal (still running redis-server) and typing redis-cli. The connection against the redis server will be automatically set up.

Setting key/value pair
```zsh
SET name Robin
```
Getting value for key (notice redis returns a string value)
```zsh
GET name #"Robin"
```
Deleting key/value pair
```zsh
DEL name #returns true like so: (integer) 1
```
Getting a null val
```zsh
GET name #returns null like so: (nil)
```
Delete all key value pairs:
```zsh
flushall
```
Get all keys
```zsh
KEYS *
```
Setting expiration on key/value pair
```zsh
expire name 10 #expiration of 10 seconds
```
Getting time to live (ttl) - time left on key/value pair before it is destroyed
```zsh
ttl name #returns ttl in seconds
```
When the key has expired it will be deleted. Thus, getting value for key will return (nil).

Expiration on setting (setex keyname expiration-time-in-sec value)
```zsh
setex name 10 robin
```

Push a value to the left or start of list (lpush)
```zsh
lpush friends roboto
```

Getting all items in list (cannot use get since it only works for string types)
```zsh
lrange friends 0 -1
```

Pushing to right or end of list (rpush)
```zsh
rpush friends robinho
```

Poping from start (lpop)
```zsh
lpop friends
```

Poping from end (rpop)
```zsh
rpop friends
```

Adding an element to a set (array-like structure, but with unique elements only)
```zsh
sadd hobbies "going to gym" #quote for strings with more than one word
```
Since a set is a unique set of values, adding "going to gym" again will give us **(integer) 0** (false), since it already exist within the set.

Getting all values from set
```zsh
smembers hobbies
```

Remove val from set
```zsh
srem hobbies "going to gym"
```

Adding value to a hashset. In this case: setting the name of a person to the value of robin.
```zsh
hset person name robin
```

Getting value from hashset
```zsh
hget person name
```

Get all fields and values from key (hashset)
```zsh
hgetall person
```

Delete a specific property from hashet
```zsh
hdel person name #deletes name from person
```

See if fields exists in hashset:
```zsh
hexists person name
```

More on [Redis Commands](https://redis.io/commands/)