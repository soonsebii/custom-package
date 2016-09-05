# Custom-packages

## Install

#### 1. Add this repository.
```bash
$ echo "src-git custom https://github.com/soonsebii/openwrt-custom-package.git" >> feeds.conf.default
```

#### 2. Install
```bash
$ ./script/feeds update custom
$ ./script/feeds install -a custom
```

#### 3. If any problem occurs when installing, see the following.
```bash
$ tree -d ./package/feeds | grep node // The Node.js may be installed already. (in OpenWRT Core)
$ ./script/feeds uninstall node
$ ./script/feeds install -p custom node
```

## List
| Name                         | Description                       |
| ---------------------------- | --------------------------------- |
| rt_rdm | Patched AUTO_MAKENODE. |
| reg | register the read/write test program. The rt_rdm module must be put in first. |
| [lirc_node](https://github.com/alexbain/lirc_node) | Control LIRC from Node. |
| [lirc_web](https://github.com/alexbain/lirc_web) | A NodeJS / Express app that creates a web UI + API for LIRC. |
| [mqtt.js](https://github.com/mqttjs/MQTT.js) | A library for the MQTT protocol. |
| [noble](https://github.com/sandeepmistry/noble) | A Node.js BLE (Bluetooth Low Energy) central module. |
| [lirc-gpio-generic](https://github.com/danitool/openwrt-pkgs/tree/cc/lirc-gpio-generic) | LIRC GPIO receiver / blaster. |
| [lirc](https://github.com/danitool/openwrt-pkgs/tree/cc/lirc) | Linux Infrared Remote Control. |
| [moment](https://github.com/moment/moment) | Parse, validate, manipulate, and display dates in javascript. |
| [simple-restful-api](https://github.com/soonsebii/simple-restful-api) | Lightweight RESTful API Server. |
| [webworker-threads](https://github.com/audreyt/node-webworker-threads) | Lightweight Web Worker API implementation with native threads |

## 
