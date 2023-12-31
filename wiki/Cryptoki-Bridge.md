[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/KristianMika/cryptoki-bridge)

Cryptoki Bridge is an implementation of the [PKCS#11](https://docs.oasis-open.org/pkcs11/pkcs11-base/v3.0/csprd01/pkcs11-base-v3.0-csprd01.html) standard. It's a shared library that can be loaded into any application that supports PKCS#11. The cryptographic operations are then delegated to [MeeSign](https://meesign.crocs.fi.muni.cz/) threshold platform.

## Installation

### Windows

You can download the **dll** library from the [releases page](https://github.com/KristianMika/cryptoki-bridge/releases).

### Debian-Based Distributions

1. [Setup the MPC Bridge repository](Debian-Repository.md)
2. Install the cryptoki-bridge package

```bash
sudo apt-get install cryptoki-bridge
```

### Other Linux

You can download the **so** library from the [releases page](https://github.com/KristianMika/cryptoki-bridge/releases) and store it to `/usr/lib`.

## Configuration

1. [Bridge Controller](Bridge-Controller.md)
2. ENV Variables
   - _COMMUNICATOR_HOSTNAME_ - sets the meesign hostname, e.g., `meesign.crocs.fi.muni.cz` (required)
   - _COMMUNICATOR_CERTIFICATE_PATH_ - provides the library with the path to the CA certificate (required)
   - _GROUP_ID_ - sets the signing group (optional). If not set, all groups present on the communicator are available.

## Usage

Cryptoki Bridge is a shared library that can be loaded into any application that supports PKCS#11. On Debian-based distributions, the library is installed in `/usr/lib/libcryptoki_bridge.so`.

### Applications

- [OpenSSH Authentication](Applications.md#openssh-authentication)

## Development

Folder _.devcontainer_ contains a configuration for an environment with all the build dependencies. To learn how to use it, please refer to the provided tutorial locaten in the [Development](Development.md) page.

### Build Requirements

_(Already installed in the devcontainer)_

- [rust](https://www.rust-lang.org/tools/install)
- [protocol buffer compiler](https://grpc.io/docs/protoc-installation/)

### Build

- Update submodules

  ```bash
  git submodule update --init --recursive
  ```

- Build the library

  ```bash
  cargo build --release
  ```
