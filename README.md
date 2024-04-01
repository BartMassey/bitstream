![Maintenance](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)
[![crates-io](https://img.shields.io/crates/v/bitstream.svg)](https://crates.io/crates/bitstream)
[![api-docs](https://docs.rs/bitstream/badge.svg)](https://docs.rs/bitstream)
[![dependency-status](https://deps.rs/repo/github/BartMassey/bitstream/status.svg)](https://deps.rs/repo/github/BartMassey/bitstream)

# bitstream: bit queue
Copyright © 2024 Bart Massey (Version 0.1.0)

A [BitStream] is a queue that you can stuff bits into, and then later
extract bits out of, in (almost) arbitrary-length chunks.

For example

    make a bs
    0010 -> bs
    0001000001 -> bs
    take 6 from bs (-> 001000)
    take 7 from bs (-> 0100000)
    take 1 from bs (-> 1)
    bs is empty (true)

# License

This work is licensed under the "MIT License". Please see the file
`LICENSE.txt` in this distribution for license terms.
