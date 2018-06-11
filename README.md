# base64.carp

A Base64 library for Carp from scratch.

Currently this library only exposes four functions, `encode`, `encode-using`,
`decode-using`, and `decode`. Both `encode` and `decode` take a reference to a
string and return a string, and they implement encoding and decoding using the
MIME character set. Together, they are isomorphic. `encode-using` and
`decode-using` are there more general sibling functions, as they take in an
additional user-supplied character set. If you want, you can check out the
documentation [online](https://veitheller.de/base64/), but it’s very sparse.

<hr/>

Have fun!
