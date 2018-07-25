# TELOS - A Smart Contract Platform for Everyone

Welcome to the official Telos repository! This software enables anyone to rapidly build and deploy high-performance and high-security blockchain-based applications.

Telos offers a suite of features including:

1. Economic disparity solutions such as elimination of whale accounts, inversely weighted voting, and increased token equity.
2. Developer and Enterprise features such as designation of propietary code and reduced RAM speculation.
3. Network freeze mitigation by regularly rotating standby BP's into production status to ensure operability and uptime.
4. Standby and BP payments are straightforward and fair, resulting in a better payment experience.
5. The Telos Constitution is ratified and enforceable at launch.
6. ...more features incoming!

For a full explanation of all the proposed Telos features, be sure to read our whitepaper!

## Node Setup with Grow

The Telos Foundation has created a lightweight, powerful tool that helps with automating many of the repetitive steps involved in setting up and configuring Telos nodes.

1. Follow the installation instructions [here](https://github.com/Telos-Foundation/grow) to set up Grow.

2. Navigate to your desired working directory and run `grow init pull`.

3. The `grow spin single` command will spin up a single node, but requires 4 positional arguments: producer name, p2p address, genesis.json path, and node address.

    a. Example: `grow spin single prodname1234 64.169.144.58 path/to/genesis.json stage1_1.telosfoundation.io`

    b. There are also 2 optional flags: `--p2p-port` and `--http-port`. These flags have default values of `8888` and `9876`, respectively.

4. Run `grow spin output prodname1234` to view the feed from the node.

5. By default, Grow creates nodes in folders inside the current working directory. For example, the node created above would be in a folder named `tn-prodname1234`. Inside the node folder is the `config.ini` and `genesis.json` used to start the node. If you need reference to the config options used for registering your node, see the `config.ini` in this folder.

6. Register Node on Testnet. 

    a. Navigate to testnet.telosfoundation.io and click on the Register button.

    b. Enter your configuration into the web form.

    c. Copy the command generated by submitting the form.

    d. Run the generated `regproducer` command on your local node.

    e. Your account is now created and registered as a producer on the testnet.

## Manual Node Setup

1. Clone master branch

    a. `git clone https://github.com/Telos-Foundation/telos`

    b. `git checkout Stage1.1`

    c. `git submodule update --init --recursive`

2. Inside the telos folder run the following commands:

    a. `./telos_build.sh`

    b. `cd build && sudo make install`

3. Set up config.ini file

    a. Run nodeos to generate a config file.

        i. Run `nodeos --config-dir ./` This will generate a config.ini file in the current directory if none exists.

    b. Determine your Producer name. Please be aware there are restrictions on the allowed characters.

        i. `producer-name = prodname1234`

    b. Determine your Signature Provider. Run `teclos create key`, and import your keys into your wallet.

        i. `signature-provider = TLOS{public key}=KEY:{private key}`

    c. Determine your p2p and http endpoints. Choose your own p2p and http ports.

        i. `http-server-address = 0.0.0.0:{http port}`

        ii. `p2p-listen-endpoint = 0.0.0.0:{p2p port}`

        iii. `p2p-server-address = {external IP address}:{p2p port}`

        iv. `p2p-peer-address = stage1_1.telosfoundation.io`

    d. Determine your Plugins. The only required plugin is producer_plugin, but other plugins add extended functionality to your nodes.

        ```plugin = eosio::http_plugin
        plugin = eosio::chain_plugin
        plugin = eosio::chain_api_plugin
        plugin = eosio::history_plugin
        plugin = eosio::history_api_plugin
        plugin = eosio::net_plugin
        plugin = eosio::net_api_plugin
        plugin = eosio::producer_plugin```

4. Register Node on Testnet

    a. Navigate to testnet.telosfoundation.io and click on the Register button.

    b. Enter your configuration into the web form.

    c. Copy the command generated by submitting the form.

    d. Run the generated `regproducer` command on your local node.

    e. Your account is now created and registered as a producer on the testnet.

## Testnet Contributions

The Telos Testnet is a sandbox for testing newly implemented features and finding bugs within the network. In order to ensure the network behaves as expected, participation in Testnet activites and providing meaningful feedback is encouraged. 

* _Voting_ Voting is an important part of the network, and with Telos' proposed changes to the voting stucture each vote will carry more weight and whales will have significantly less influence on the direction of the network. 

* _Claiming Producer/Standby Rewards_ In order to receive your hard-earned Producer/Standby payout, registered producers will make a call to `claimrewards` no more than once per day. When `claimrewards` is called, the calling producer's share of TLOS is calculated and paid to their account. In addition to sending the producer's earned payout, `claimrewards` will also make a deposit to the Worker Proposal Fund. This deposit is not taken out of the producer's share, but rather from the newly minted tokens from the claimrewards call. For a more in depth explanation of this process, please consult the whitepaper or join a discussion on our many public channels.

## Supported Operating Systems
Telos currently supports the following operating systems:  
1. Amazon 2017.09 and higher
2. Centos 7
3. Fedora 25 and higher (Fedora 27 recommended)
4. Mint 18
5. Ubuntu 16.04 (Ubuntu 16.10 recommended)
6. Ubuntu 18.04
7. MacOS Darwin 10.12 and higher (MacOS 10.13.x recommended)

# Resources
1. [Telos Website](https://telosfoundation.io)
2. [Telos Blog](https://medium.com/@teloslogical)
3. [Telos Twitter](https://twitter.com/HelloTelos)
4. [Telos Documentation Wiki](https://github.com/Telos-Foundation/telos/wiki)
5. [Telos Community Telegram Group](https://t.me/TheTelosFoundation)

Telos is released under the open source MIT license and is offered “AS IS” without warranty of any kind, express or implied. Any security provided by the Telos software depends in part on how it is used, configured, and deployed. Telos is built upon many third-party libraries such as Binaryen (Apache License) and WAVM (BSD 3-clause) which are also provided “AS IS” without warranty of any kind. Without limiting the generality of the foregoing, Telos Foundation makes no representation or guarantee that Telos or any third-party libraries will perform as intended or will be free of errors, bugs or faulty code. Both may fail in large or small ways that could completely or partially limit functionality or compromise computer systems. If you use or implement Telos, you do so at your own risk. In no event will Telos Foundation be liable to any party for any damages whatsoever, even if it had been advised of the possibility of damage.