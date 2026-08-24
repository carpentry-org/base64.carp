# base64.carp

A Base64 library for Carp from scratch.

## Installation

```clojure
(load "git@github.com:carpentry-org/base64.carp@0.2.0")
```

## Usage

```clojure
(defn main []
  (let-do [encoded (Base64.encode-str "Hello, Carp!")]
    (println* &encoded)                        ; => SGVsbG8sIENhcnAh
    (println* &(Base64.decode-str &encoded)))) ; => (Success @"Hello, Carp!")
```

Currently this library exposes ten functions: `encode`, `encode-str`,
`encode-using`, `decode-using`, `decode-str`, and `decode`, plus their URL- and
filename-safe counterparts `encode-url`, `encode-url-str`, `decode-url`, and
`decode-url-str`. Both `encode-str` and `decode-str` take a reference to a string
and return a `Result`, and they implement encoding and decoding using the MIME
character set. `encode` and `decode` make no such assumptions and deal with binary
data (or rather, arrays of byte-sized integers). `encode-using` and `decode-using`
are their more general sibling functions, as they take in an additional
user-supplied character set.

The `*-url` functions use the URL- and filename-safe alphabet of RFC 4648
section 5, where `+` and `/` become `-` and `_`. Because URL-safe Base64 is
frequently transmitted without padding (for example in JWTs), the `decode-url`
functions accept input both with and without trailing `=` padding; the
`encode-url` functions always emit padding.

```clojure
(defn main []
  (let-do [data [251b 255b 254b]]
    (println* &(Base64.encode &data))                   ; => +//+
    (println* &(Base64.encode-url &data))               ; => -__-
    (println* &(Base64.decode-url-str "c3ViPTEyMzQ")))) ; => (Success @"sub=1234")
```

The decode functions return `Result`, validating that input has correct length,
only contains valid characters, and has proper padding placement. If you want,
you can check out the documentation [online](https://veitheller.de/base64/), but
it’s very sparse.

<hr/>

Have fun!
