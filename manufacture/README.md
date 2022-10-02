# How to run the manufacture demo

**Generate crypto materials using the orion-server scripts:**

`cd ./manufacture`

`~/go/src/github.com/hyperledger-labs/orion-server/scripts/cryptoGen.sh . operator1 operator2 operator3 controller auditor`

**Run the orion-server in docker:**

Get the server image from:

https://hub.docker.com/r/orionbcdb/orion-server

`docker run -it --rm -v $(pwd)/crypto/:/etc/orion-server/crypto \
-v $(pwd)/ledger:/etc/orion-server/ledger \
-v $(pwd)/../../../orion-server/deployment/config-docker:/etc/orion-server/config \
-p 6001:6001 -p 7050:7050 orionbcdb/orion-server`

**In another window - create db and users**

`cd examples/manufacture`

`cd create_users`

`go build`

`./create_users operator1 operator2 operator3 controller auditor ../crypto`

**Create machines configuration**

`cd ../create_machines_config/`

`go build`

`./create_machines_config`

**Update machine config by operator1 with approval from controller**

`cd ../change_machine_config`

`go build`

`./change_machine_config`

**Show stored final tx and receipt in IDE**

finalTx.json

receipt.json

**Change machine ownership**

`cd ../change_machine_operator`

`go build`

`./change_machine_operator`

**Get proof for config change and verify**

`cd ../verify_machine_config_change/`

`go build`

`./verify_machine_config_change`

