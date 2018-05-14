# bxb-miner
![](https://github.com/BixBite-project/bxb-miner/blob/master/img.png?raw=true)

Miner is early alpha version. Support only AMD GPU Graphics with fan control. For test only.
Supported algo/coins: Cryptonight, Cryptonight v7, Cryptonight-Heavy (Bixbite, Sumocoin, Haven), IPBC, Alloy, Cryptonight Lite, Cryptonight Lite v7

Without Dev fee !
Not a fork of any miner software!

Config example:
{
  "pools": [ // list pools
  {
     "name":"Bixbite",   // configuration name
     "url": "pool.bixbite.pro", // pool url address
    "port": 3333,       // pool port 
    "stale-time":0,     //stale share time interval allowing window (ms)
      "user": "<WALLET>",     // wallet address
      "pass": "",       // password
    "algo":"heavy" // supported algorithm: old, v7, heavy, ipbc, alloy, lite, lite_v7, auto (for old/v7)
  }
  ],
  "intensity": "896",     //GPU intensity (one value for all GPUs, separated list for individual intensity per adapter ("896,432,896")
  "gpu":"0",        // GPU ID using to mine, for multiple set as "0,1,2,3,4"
  "gpu-threads": "2",    // threads per GPU, may be set ("2,1,1,2,2")
  "auto-fan":true,        // fan auto-control
  "target-temp":60,       // target temperature
  "server":true,      // this option enabling server monitoring feature, other rigs may acts as clients
  "server-ip":"0.0.0.0",  // server IP address for server monitoring
  "rig-name":"PROG"      // rig name on monitoring server
}
Use the "-c" switch to run different configurations (ex: bxb-miner.exe -c config_heavy.json)

