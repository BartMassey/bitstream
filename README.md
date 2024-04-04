![Maintenance](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)
[![crates-io](https://img.shields.io/crates/v/bitstream.svg)](https://crates.io/crates/bitstream)
[![api-docs](https://docs.rs/bitstream/badge.svg)](https://docs.rs/bitstream)
[![dependency-status](https://deps.rs/repo/github/BartMassey/bitstream/status.svg)](https://deps.rs/repo/github/BartMassey/bitstream)

# bitstream: bit queue
Copyright © 2024 Bart Massey (Version 0.1.0)

A `BitStream` is a queue that you can stuff bits into and
extract bits out of, in (almost) arbitrary-length chunks.

Bits are inserted and removed LSB…MSB (little-endian).

## Examples

Consider this sequence of operations:

```
    make a bs
    0010 -> bs
    1001000001 -> bs
    take 6 from bs (-> 010010)
    take 7 from bs (-> 0010000)
    take 1 from bs (-> 1)
    bs is empty (true)
```

The code would look something like this:

```rust
let mut bs = bitstream::BitStream::default();
bs.insert(0b0010_u8, 4);
bs.insert(0b1001000001_u16, 10);
assert_eq!(0b010010, bs.extract(6).unwrap());
assert_eq!(0b0010000, bs.extract(7).unwrap());
assert_eq!(0b1, bs.extract(1).unwrap());
assert!(bs.is_empty());
```

## Features

The feature `std` is enabled by default. Disable it to
compile this as a `no_std` crate. This will limit the stream
buffer to [NCHUNK] bits.


# License

This work is licensed under the "MIT License". Please see the file
`LICENSE.txt` in this distribution for license terms.
