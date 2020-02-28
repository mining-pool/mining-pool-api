# Pool

## Path "/pool"

GET

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

## Path "/pool/network"

GET

```json

{
    "height": 1187802,
    "hashrate": 3366733275,
    "difficulty": 538996687554816,
}
```

### Path "/pool/blocks"

- GET/POST

on default, return 25 items as maximum

Can also POST with limitation

Get all blocks mined between 1-Jan-2020 and 10-Jan-2020

```json
{
  "from": "1-Jan-2020",
  "to": "10-Jan-2020"
}
```

Get 100 mined blocks from 1-Jan-2020

```json
{
  "from": "1-Jan-2020",
  "max": 100, // "max" will be ignored when having a "to"
}
```

Get last(latest) 100 blocks mined by pool

```json
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

### Path "/pool/blocks/last"

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
