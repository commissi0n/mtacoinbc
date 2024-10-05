<h1 align="center">
  <a><img src="https://github.com/commissi0n/mtacoinbc/blob/main/img/mtacoin.png" width="300"></a>
  <br>
  MTACoin Blockchain
  <br>
</h1>

<p align="center">Blockchain mining simulation using IPC via named pipes.</p>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#download">Download</a> •
  <a href="#credits">Credits</a> •
  <a href="#license">License</a>
</p>

## Key Features

* Simulates a blockchain mining process
  - Uses named pipes to communicate between the server container and the miner containers.
* Logging for each individual container
  - Each container logs its communication attempts to a specified file within its container.
* Difficulty setting
  - Option to change the difficulty - the number of leading 0's required in a hash for it to be valid.
* Cross platform
  - Windows, macOS* and Linux ready.

## How To Use

To clone and run this application, you'll need [Git](https://git-scm.com) and [Docker](https://github.com/docker):

```bash
# Clone this repository
$ git clone https://github.com/commissi0n/mtacoinbc

# Go into the repository
$ cd mtacoinbc

# Install dependencies
$ sudo apt-get install docker

# AUTOMATED
# Run the script with sudo privileges to launch the program
# Will download the relevant docker images and launch 1 server container and 4 miner containers
$ sudo sh blockchain_launcer.sh

# MANUALLY
# Fetch images from docker hub
$ sudo docker image pull commissi0n/mtacoin-server:1.0
$ sudo docker image pull commissi0n/mtacoin-miner:1.0

# Run the server container with specified shared volume
$ sudo docker run -d -v ./conf/mta/:/mnt/mta/ commissi0n/mtacoin-server:1.0

# Run the miner container with same specified shared volume
$ sudo docker run -d -v ./conf/mta/:/mnt/mta/ commissi0n/mtacoin-miner:1.0
```

## Notes
- Supports up to 4 miner containers concurrently.
- "Server" directory contains all files relevant to the server container.
- "Miner" directory contains all files relevant to the miner container.
- Log is kept in "/var/log/mtacoin.log".
- "conf/mta" directory holds the "mtacoin.conf" configuration file which sets the difficulty (default is 16).

## Download

You can download the project [here](https://github.com/commissi0n/mtacoinbc/releases/tag/v1.00).

## Credits

This software uses the following open source packages:

- [zlib](https://github.com/madler/zlib)
- [Docker](https://github.com/docker)

## License

MIT