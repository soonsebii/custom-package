# Custom-packages

## Installation

#### Add this repository.
```bash
$ echo "src-git custom https://github.com/soonsebii/openwrt-custom-package.git" >> feeds.conf.default
```

#### Install
```bash
$ ./script/feeds update custom
$ ./script/feeds install -a -p custom
```

## Issues

#### If any problem occurs when installing, see the following.
```bash
$ tree -d ./package/feeds | grep node // The Node.js may be installed already. (in OpenWRT Core)
$ ./script/feeds uninstall node
$ ./script/feeds install -p custom node

// bluez
$ tree -d ./pcakge/feeds | grep blue*
$ ./script/feeds uninstall bluez-utils
$ ./script/feeds install -p custom bluez-utils
```

#### Module version missmatch.
```
// In such a case, you may need to modify the Node.js's version in Makefile.
$ find . -name "Makefile" -exec sed -i 's/0\.12\.7/4\.5\.0/g' {} \; // 0.12.7 -> 4.5.0
```

## Package List

#### Linux
| Name                         | Description                       |
| ---------------------------- | --------------------------------- |
| rt_rdm | Patched AUTO_MAKENODE. |
| bluez | Bluez 5.38 |
| [lirc-gpio-generic](https://github.com/danitool/openwrt-pkgs/tree/cc/lirc-gpio-generic) | LIRC GPIO receiver / blaster. |
| [lirc](https://github.com/danitool/openwrt-pkgs/tree/cc/lirc) | Linux Infrared Remote Control. |
| reg | register the read/write test program. The rt_rdm module must be put in first. |

#### Node.js
| Name                         | Description                       |
| ---------------------------- | --------------------------------- |
| [debug](https://github.com/visionmedia/debug) | tiny node.js & browser debugging utility for your libraries and applications. |
| [gc-profiler](https://github.com/bretcope/node-gc-profiler) | gc-profiler for Node.js |
| [lirc_node](https://github.com/alexbain/lirc_node) | Control LIRC from Node. |
| [lirc_web](https://github.com/alexbain/lirc_web) | A NodeJS / Express app that creates a web UI + API for LIRC. |
| [moment](https://github.com/moment/moment) | Parse, validate, manipulate, and display dates in javascript. |
| [mqtt.js](https://github.com/mqttjs/MQTT.js) | A library for the MQTT protocol. |
| [noble](https://github.com/sandeepmistry/noble) | A Node.js BLE (Bluetooth Low Energy) central module. |
| node | Node.js 4.5 |
| [simple-restful-api](https://github.com/soonsebii/simple-restful-api) | Lightweight RESTful API Server. |
| [webworker-threads](https://github.com/audreyt/node-webworker-threads) | Lightweight Web Worker API implementation with native threads |

## License
MIT
