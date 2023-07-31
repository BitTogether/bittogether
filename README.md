# Virtual Private Mempool Server by Bittogether (Forked from Sparrow Wallet)

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Configuration & Usage](#configuration--usage)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction

The Virtual Private Mempool Server is a custom implementation of Bitcoin tx routing and timing forked from Sparrow Wallet's Electrum Server by BitTogether, designed to provide a private and secure mempool service for Bitcoin transactions and Bitcoin Ordinals. This software serves as a backend component, optimizing the transaction relay process and providing a dedicated mempool for a single client or a group of trusted clients like an Ordinals project or collection.

> **Note:** If you are looking for the Sparrow Wallet repository, visit the original repository [here](https://github.com/sparrowwallet/sparrow).

## Features

- **Lower Fees**: Prevents Bitcoin users from bidding each other up for blockspace, resulting in lower transaction fees.
- **Privacy**: Provides a virtual private mempool for enhanced transaction privacy.
- **Security**: Ensures a controlled environment for tx propagation, mitigates risk of MEV frontrunning and other attacks.
- **Customizable**: Easy-to-configure settings for tailored use-cases. Customize your private mempool with your own rules.  
- **Compatibility**: Designed to be used with Sparrow Wallet and other PSBT compatible clients. 
- **Real-time Updates**: Keeps your private mempool synchronized with the Bitcoin network.
- **Unstuck Transactions**: Prevents transactions from getting stuck in the public memPool because of a low fee rate tx.

## Installation

**Prerequisites:**

- [Bitcoin Core](https://github.com/bitcoin/bitcoin) (v0.21.1 or higher) - Ensure you have Bitcoin Core installed and fully synced.

**Whitelist**

Obtain whitelist from https://www.x.com/btctogether for Early Access!! 

## Configuration & Usage

To utilize the Virtual Private Mempool Server, point your inscription service or Bitcoin tx relay to your server's URL or the Bittogether Private memPool URL. The client will then interact with the server for transaction broadcasting, waiting until the anticipated fee rate is below the fee rate set on the transaction.  For PSBTs, fees will be adjusted down to minimum effective fee rate anticipated, based on the fee rates of visible transactions and meta-transactions waiting in the public and private memPools.

## API Documentation

Refer to whitelist inscription instructions, Guide Coming Soon!

## Contributing

Contributions to the Virtual Private Mempool Server are welcome and encouraged! If you have any bug fixes, improvements, or new features to add, please follow the [contribution guidelines](CONTRIBUTING.md) in this repository.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

Special thanks to the developers of Sparrow Wallet for their excellent work, which served as the foundation for this fork. 

------------------------------------------------------------------------

------------------------------------------------------------------------

Original Sparrow Wallet README.md forked July 30, 2023 below:

# Sparrow Bitcoin Wallet

Sparrow is a modern desktop Bitcoin wallet application supporting most hardware wallets and built on common standards such as PSBT, with an emphasis on transparency and usability.

More information (and release binaries) can be found at https://sparrowwallet.com. Release binaries are also available directly from [GitHub](https://github.com/sparrowwallet/sparrow/releases).

![Sparrow Wallet](https://sparrowwallet.com/assets/images/control-your-sends.png)

## Building

To clone this project, use

`git clone --recursive git@github.com:sparrowwallet/sparrow.git`

or for those without SSH credentials:

`git clone --recursive https://github.com/sparrowwallet/sparrow.git`

In order to build, Sparrow requires Java 18 or higher to be installed. 
The release binaries are built with [Eclipse Temurin 18.0.1+10](https://github.com/adoptium/temurin18-binaries/releases/tag/jdk-18.0.1%2B10).

Other packages may also be necessary to build depending on the platform. On Debian/Ubuntu systems:

`sudo apt install -y rpm fakeroot binutils`


The Sparrow binaries can be built from source using

`./gradlew jpackage`

Note that to build the Windows installer, you will need to install [WiX](https://github.com/wixtoolset/wix3/releases).

When updating to the latest HEAD

`git pull --recurse-submodules`

The release binaries are reproducible from v1.5.0 onwards (pre codesigning and installer packaging). More detailed [instructions on reproducing the binaries](docs/reproducible.md) are provided.

> Video documentation of your build process uploaded to [bitcoinbinary.org](https://bitcoinbinary.org/) is appreciated. Alternatively check the site if you wish to see if someone else already verified the provided binaries. 

## Running

If you prefer to run Sparrow directly from source, it can be launched from within the project directory with

`./sparrow`

Java 18 or higher must be installed. 

## Configuration

Sparrow has a number of command line options, for example to change its home folder or use testnet:

```
./sparrow -h

Usage: sparrow [options]
  Options:
    --dir, -d
      Path to Sparrow home folder
    --help, -h
      Show usage
    --level, -l
      Set log level
      Possible Values: [ERROR, WARN, INFO, DEBUG, TRACE]      
    --network, -n
      Network to use
      Possible Values: [mainnet, testnet, regtest, signet]
```

As a fallback, the network (mainnet, testnet, regtest or signet) can also be set using an environment variable `SPARROW_NETWORK`. For example:

`export SPARROW_NETWORK=testnet`

A final fallback which can be useful when running the Sparrow binary is to create a file called ``network-testnet`` in the Sparrow home folder (see below) to configure the testnet network.

Note that if you are connecting to an Electrum server when using testnet, that server will need to be running on testnet configuration as well.

When not explicitly configured using the command line argument above, Sparrow stores its mainnet config file, log file and wallets in a home folder location appropriate to the operating system:

| Platform | Location |
|----------| -------- |
| OSX      | ~/.sparrow |
| Linux    | ~/.sparrow |
| Windows  | %APPDATA%/Sparrow |

Testnet, regtest and signet configurations (along with their wallets) are stored in subfolders to allow easy switching between networks.

## Reporting Issues

Please use the [Issues](https://github.com/sparrowwallet/sparrow/issues) tab above to report an issue. If possible, look in the sparrow.log file in the configuration directory for information helpful in debugging. 

## License

Sparrow is licensed under the Apache 2 software licence.

## GPG Key

The Sparrow release binaries here and on [sparrowwallet.com](https://sparrowwallet.com/download/) are signed using [craigraw's GPG key](https://keybase.io/craigraw):  
Fingerprint: D4D0D3202FC06849A257B38DE94618334C674B40  
64-bit: E946 1833 4C67 4B40

## Credit

![Yourkit](https://www.yourkit.com/images/yklogo.png)

Sparrow Wallet uses the [Yourkit Java Profiler](https://www.yourkit.com/java/profiler/) to profile and improve performance. 
YourKit supports open source projects with useful tools for monitoring and profiling Java and .NET applications.
