# API Design

## Objects

migrated to [objects page](./objects.md)

## Paths

### Path `/`

GET

fetch a table about all paths' status (available or not)

```javascript
{
    "path1": true, // response of path1
    "path2": false, // response of path2
                 // ...
    "pathN": {}, // response of pathN
}
```

### Path `/config`

migrated to [config page](./config.md)

### Path `/pool`

migrated to [pool page](./pool.md)

### Path `/miner`

migrated to [miner page](./miner.md)

#### Path `/payments`

TODO

#### Path "/algorithm"

We are recommend to deploy different algorithm stratum port with different
mining pool instance, so it means the frontend page have to deal with
multi-api-server circumstance.

-   GET

Get all algorithms

-   POST

POST on '/algorithm' is meaning for being compatible multi-algorithms coins

```json
{
    "name": "scrypt",
    "variant": "ltc-origin",
    "blobType": ""
}
```

#### Path "/lucky"

the lucky table

lucky = 1 / effort

More lucky means more benefit when same hashrate

-   GET

```json
{
    "1d": 0.99,
    "7d": 1.01,
    "1m": 1.11
}
```

-   POST

e.g.

request with body, aiming to fetch luckies between these 14 days.

```json
{
    "start": "1-Jan-2020",
    "end": "10-Jan-2020"
}
```

pool returns a list

```json
["1.1", "1.11", "0.9", "0.98", "0.7", "1.5", "1.11", "0.9", "0.98", "1"]
```

#### Path "/effort"

the effort table

effort = 1 / lucky

More lucky means more benefit when same hashrate

-   GET

```json
{
    "1d": 1.01,
    "7d": 0.99,
    "1m": 0.91
}
```

-   POST

e.g.

request with body, aiming to fetch efforts between these 14 days.

```json
{
    "start": "1-Jan-2020",
    "end": "10-Jan-2020"
}
```

pool returns a list

```json
["1.1", "1.11", "0.9", "0.98", "0.7", "1.5", "1.11", "0.9", "0.98", "1"]
```
