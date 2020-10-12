# F´ GPS Tutorial App

This is an example F´ driver for a NEMA compatible GPS built in the F´ GPS Tutorial (TODO: link?).
It has been built to run on the raspberry pi but should work on any linux system.

## Building

1. Run `git clone --recurse-submodules` to checkout this repository and its submodules.
2. If you're cross compiling, change the default toolchain in `GpsApp/settings.ini` to the correct
   target (ex. `raspberrypi`).
3. In the `GpsApp` directory, run `fprime-util generate`, then `fprime-util install` to build the app.

## Running

The `GpsApp` binary will be in the `bin` directory and after copying to the target can be run
directly. It defaults to listening to a GPS on the `/dev/ttyUSB0` serial port, but the `-d` argument
can be used to manually set the GPS serial port. The `-a` sets the location of the GDS to connect
to.

```shell
# On target
$ ./GpsApp -a <GDS IP> -d /dev/ttyUSB0
# On host computer
$ fprime-gds -n --dictionary GpsApp/Top/GpsAppTopologyAppDictionary.xml
```
