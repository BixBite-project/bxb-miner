# BXB-Miner
![](https://github.com/BixBite-project/bxb-miner/blob/master/img.png?raw=true)

Miner is early BETA version.

# Attention!!! Configuration file format was changed, read below!

Support AMD GPU Graphics with monitoring and auto-fan control.
Support NVIDIA GPU Graphics with temperature/fan monitoring.
Support CPU mining.

Supported algo/coins (AMD/CPU): Cryptonight, Cryptonight v7, Cryptonight v8 (Monero, Wownero), Cryptonight-Fast (Masari), Cryptonight-Heavy (Bixbite, Loki, Saronite), New Stellite, New Haven, IPBC, Alloy, Cryptonight Lite, Cryptonight Lite v7

Supported algo/coins (NVIDIA): Cryptonight-Heavy (Bixbite, Loki, Saronite), Haven

Without Dev fee !


# Configuration example (config.json):
	{
		"pools":[				// POOLS section
		{	
			"name": "Bixbite",		// pool configuration name
			"url": "pool.bixbite.pro",	// pool address
			"port": 3333,			// pool port
			"stale-time": 0,		// stale share time interval allowing window in milliseconds (0 means don't submit stale shares)
			"user": "<WALLET>",		// your wallet address
			"pass": "<PASSWORD",		// your password
			"algo": "heavy"			// mining algorithm: old, v7, v8, stellite, heavy, haven, ipbc(new BitTube variant), alloy, lite, lite_v7, masari, auto (for old/v7)
		}
		],
		"ocl":{					// AMD (OpenCL) section
			"gpu": "0",			// GPU ID using to mine, for multiple set as "0,1,2,3,4"
			"intensity": "896",		// GPU intensity (one value for all GPUs, separated list for individual intensity per adapter ("896,432,896")
			"threads": "2",			// threads per GPU, can be set for multiple GPUs ("2,1,1,2,2")
			"worksize": "8",		// Worksize per GPU, can be set for multiple GPUs ("8,8,8,7,8")
			"auto-fan": true,		// fan auto-control
			"target-temp": 60		// target temperature
		},
		"cuda":{				// NVIDIA (CUDA) section
			"gpu": "0",			// GPU ID using to mine, for multiple set as "0,1,2,3,4"
			"blocks": "36",			// blocks per GPU, may be set ("24,36,36,24,36")
			"threads": "16",		// threads per GPU, may be set ("8,8,16,32,8")
			"temp-monitor": true		// temperature monitoring
		},
		"cpu":{					// CPU section
			"use-cpu": true,		// Enable CPU mining
			"cpu-threads": 2		// Manual settings for cpu threads (not recommend). Exclude this option to auto-select thread count.
		},
		"server": true,				// this option enabling server monitoring feature, other rigs may acts as clients
		"server-ip": "0.0.0.0",			// server IP address to connect (when acts as client)
		"rig-name": "PROG",			// rig name on monitoring server
		"log": true				// show log at start and write into file
	}

Use the "-c" switch to run different configurations (ex: bxb-miner.exe -c config_heavy.json)

# BXB-Miner client-server usage:

![](https://github.com/BixBite-project/bxb-miner/blob/master/scheme.jpg?raw=true)


If your have many rig's, you can use this function for simplify monitoring and management

Next commands avalible for use:
- Change current pool in all rigs;
- Pause/Start all rig's;
- Reset statistics on  all rig's which connected to server;
- Reload pool list from file, without restart miner;
- Update pool list on rig's (from server). Use macros $$$name$$$ in config for automaticaly replace to rig-name on recieved rig's;

# Miner hashrate performance recommendations:

- Use large pagefile, 32Gb or more
- Allow lock pages in memory
- Set system variable:
  - GPU_FORCE_64BIT_PTR 1
  - GPU_MAX_ALLOC_PERCENT 100
  - GPU_MAX_HEAP_SIZE 100
  - GPU_MAX_SINGLE_ALLOC_PERCENT 100
  - GPU_MAX_USE_SYNC_OBJECTS 1

# Tested CPU's:

Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz // 3 threads // cryptonight v7 // 195 H/s
Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz // 4 threads // cryptonight light v7 // 595 H/s
Intel(R) Xeon(R) CPU E5-2630 v4 @ 2.20GHz // 12 threads // cryptonight v7 // 495 H/s
Intel(R) Xeon(R) CPU E3-1245 @ 3.30GHz // 4 threads // cryptonight v7 // 260 H/s

# Tested AMD cards:

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

# Tested NVIDIA cards:

| Video card | Chip | Characteristics | Blocks | Threads | Algo | Hashrate |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| MSI GeForce GTX 1060 OC 3Gb | GP106 | 1950/4550 Hynix | 36 | 16 | cryptonight heavy | 495 |
| PNY GeForce GTX 1060 XLR8 Gaming OC 3Gb | GP106 | 2050/4550 Samsung | 36 | 16 | cryptonight heavy | 537 |
| ZOTAC GeForce GTX 680 680 AMP! Edition 2Gb | GK104 | 1240/3500 Hynix | 16 | 16 | cryptonight heavy | 180 |

# TODO

- Future BixBite v2 algo support;
- Failover mode for pools;
- Full algo support for CUDA devices;
- Improvements in client-server mode;
- The mechanism for determining GPU overclocking too much;
- Easy realtime autoswitch to any algo.
