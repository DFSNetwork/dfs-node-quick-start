
# Run DFS Node, Secure the Network, Earn DFS.
Help Decentralize the network by runing a DFS node. 

By processing transactions and participating in consensus, each validator helps make DFS Network the most censorship resistant and highest-performance blockchain network in the world.

# How to Run a DFS node 

## Step 0: register as a block producer 

You can register more easily through the ui: https://dfs.land/nodeVote/register

* Remember to save the producer key pair generated during registration * 

## Step 1: Clone this repository

```
git clone git@github.com:DFSNetwork/dfs-node-quick-start.git
or
git clone https://github.com/DFSNetwork/dfs-node-quick-start.git

cd dfs-node-quick-start
```

## Step 2: Download and Install

system requirement: ubuntu18.04 or ubuntu22.04


if you are using ubuntu18.04:

```
wget https://github.com/DFSNetwork/dfs-core/releases/download/v10.0.0/dfs_10.0.0-ubuntu18.04_amd64.deb

apt update

dpkg -i dfs_10.0.0-ubuntu18.04_amd64.deb
```

if you are using ubuntu22.04:

```
wget https://github.com/DFSNetwork/dfs-core/releases/download/v10.0.0/dfs_10.0.0-ubuntu22.04_amd64.deb

apt update

dpkg -i dfs_10.0.0-ubuntu22.04_amd64.deb
```

check whether the installation is successful

```
nodeos --version
v10.0.0
```

## Step 3: Run rpc Node

```
cd rpc-node
```

run start cmd to start DFS Node

```
./start
```

view run logs and synchronization progress

```
./showlog
```

and stop cmd

```
./stop
```

Run the command to check whether it is successful

```
cleos -u http://127.0.0.1:8888 get info

{
  "server_version": "53eeb0ec",
  "chain_id": "000d9cae502dd1cc895745e204f83cc892bc4c450f92a03ecd4fe057709853cc",
  "head_block_num": 1443473,
  "last_irreversible_block_num": 1443148,
  "last_irreversible_block_id": "0016054c4c6e8a930b34d749cc123d79dbc4551546aa8a036a607a39a2421cef",
  "head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "head_block_time": "2024-01-09T10:35:00.000",
  "head_block_producer": "nyrn1oxdglzh",
  "virtual_block_cpu_limit": 202007,
  "virtual_block_net_limit": 1048576000,
  "block_cpu_limit": 200000,
  "block_net_limit": 1048576,
  "server_version_string": "v10.0.0",
  "fork_db_head_block_num": 1443473,
  "fork_db_head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "server_full_version_string": "v10.0.0-53eeb0ec36e4bc28714ae17761230d3956fe0df7",
  "total_cpu_weight": 0,
  "total_net_weight": 0,
  "earliest_available_block_num": 1,
  "last_irreversible_block_time": "2024-01-09T10:32:05.500"
}
```

## Step 4: Run Producer Node

Edit your Producer Node's config.ini

Remember to replace your own bp name and key pair.

```

## producer-name: Replace it with yours
producer-name = produceraaaa

## key-pair: Replace it with yours
signature-provider = PUB_K1_5KReCfGBEgmMsEjGZmfQRzKCHntrU4kuq7LF8ywr6YK7ZHm121=KEY:PVT_K1_2H5vUyCpGWE3DXyY87ZzeneniQqHtmjSg8YbcU8788QjzccHs2
```

** Do not expose block producer nodes to the external network ** 

Run the command to check whether it is successful

```
cleos -u http://127.0.0.1:8887 get info

{
  "server_version": "53eeb0ec",
  "chain_id": "000d9cae502dd1cc895745e204f83cc892bc4c450f92a03ecd4fe057709853cc",
  "head_block_num": 1443473,
  "last_irreversible_block_num": 1443148,
  "last_irreversible_block_id": "0016054c4c6e8a930b34d749cc123d79dbc4551546aa8a036a607a39a2421cef",
  "head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "head_block_time": "2024-01-09T10:35:00.000",
  "head_block_producer": "nyrn1oxdglzh",
  "virtual_block_cpu_limit": 202007,
  "virtual_block_net_limit": 1048576000,
  "block_cpu_limit": 200000,
  "block_net_limit": 1048576,
  "server_version_string": "v10.0.0",
  "fork_db_head_block_num": 1443473,
  "fork_db_head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "server_full_version_string": "v10.0.0-53eeb0ec36e4bc28714ae17761230d3956fe0df7",
  "total_cpu_weight": 0,
  "total_net_weight": 0,
  "earliest_available_block_num": 1,
  "last_irreversible_block_time": "2024-01-09T10:32:05.500"
}
```

# Use docker to run a dfs rpc node

A way to easily run DFS nodes on any platform.

## Step 1: Install docker on your platforms

Install according to the docker official documentation : https://docs.docker.com/get-docker/

## Step 2: use docker command to run DFS node

```
// go to the folder with the compose.yaml file
cd dfs-node-quick-start

// run a DFS node 
docker-compose up -d

// stop 
docker compose stop

// start
docker compose start

// log
docker compose logs
```

Run the command to check whether it is successful

```
./dfs-cli get info

{
  "server_version": "53eeb0ec",
  "chain_id": "000d9cae502dd1cc895745e204f83cc892bc4c450f92a03ecd4fe057709853cc",
  "head_block_num": 1443473,
  "last_irreversible_block_num": 1443148,
  "last_irreversible_block_id": "0016054c4c6e8a930b34d749cc123d79dbc4551546aa8a036a607a39a2421cef",
  "head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "head_block_time": "2024-01-09T10:35:00.000",
  "head_block_producer": "nyrn1oxdglzh",
  "virtual_block_cpu_limit": 202007,
  "virtual_block_net_limit": 1048576000,
  "block_cpu_limit": 200000,
  "block_net_limit": 1048576,
  "server_version_string": "v10.0.0",
  "fork_db_head_block_num": 1443473,
  "fork_db_head_block_id": "0016069121c651d58a308af890d9dcc7a609b5323e9a57ad0fb505f29bcf162c",
  "server_full_version_string": "v10.0.0-53eeb0ec36e4bc28714ae17761230d3956fe0df7",
  "total_cpu_weight": 0,
  "total_net_weight": 0,
  "earliest_available_block_num": 1,
  "last_irreversible_block_time": "2024-01-09T10:32:05.500"
}
```

// rpc node logs 
docker logs -fn 200  dfs-node-quick-start-rpcnode-1

// producer node logs
docker logs -fn 200  dfs-node-quick-start-producernode-1


# Tools

## producer: See which node is producing

```
./producer

-------------------------------
       Time        Producer
-------------------------------
 1.  11:33:05    2vy14dqixpvi
 2.  11:33:11    bitcoinzhang
 3.  11:33:17    bpdfsnetwork
 4.  11:33:23    californiabp
 5.  11:33:29    dfgdeveloper
 6.  11:33:35    dfs111223344
 7.  11:33:41    dfsbpdfsbp11
 8.  11:33:47    dfsbtcl2no1x
 9.  11:33:53    dfslover1111
 10. 11:33:59    dfsnetworkbp *
 11. 11:34:05    dfsneverfail
 12. 11:34:11    dfssingapore
 13. 11:34:17    ethereumbest
 14. 11:34:23    greatdfsfarm
 15. 11:34:29    hpe4jyjgyjd4
 16. 11:34:35    hungarytiger
 17. 11:34:41    iamaproducer
 18. 11:34:47    imaxiusfirst
 19. 11:34:53    poweredbydfs
 20. 11:32:41    thlknlna32fu
 21. 11:32:53    xiaoming5555
 22. 11:32:59    zydntcgyiozo
-------------------------------
```

## lsnode: List all nodes status
```
./lsnode

 nodes=73
 producers=22

-------------------------------------------------------
 No     Node            RPC     P2P     Reward  Votes
-------------------------------------------------------
 1      dfsbpdfsbp11    1       1       1       446307
 2      californiabp    1       1       1       199924
 3      dfsbtcl2no1x    1       1       1       94260
 4      iamaproducer    1       1       1       74039
 5      imaxiusfirst    1       1       1       73452
 6      dfsnetworkbp    1       1       1       57672
 7      thlknlna32fu    1       1       1       57613
 8      dfssingapore    1       1       1       45847
 9      dfsneverfail    1       1       1       43960
 10     dfgdeveloper    1       1       1       31668
 11     greatdfsfarm    1       1       1       29437
 12     bpdfsnetwork    1       1       1       25724
 13     poweredbydfs    1       1       1       24723
 14     hpe4jyjgyjd4    1       1       1       24082
 15     2vy14dqixpvi    1       1       1       22458
 16     dfs111223344    1       1       1       17941
 17     woyaofeidegg    0       0       0       17694
 18     bitcoinzhang    1       1       1       12315
 19     ethereumbest    1       1       1       10432
 20     zydntcgyiozo    0       0       0       8646
 21     dfslover1111    1       1       1       8081
 22     hungarytiger    1       1       1       7074
 23     xiaoming5555    1       1       1       5379
 24     pumpmydfs55k    1       1       1       4235
 25     4kfkhcqgsqwd    0       0       0       1849
 26     sunrisedfs11    1       1       1       1753
 27     physicslover    1       1       1       1323
 28     pinkdfsbp111    1       1       1       1090
 29     ptfgxmg12345    1       1       1       1030
 30     testusera114    0       0       0       966
-------------------------------------------------------
```


## Join discord and get support

https://discord.com/invite/JydrcH5u9V
