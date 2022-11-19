# Ansible scripts for all Axelar networks

Design principles:

1. Support both mainnet and testnet
1. Support chains with direct binary install and leave out Docker installation (e.g. Arbitrum)
1. The same playbook can be used for version upgrade (default) and initial installation (with an extra flag)

## TL/DR

You run one playbook to set up a node or update a node version. Here is a few examples:

```bash
# Mainnet: upgrade version
ansible-playbook ethereum.yml -e "target=ethereum_mainnet"
# Testnet: upgrade version
ansible-playbook ethereum.yml -e "target=ethereum_testnet"
# Initial full installation
ansible-playbook ethereum.yml -e "target=ethereum_mainnet mode=full"
```

## Supported Modes

| Mode                 | Flags                  |
| -------------------- | ---------------------- |
| Initial Installation | `target=XYZ mode=full` |
| Version Upgrade      | `target=XYZ`           |

## Supported Nodes

| Chain     | Supported? | Playbook        | Upgrade                       | Note                                                                         |
| --------- | ---------- | --------------- | ----------------------------- | ---------------------------------------------------------------------------- |
| Arbitrum  | No         | NA              | Restart service               | Use Axelar Official doc                                                      |
| Aurora    | WIP        |                 |                               |                                                                              |
| Avalanche | Yes        | `avalanche.yml` | Update version & run playbook |                                                                              |
| Binance   | Yes        | `binance.yml`   | Update version & run playbook | Use [snapshot](https://github.com/BNB48Club/bsc-snapshots)                   |
| Celo      | Yes        | `celo.yml`      | Update version & run playbook |                                                                              |
| Ethereum  | Yes        | `ethereum.yml`  | apt update & upgrade          | Geth + Prysm                                                                 |
| Fantom    | Yes        | `fantom.yml`    | Update version & run playbook | Use [snapshot](https://docs.fantom.foundation/node/snapshot-download)        |
| kava      | Yes        | NA              | NA                            | See our [Cosmos Ansible Repo](https://github.com/polkachu/cosmos-validators) |
| Moonbeam  | Yes        | `moonbeam.yml`  | Update version & run playbook |                                                                              |
| Polygon   | WIP        |                 |                               |                                                                              |

## Note

The mainnet version of the deployment script is fully tested with our own deployed nodes.

The testnet version of the deployment script is never fully tested. The script has all the right testnet vars based on our understanding, but please verify before blindly using it. Feel free to send a PR if you find a bug. Thanks!
