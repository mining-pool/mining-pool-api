# Objects

## Algorithm

```javascript
{
    "name": "scrypt",
    "variant": "ltc-origin", // an additional remark for algorithm name
    "blobType": "bitcoin" // maybe cryptonote v1/v2, forknote v1/v2, ethereum or any other coin's own blobType, just used as an additional remark for variant. Pool software can keep null or "".
}
```

## Port

port is an object contains the configs for guiding users to quick start mining on your pool

```javascript
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

## Block

```javascript
{
    "difficulty": 539702861270356, // float64
    "hash":"8d04b7f92faba60fdc071304c1d1260daed0dd6a30def76dc3e322589b867762",
    "height": 1187801,
    "reward": 4129400000000,
    "timestamp": 1582458302
}
```
