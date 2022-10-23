# PlatformIO Remote Test

GitHub Action for PlatformIO Remote Test.

## Usage

`.github/workflows/platformio-test.yml`

```yml
name: PlatformIO

on: pull_request

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: PlatformIO Test
        uses: karniv00l/platformio-remote-test-action@0.1.0
        with:
          environments: "teensy35,teensy36,teensy41"
          ignores: "mytest*,test[13]"
          upload-port: "/dev/cu.SLAB_USBtoUART"
          test-port: "/dev/cu.uart-1CFF4676258F4543"
          project-dir: "./some_dir"
          force-remote: true
          without-building: false
          without-uploading: false
          verbose: true
```

## Inputs

```yml
environments:
  description: Process specified environments (comma separated).
  required: false
ignores:
  description: Ignore tests where the name matches specified patterns. More than one pattern is allowed (comma separated).
  required: false
upload-port:
  description: A port that is intended for firmware uploading.
  required: false
test-port:
  description: A Serial/UART port that PlatformIO uses as communication interface between PlatformIO Unit Test Engine and target device.
  required: false
project-dir:
  description: Specify the path to project directory. By default, project-dir is equal to current working directory (CWD).
  required: false
force-remote:
  description: By default, Remote Development processes project on a host machine and deploy final testing firmware (program) to remote device (embedded board).
  required: false
without-building:
  description: Skip building stage.
  required: false
without-uploading:
  description: Skip uploading stage.
  required: false
verbose:
  description: Shows detailed information when processing environments.
  required: false
```
