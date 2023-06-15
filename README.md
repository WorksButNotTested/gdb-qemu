# GDB-QEMU
`gdb-qemu` is a launcher for running `qemu-user` within `gdb`.

# Test
```
$ cargo make gdb
```

# Example
```
gdb-multiarch \
  -ex "set architecture powerpc:MPC8XX" \
  -ex "set pagination off" \
  -ex "set confirm off" \
  -ex "file demo" \
  -ex "target remote | gdb-qemu -p 1234 qemu-ppc -- -L /usr/powerpc-linux-gnu -g 1234 demo
```

# Usage
```
Tool launching qemu-user for debugging

Usage: gdb-qemu [OPTIONS] --port <PORT> <PROGRAM> [-- <ARGS>...]

Arguments:
  <PROGRAM>
          Name of the qemu-user binary to launch

  [ARGS]...
          Arguments passed to the target

Options:
  -p, --port <PORT>
          Port

  -t, --timeout <TIMEOUT>
          Timeout Ms

          [default: 2000]

  -l, --log-file <LOG_FILE>
          Log file (Requires --log-level)

          [default: gdb-qemu.log]

  -L, --log-level <LOG_LEVEL>
          Log level

          [default: off]
          [possible values: off, error, warn, info, debug, trace]

  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version
```
