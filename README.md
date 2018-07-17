# base64.carp

A Base64 library for Carp from scratch.

Currently this library only exposes six functions, `encode`, `encode-str`,
`encode-using`, `decode-using`, `decode-str`, and `decode`. Both `encode-str` and
`decode-str` take a reference to a string and return a string, and they implement
encoding and decoding using the MIME character set. `encode` and `decode` make no
such assumptions and deal with binary data (or rather, arrays of byte-sized
integers). `encode-using` and `decode-using` are there more general sibling
functions, as they take in an additional user-supplied character set. If you want,
you can check out the documentation [online](https://veitheller.de/base64/), but
it’s very sparse.

<hr/>

Have fun!
