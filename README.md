# Hello World

mkdir prysm && cd prysm

# Download installation script

curl https://raw.githubusercontent.com/prysmaticlabs/prysm/master/prysm.sh --output prysm.sh && chmod +x prysm.sh

# Download the Goerli network genesis file

wget https://github.com/eth-clients/eth2-networks/raw/master/shared/prater/genesis.ssz

# Generate a 32 byte hex secret key for authentication, for e.g.

./prysm.sh beacon-chain generate-auth-secret

# Alternatively, `openssl rand -hex 32 | tr -d "\n" > "jwt.hex"`

# Start Prysm beacon chain.

# NOTE: For Goerli testnet, add `--prater` flag

./prysm.sh beacon-chain --http-web3provider=http://localhost:8551 --jwt-secret=/path/to/jwt.hex --genesis-state=./genesis.ssz
