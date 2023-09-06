# IBM-1047
Conversions to and from IBM-1047 in Rust.

`\n` is encoded as `0x15` and `U+0085` is encoded as `0x25`.

## Usage

```rust
use ibm1047::Encode;

// Warning: flatten will discard characters that cannot be encoded as IBM-1047.
let ebcdic: Vec<u8> = "Hello, World!\n".encode_ibm1047().flatten().collect();
let string: String = ibm1047::decode(&ebcdic).collect();

assert_eq!(string, "Hello, World!\n");
```

Decoding directly to a string requires the `alloc` feature.

```rust
use ibm1047::Decode;
let name = String::from_ibm1047(&ebcdic);
```
