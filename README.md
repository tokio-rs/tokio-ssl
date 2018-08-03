# tokio-tls

An implementation of TLS/SSL streams for Tokio built on top of the [`native-tls`
crate]

[![Build Status](https://travis-ci.org/tokio-rs/tokio-tls.svg?branch=master)](https://travis-ci.org/tokio-rs/tokio-tls)
[![Build status](https://ci.appveyor.com/api/projects/status/iiut5d2mts6bt5g1?svg=true)](https://ci.appveyor.com/project/alexcrichton/tokio-tls)

[Documentation](https://docs.rs/tokio-tls)

[`native-tls` crate]: https://github.com/sfackler/rust-native-tls

## Usage

First, add this to your `Cargo.toml`:

```toml
[dependencies]
native-tls = "0.2"
tokio-tls = "0.2"
```

Next, add this to your crate:

```rust
extern crate native_tls;
extern crate tokio_tls;

use tokio_tls::{TlsConnectorExt, TlsAcceptorExt};
```

You can find few examples how to use this crate in examples directory (using TLS in 
hyper server or client).

This crate provides two extension traits, `TlsConnectorExt` and
`TlsAcceptorExt`, which augment the functionality provided by the [`native-tls`
crate]. These extension traits provide the ability to connect a stream
asynchronously and accept a socket asynchronously. Configuration of TLS
parameters is still done through the support in the `native-tls` crate.

By default the `native-tls` crate currently uses the "platform appropriate"
backend for a TLS implementation. This means:

* On Windows, [SChannel] is used
* On OSX, [SecureTransport] is used
* Everywhere else, [OpenSSL] is used

[SChannel]: https://msdn.microsoft.com/en-us/library/windows/desktop/aa380123%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396
[SecureTransport]: https://developer.apple.com/reference/security/1654508-secure_transport
[OpenSSL]: https://www.openssl.org/

Typically these selections mean that you don't have to worry about a portability
when using TLS, these libraries are all normally installed by default.

# License

This project is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or
   http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in tokio-tls by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
