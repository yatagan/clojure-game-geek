
# CPU 100% issue:

```
$ lein repl
user=> (start)
```
Run subscriptions in graphiql:

## Good case

```
subscription ($user_id: ID!) {
  compute(user_id: $user_id) {
    id
    member_name
  }
}
```

variables:
```
{
  "user_id": "dummy"
}
```

It works fine, returns dummy result.

## Bad case

```
subscription ($user_id: ID) {
  compute(user_id: $user_id) {
    id
    member_name
  }
}
```

variables:
```
{
  "user_id": "dummy"
}
```

It's the same query, but with malformed arguments (without exclamation mark).

Check your CPU :(

