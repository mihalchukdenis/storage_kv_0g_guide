# storage_kv_0g_guide

![0G-bg-2](https://github.com/user-attachments/assets/2f299154-c046-4d33-9569-ef9787b8422a)

# How to install Storage KV
## Hardware Requirement
```bash
- Memory: 16 GB RAM
- CPU: 4 cores
- Disk: 500GB / 1T NVME SSD
- Bandwidth: 500 MBps for Download / Upload
```

## Download the source code
```bash
git clone -b v1.1.0-testnet https://github.com/0glabs/0g-storage-kv.git
```

## Build the source code
```bash
cd 0g-storage-kv
git submodule update --init
cargo build --release
```

## Copy the config_example.toml to config.toml
```bash
# rpc endpoint
rpc_listen_address
# ips of storage service, separated by ","
zgs_node_urls = "http://ip1:port1,http://ip2:port2,..."

# layer one blockchain rpc endpoint
blockchain_rpc_endpoint

# flow contract address
log_contract_address

# block number to start the sync, better to align with the config in storage service
log_sync_start_block_number

# storage nodes to download data from, separated by ","
# the provided nodes should cover full data in the storage network
zgs_node_urls
```

## Run the KV
```bash
cd run

# consider using tmux in order to run in background
../target/release/zgs_kv --config config.toml
```
