# mi-debian-9

This repo contains live-build files and scripts to create an custom Debian 9
ISO and image for deploying on SmartOS and Smart Data Center.

For more information on live-build see the [live-build manual](https://live-team.pages.debian.net/live-manual/html/live-manual/index.en.html)

## Requirements

In order to use this repo, you need to have the following:

 * A running Debian instance (physical or virtual) with spare disk space and  live-build 5.* installed.
 * A SmartOS machine

 
## Install live-build via the git repo

Clone the repo and build the package:
```
git clone https://salsa.debian.org/live-team/live-build.git
cd live-build
git reset --hard debian/1%20190311
dpkg-buildpackage -b -uc -us
cd ..
```

Then install the newly build *deb file:

```
dpkg -i live-build_20190311_all.deb
```

## Configure

Modify the scripts in `auto\` and `config` depending on how you want your ISO configured. See the [live-build manual](https://live-team.pages.debian.net/live-manual/html/live-manual/index.en.html) for more information.


## Usage

Create the custom ISO with:

```
./create-iso
```
Once complete, your custom ISO will be available in the root of this repository.

On a SmartOS machine, you can then create and image with:

```
./create-image -i <ISO> -n <IMAGE_NAME> -d <DESC> -u <HOMEPAGE> -o <OWNER_UUID> -p <IP> -m NETMASK -g <GATEWAY> -v <VLAN_ID> -U <NETWORK_UUID>
```
See `./create-image -h` for usage.
