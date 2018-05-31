# BXB-Miner
![](https://github.com/BixBite-project/bxb-miner/blob/master/img.png?raw=true)

Miner is early alpha version.

Support only AMD GPU Graphics with fan control. For test only.

Supported algo/coins: Cryptonight, Cryptonight v7, Cryptonight-Heavy (Bixbite, Sumocoin, Haven), IPBC, Alloy, Cryptonight Lite, Cryptonight Lite v7

Without Dev fee !
Not a fork of any miner software!

# Config example:
    {
      "pools": [ 				// list pools
      {
    	"name":"Bixbite",		// configuration name
    	"url": "pool.bixbite.pro",	// pool url address
    	"port": 3333,			// pool port 
        "stale-time":0,			// stale share time interval allowing window (ms)
    	"user": "<WALLET>",		// wallet address
    	"pass": "", 			// password
    	"algo":"heavy"			// supported algorithm: old, v7, heavy, ipbc, alloy, lite, lite_v7, auto (for old/v7)
      }
      ],
      "intensity": "896", 			// GPU intensity (one value for all GPUs, separated list for individual intensity per adapter ("896,432,896")
      "gpu":"0",				// GPU ID using to mine, for multiple set as "0,1,2,3,4"
      "gpu-threads": "2",			// threads per GPU, may be set ("2,1,1,2,2")
      "auto-fan":true,			// fan auto-control
      "target-temp":60,			// target temperature
      "server":true, 			// this option enabling server monitoring feature, other rigs may acts as clients
      "server-ip":"0.0.0.0",  		// server IP address for server monitoring
      "rig-name":"PROG"      		// rig name on monitoring server
    }

Use the "-c" switch to run different configurations (ex: bxb-miner.exe -c config_heavy.json)

# Recommended:

- Use large pagefile, more 32gb
- Set system variable GPU_FORCE_64BIT_PTR in 1

# Tested cards:
					
| Video card | Chip | Characteristics | Threads | Algo | Intensity | Hashrate |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Gigabyte AMD Radeon RX 580 8Gb | 580 | 1310/1900 Hynix |2| cryptonight heavy | 856 | 965 |
| MSI AMD Radeon RX 580 ARMOR OC 4Gb | 580 | 1250/2000 Elpida |2| cryptonight heavy | 477 | 740 |
| Sapphire AMD Radeon RX 580 Nitro+ 4Gb | 580 | 1250/2000 Elpida | 2|cryptonight heavy | 477 | 770 |
| Gigabyte AMD Radeon RX 550 D5 [GV-RX550D5-2GD] 2Gb | 550 | 1195/2000 Elpida |2| cryptonight heavy | 216 | 340 |
| MSI AMD Radeon RX 550 AERO 2Gb | 550 | 1250/1950 Hynix |2| cryptonight heavy | 216 | 332 |
| MSI AMD Radeon RX 550 LP 2Gb | 550 | 1250/1950 Hynix |2| cryptonight heavy | 216 | 332 |
| Sapphire AMD Radeon RX 550 PULSE 2Gb | 550 | 1250/1800 Elpida |2| cryptonight heavy | 216 | 325 |
| MSI AMD Radeon RX 480 Reference 8Gb | 480 | 1300/2060 Samsung |2| cryptonight heavy | 672 | 1050 |
| PowerColor RedDevil AMD Radeon RX 470 4Gb | 470 | 1300/2020 Hynix |2| cryptonight heavy | 456 | 780 |
| Sapphire AMD Radeon RX 460 Nitro 4Gb | 460 | 1250/2000 Micron |2| cryptonight heavy | 312 | 550 |
| Sapphire AMD Radeon RX 390 Nitro 8Gb | 390 | 1070/1500 Samsung |2| cryptonight heavy | 896 | 650 |

