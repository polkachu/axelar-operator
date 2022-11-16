# Ansible scripts for all Axelar networks

Design principles:

1. Support both mainnet and testnet
1. Support chains that are complex to install and upgrade; Do not support chains that are already easy based on official doc
1. The same playbook can be used for initial installation and version upgrade

## TL/DR

You run one playbook to set up a node or update a node version. Here is a few examples:

```bash
# Mainnet
ansible-playbook ethereum.yml -e "target=ethereum_mainnet"
# Testnet
ansible-playbook ethereum.yml -e "target=ethereum_testnet"
# Full install
ansible-playbook ethereum.yml -e "target=ethereum_mainnet mode=full"
```

## Supported Modes

| Mode         | Extra                  |
| ------------ | ---------------------- |
| Full Install | `target=XYZ mode=full` |
| Upgrade      | `target=XYZ`           |

## Supported Nodes

| Chain     | Supported? | Playbook       | Upgrade                       | Note                    |
| --------- | ---------- | -------------- | ----------------------------- | ----------------------- |
| Arbitrum  | No         | NA             | Restart docker                | Use Axelar Official doc |
| Avalanche | No         | NA             | Restart service               | Use Axelar Official doc |
| Moonbeam  | Yes        | `moonbeam.yml` | Update version & run playbook |                         |
| Ethereum  | Yes        | `ethereum.yml` | apt update & upgrade          | Geth + Prysm            |
| Fantom    | Yes        | `fantom.yml`   | Update version & run playbook |                         |
