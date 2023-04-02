# eRPC (An efficient Relay Partition Checker)

A possible collection of tools for relay partition checking using **arti_client**

## OnionPerf Logs of current run 

```
Downloading OnionPerfData from https://collector.torproject.org/recent/onionperf/2023-03-31.op-de7a.onionperf.analysis.json.xz
Download time : 3.151173624s | Size(in Bytes) : 1174348
Decompressing op-de7a.json.xz
117434800
Decompression time : 70.198472ms | Size(in Bytes) : 29840718
Created op-de7a.json

Downloading OnionPerfData from https://collector.torproject.org/recent/onionperf/2023-03-31.op-hk6a.onionperf.analysis.json.xz
Download time : 2.301160649s | Size(in Bytes) : 1020812
Decompressing op-hk6a.json.xz
102081200
Decompression time : 67.332457ms | Size(in Bytes) : 23282938
Created op-hk6a.json

Downloading OnionPerfData from https://collector.torproject.org/recent/onionperf/2023-03-31.op-hk7a.onionperf.analysis.json.xz
Download time : 1.920114551s | Size(in Bytes) : 1009796
Decompressing op-hk7a.json.xz
100979600
Decompression time : 64.921751ms | Size(in Bytes) : 23615588
Created op-hk7a.json

Downloading OnionPerfData from https://collector.torproject.org/recent/onionperf/2023-03-31.op-nl7a.onionperf.analysis.json.xz
Download time : 2.167353334s | Size(in Bytes) : 1165524
Decompressing op-nl7a.json.xz
116552400
Decompression time : 69.504284ms | Size(in Bytes) : 28199754
Created op-nl7a.json

Downloading OnionPerfData from https://collector.torproject.org/recent/onionperf/2023-03-31.op-us7a.onionperf.analysis.json.xz
Download time : 2.255002283s | Size(in Bytes) : 1658736
Decompressing op-us7a.json.xz
165873600
Decompression time : 94.64186ms | Size(in Bytes) : 51306885
Created op-us7a.json

total failed : 12280
total successful :27484
The total 2 hop circuit in successful circuits are : 0
The total 3 hop circuit in successful circuits are : 18441
The total 4 hop circuit in successful circuits are : 8892
The total 5 hop circuit in successful circuits are : 0
The total 2 hop circuit in failed circuits are : 2606
The total 3 hop circuit in failed circuits are : 8433
The total 4 hop circuit in failed circuits are : 2
The total 5 hop circuit in failed circuits are : 0
---------------------------------------------------
The total 2 relay combinatiosn that were in successful circuit were 63719
---------------------------------------------------
The total 2 relay combinatiosn that were in failed circuit were 19478
```

## Logs for checking relay partition with two hop circuits combination among 400 random relays 
I ran the partition checking tool for ~ 6 hrs 50 min to check partition among **400** random relays. Here's the result obtained

Here's a snippet of one of the line of data produced during that run in [Data.csv](https://github.com/rishadbaniya/rpc/blob/main/data.csv)
```
11ac67307b362b77569af314a9a7a06b9195df19,9e627928dfe5dd5e518a452a503d40880115dfa1,2023-04-01 19:49:40.424670303 UTC,No error
```

Here the field of the CSV represents the **source_relay**,**source_relay**,**utc_time**,**error_produced_during_run**

I saw many errors to be **Circuit took too long to build**, which i'm still trying to figure out and might need to go deep into how arti_client does that timeout, whether it sums up the time taken 
to connect to the guard relay or not, or it just calculates the circuit build time based on time taken to get the CIRC EXTENDED sort of events, i've still room to figure out the ways to look at the CIRC EVENT logs in arti_client, in few weeks i hope to finish this tool 
