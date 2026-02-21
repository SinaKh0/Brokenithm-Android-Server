## Brokenithm-Android-Server

The Windows server of [Brokenithm-Android](https://github.com/tindy2013/Brokenithm-Android).

This fork adds `-a` (air only) and `-s` (slider only) flags, allowing two server instances to run simultaneously, one handling slider input from a tablet, one handling air input from a phone, without conflicting over shared memory.

## Build
```bash
# Requires MSYS2 with MinGW64
cmake -G "MSYS Makefiles" -DCMAKE_POLICY_VERSION_MINIMUM=3.5 .
make
```

The output `brokenithm.exe` is fully standalone with no DLL dependencies.

## Usage
```
brokenithm.exe [options]

Options:
  -p <port>   Port number (default: 52468)
  -T          TCP mode (recommended)
  -r <n>      TCP receive threshold
  -a          Air only mode (ignores slider input)
  -s          Slider only mode (ignores air input)
```

## Dual Instance Setup

To split slider and air input across two devices:
```bash
# Instance 1 — device 1 handles slider
brokenithm.exe -T -s -p 52468

# Instance 2 — device 2 handles air
brokenithm.exe -T -a -p 52469
```

Connect your tablet to port 52468 and your phone to port 52469 in the Brokenithm Android app.