node-wrapper
============

Downloads, builds, and proxies to node locally.  This allows you to automatically manage the installed version of node. Traditionally, installing Node.js on a linux server requires root access to `configure && make && sudo make install`. This script will build and install Node.js as a non super user and correctly reference the binaries. The version of Node.js installed can be easily managed by changing a environment variable.

###Installation
Download the two executables `nodew` and `npmw` to your desired location (or clone the repository).

###Requirements
Linux/Unix - As long as you can manually compile and build node on your machine, you should be good to go. This was tested in Linux but not in MacOS.

Because the script will remotely fetch the current node version, it requires `curl`. If you specifically define the version of node, this request and subsequently `curl` is unnecessary. 

###Usage
The first time running either the node or npm wrapper, node will be downloaded, built, and cached locally. Subsequent calls to `nodew` and `npmw` should directly proxy to the cached binaries. All parameters passed to the wrapper executables will be directly passed to the underlying node/npm binaries.

```shell
./npmw install --save express
./nodew app.js
```

If you would like install and run global packages, you will need to add `/home/<youruser>/.node/node-install/bin` (or to your custom nodew install path) to your path.

###Options
Configure the behavior of the wrappers with the following environment variables:
 * `NODEW_INSTALL_PATH` - The location which node will be downloaded and cached - *needs* to be an absolute path - defaults to `/home/<your-user>/.node`
 * `NODEW_INSTALL_VERSION` - The version of Node to install - defaults to the value in https://raw.githubusercontent.com/blittle/node-wrapper/master/node-version
