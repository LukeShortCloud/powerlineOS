# powerlineOS

A Chromium OS fork designed to test experimental features.

## Directory Structure

- google = Projects from Google relating to Chromium OS.
    - [board-overlays](https://chromium.googlesource.com/chromiumos/overlays/board-overlays/+/refs/heads/main)
        - overlay-powerlineos-amd64 = An overlay for building Chromium OS based on "overlay-amd64-generic".
- powerline = Custom projects made for powerlineOS.
- third_party = Projects from third-party vendors (not Google) relating to Chromium OS.

## powerlineOS Development Environment

- Setup and enter a [Chromium OS development environment](https://rootpages.lukeshort.cloud/linux_distributions/chromium_os.html#development-environment).
- Set an environment variable for the directory where `repo init` and `repo sync` were ran.

    ```
    $ export CROS_SDK_DIR="/home/$USER/github/chromiumos"
    ```

- Copy the powerlineOS files over.

    ```
    $ rsync -a -u -r -v -P google/overlays/overlay-powerlineos-amd64 ${CROS_SDK_DIR}/src/overlays/
    ```

- Build powerlineOS.

    ```
    $ export BOARD=powerlineos-amd64
    $ setup_board --board=${BOARD}
    $ ./build_packages --nowithdebug --board=${BOARD}
    $ ./build_image --board=${BOARD} --noenable_rootfs_verification dev
    ```

## License

[Apache Software License v2.0](LICENSE)
