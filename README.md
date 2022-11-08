# Ansible scripts for all Axelar networks

Design principles:

1. Support both mainnet and testnet
1. Support chains that are complex to install and upgrade; Do not support chains that are already easy based on official doc
1. The same playbook can be used for initial installation and version upgrade

## Supported Nodes

| Chain     | Supported? | Playbook       | Note                                     |
| --------- | ---------- | -------------- | ---------------------------------------- |
| Avalanche | No         |                | The official Axelar doc is simple enough |
| Moonbeam  | Yes        | `moonbeam.yml` |                                          |
| Ethereum  | Yes        | `ethereum.yml` |                                          |
