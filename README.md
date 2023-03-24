Commands reminder:

0. ZMK repo URL
`https://github.com/zmkfirmware/zmk.git`

1. To setup docker container:
`$ docker run -v <HOST>:<TARGET> -it zmkfirmware/zmk-build-arm:3.0-branch /bin/bash`

2. Setup ZMK environment in a Docker container
_in <ZMK_REPO>_

`$ west init -l app && west update`

3. Build the firmware in a Docker container
_in <ZMK_REPO>/app_

3.1. Left shield:
`$ west build -d build/left -b nice_nano_v2 -- -DSHIELD=cradio_left -DZMK_CONFIG="<ZMK_CONFIG_PATH_IN_THE_CONTAINER>"`

3.2. Right shield:
`$ west build -d build/right -b nice_nano_v2 -- -DSHIELD=cradio_right -DZMK_CONFIG="<ZMK_CONFIG_PATH_IN_THE_CONTAINER>"`

4. Install the firmware
`udisksctl mount -b /dev/disk/by-id/usb-Adafruit_nRF_UF2* && cp <PATH>/zmk.uf2 /run/media/glaeqen/NICENANO`
