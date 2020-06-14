# Miner

## GET "/miner/{miner}"

get the details of miner

## POST "/miner/{miner}"

submit the additional miner options to pool, like payment method

```json

{
    "totalAverageHashrate": 18000, // unit h/s
    "totalLiveHashrate": 18000,
    "lastShareTimestamp": 1582801903,
    "rigs": ["rig1", "rig2", "rigN"]
}

```

## GET "/miner/{miner}/{rig}"

get the stats of rig
