# Ansible scripts for all Axelar networks

Design principles:

1. Support both mainnet and testnet
1. Only support chains with direct binary installation. For docker installation (Arbitrum and Aurora), users should just refer to the official doc
1. Can be used for version upgrade (default) and initial installation (with an extra "mode=full" flag)
1. Assume that Golang already exists on the server

## TL/DR

You run one playbook to set up a node or update version. Here is a few examples:

```bash
# Mainnet: upgrade version
ansible-playbook ethereum.yml -e "target=ethereum_mainnet"
# Testnet: upgrade version
ansible-playbook ethereum.yml -e "target=ethereum_testnet"
# Initial full installation
ansible-playbook ethereum.yml -e "target=ethereum_mainnet mode=full"
```

## Setup

Please first copy the sample inventory file to your own inventory file so you can customize the IPs etc:

```bash
cp inventory.sample inventory.ini
```

## Supported Modes

| Mode              | Flags                  |
| ----------------- | ---------------------- |
| Full Installation | `target=XYZ mode=full` |
| Version Upgrade   | `target=XYZ`           |

## Supported Nodes

| Chain     | Supported? | Playbook        | Upgrade                       | Note                                                                     |
| --------- | ---------- | --------------- | ----------------------------- | ------------------------------------------------------------------------ |
| Arbitrum  | No         | NA              | Restart docker                | Use Axelar Official doc                                                  |
| Aurora    | No         | NA              | Restart docker                | Use Axelar Official doc                                                  |
| Avalanche | Yes        | `avalanche.yml` | Update version & run playbook |                                                                          |
| Binance   | Yes        | `binance.yml`   | Update version & run playbook | Use [snapshot](https://github.com/BNB48Club/bsc-snapshots)               |
| Celo      | Yes        | `celo.yml`      | Update version & run playbook |                                                                          |
| Ethereum  | Yes        | `ethereum.yml`  | apt update & upgrade          | Geth + Prysm                                                             |
| Fantom    | Yes        | `fantom.yml`    | Update version & run playbook | Use [snapshot](https://docs.fantom.foundation/node/snapshot-download)    |
| kava      | Yes        | NA              | NA                            | See [Cosmos Ansible Repo](https://github.com/polkachu/cosmos-validators) |
| Moonbeam  | Yes        | `moonbeam.yml`  | Update version & run playbook |                                                                          |
| Polygon   | WIP        | `polygon.yml`   | Update version & run playbook | Use [snapshot](https://snapshot.polygon.technology/)                     |

## Note

The mainnet version of the deployment script is fully tested with our own node deployments.

The testnet version of the deployment script is never fully tested. The script has all the right testnet vars based on our understanding, but please verify before using it. Feel free to send a PR if you find a bug. Thanks!
