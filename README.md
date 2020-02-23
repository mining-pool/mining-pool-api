# API Design

## Objects

### Algorithm

```json5
{
  "name": "scrypt",
  "variant": "ltc-origin", // an additional remark for algorithm name
  "blobType": "bitcoin" // maybe cryptonote v1/v2, forknote v1/v2, ethereum or any other coin's own blobType, just used as an additional remark for variant. Pool software can keep null or "".
}
```

### Port

port is an object contains the configs for guiding users to quick start mining on your pool

```json
{
  "host": "192.168.1.101",
  "port": 10086,
  "algorithm": {
    "name": "scrypt",
    "variant": "ltc-origin",
    "blobType": ""
  },
  "ssl": true,
  "difficulty": 0.02,
  "fee": 0,
  "desc": "Low-End Cpu and Gpu"
}
```

### Block

```json
{
  "difficulty": 539702861270356,
  "hash": "8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
  "height": 1187801,
  "reward": 4129400000000,
  "timestamp": 1582458302
}
```

## Paths

### Path "/"

fetch all followings in an array

```text
{
  "path1": thePath1ResponseJson,
  "path2": thePath2ResponseJson,
  ...
}
```

### Path "/network"

```json
{
  "height": 1187802,
  "hashrate": 3366733275,
  "difficulty": 538996687554816,
}
```

### Path "/ports"

- GET

return

```json
[
  {
    "host": "192.168.1.101",
    "port": 10086,
    "ssl": true,
    "algorithm": {
      "name": "scrypt",
      "variant": "ltc-origin",
      "blobType": ""
    },
    "difficulty": 0.02,
    "fee": 0,
    "desc": "Low-End Cpu and Gpu"
  },
  {
    "host": "192.168.1.102",
    "port": 10088,
    "ssl": true,
    "algorithm": {
      "name": "scrypt",
      "variant": "ltc-origin",
      "blobType": ""
    },
    "difficulty": 2,
    "fee": 0,
    "desc": "Hign-End rigs"
  }
]
```

### Path "/pool"

- GET

Stats shows the pool basic mining status.

```json
{
  "minerCount": 10,
  "rigCount": 20,

  "totalMined": 14,
  "totalHashrates": 3366733275,
  "totalDiff":9506129270212336,
  "totalShares":8918601904388584,
}
```

### Path "/blocks"

- GET/POST

on default, return 25 items as maxium

Can also POST with limition

Get all blocks mined between 1-Jan-2020 and 10-Jan-2020

```json5
{
  "from": "1-Jan-2020",
  "to": "10-Jan-2020"
}
```

Get 100 mined blocks from 1-Jan-2020

```json5
{
  "from": "1-Jan-2020",
  "max": 100, // "max" will be ignored when having a "to"
}
```

Get last(latest) 100 blocks mined by pool

```json5
{
  "max": 100, // "max" will be ignored when having a "to"
}
```

the return looks like this

```json5
[
  {
    "difficulty": 539702861270356,
    "hash": "8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
    "height": 1187801,
    "reward": 4129400000000,
    "timestamp": 1582458302
  },
  {
    "difficulty": 539702861270356,
    "hash": "8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
    "height": 1187801,
    "reward": 4129400000000,
    "timestamp": 1582458302
  },
  {
    "difficulty": 539702861270356,
    "hash": "8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
    "height": 1187801,
    "reward": 4129400000000,
    "timestamp": 1582458302
  }
]
```

### Path "/blocks/last"

- Get

last Block Mined

```json
[
  {
    "difficulty": 539702861270356,
    "hash": "8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
    "height": 1187801,
    "reward": 4129400000000,
    "timestamp": 1582458302
  },
  ...
]
```

#### Path "/payments"

TODO

#### Path "/algorithm"

We are recommend to deploy different algorithm stratum port with different mining pool instance, so it means the frontend page have to deal with multi-api-server circumstance.

- GET

Get all algorithms

- POST

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

More lucky means more benefit when same hashrates

- GET

```json
{
  "1d": 0.99,
  "7d": 1.01,
  "1m": 1.11,
}
```

- POST

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
[
  "1.1",
  "1.11",
  "0.9",
  "0.98",
  "0.7",
  "1.5",
  "1.11",
  "0.9",
  "0.98",
  "1"
]
```

#### Path "/effort"

the effort table

effort = 1 / lucky

More lucky means more benefit when same hashrates

- GET

```json
{
  "1d": 1.01,
  "7d": 0.99,
  "1m": 0.91,
}
```

- POST

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
[
  "1.1",
  "1.11",
  "0.9",
  "0.98",
  "0.7",
  "1.5",
  "1.11",
  "0.9",
  "0.98",
  "1"
]
```
