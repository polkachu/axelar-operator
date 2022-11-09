# Ansible scripts for all Axelar networks

Design principles:

1. Support both mainnet and testnet
1. Support chains that are complex to install and upgrade; Do not support chains that are already easy based on official doc
1. The same playbook can be used for initial installation and version upgrade

## TL/DR

You run one playbook to set up a node or update a node version. Here is an example:

```bash
# Mainnet
ansible-playbook ethereum.yml -e "target=ethereum_mainnet"
# Testnet
ansible-playbook ethereum.yml -e "target=ethereum_mainnet"
```

## Supported Nodes

| Chain     | Supported? | Playbook       | Update version                                    | Note                                                                       |
| --------- | ---------- | -------------- | ------------------------------------------------- | -------------------------------------------------------------------------- |
| Avalanche | No         |                | Just restart the service                          | The official Axelar doc is simple enough                                   |
| Moonbeam  | Yes        | `moonbeam.yml` | Update version variable and run the same playbook |                                                                            |
| Ethereum  | Yes        | `ethereum.yml` | sudo apt update && sudo apt upgrade               | Geth + Prysm                                                               |
| Fantom    | Yes        | `fantom.yml`   | Update version variable and run the same playbook | For initial installation, use mode=full to download the large genesis file |
