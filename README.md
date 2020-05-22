# Gemini Diagnostics

A torture test for [gemini](https://portal.mozz.us/gemini/gemini.circumlunar.space/) servers.

## Requirements

Python 3.7 or higher.

Tests that inspect TLS certificates additionally require that the [pyca/cryptography](https://cryptography.io/en/latest/installation/) library be installed.

## History

This script originated from an idea on the [gemini mailing list](https://lists.orbitalfox.eu/listinfo/gemini) that it would be nice to have a gemini "torture test" to uncover bugs and unhandled edge cases in new server implementations. It was originally called *jetforce-diagnostics* and was bundled with the [jetforce](https://github.com/michael-lazar/jetforce) server. Now it has been moved to its own repository and operates as a separate project.

## Usage

```
usage: gemini-diagnostics [host] [port] [--help]

A diagnostic tool for gemini servers.

This program will barrage your server with a series of requests in
an attempt to uncover unexpected behavior. Not all of these checks
adhere strictly to the gemini specification. Some of them are
general best practices, and some trigger undefined behavior. Results
should be taken with a grain of salt and analyzed on their own merit.

positional arguments:
  host             server hostname (default: localhost)
  port             server port (default: 1965)

optional arguments:
  -h, --help       show this help message and exit
  --checks CHECKS  comma separated list of checks to apply
  --show-checks    display the complete list of checks and exit
  --delay DELAY    seconds to sleep between checks (default: 2)
```

## Supported Tests

<dl>
<dt>[IPv4Address]</dt>
<dd>Establish a connection over an IPv4 address.</dd>

<dt>[IPv6Address]</dt>
<dd>Establish a connection over an IPv6 address.</dd>

<dt>[TLSVersion]</dt>
<dd>Server must negotiate at least TLS v1.2, ideally TLS v1.3.</dd>

<dt>[TLSClaims]</dt>
<dd>Certificate claims must be valid.</dd>

<dt>[TLSVerified]</dt>
<dd>Certificate should be self-signed or have a trusted issuer.</dd>

<dt>[TLSRequired]</dt>
<dd>Non-TLS requests should be refused.</dd>

<dt>[ConcurrentConnections]</dt>
<dd>Server should support concurrent connections.</dd>

<dt>[Homepage]</dt>
<dd>Request the gemini homepage.</dd>

<dt>[HomepageRedirect]</dt>
<dd>A URL with no trailing slash should redirect to the canonical resource.</dd>

<dt>[PageNotFound]</dt>
<dd>Request a gemini URL that does not exist.</dd>

<dt>[RequestMissingCR]</dt>
<dd>A request without a <CR> should timeout.</dd>

<dt>[URLIncludePort]</dt>
<dd>Send the URL with the port explicitly defined.</dd>

<dt>[URLSchemeMissing]</dt>
<dd>A URL without a scheme should be inferred as gemini.</dd>

<dt>[URLByIPAddress]</dt>
<dd>Send the URL using the IPv4 address.</dd>

<dt>[URLInvalidUTF8Byte]</dt>
<dd>Send a URL containing a non-UTF8 byte sequence.</dd>

<dt>[URLMaxSize]</dt>
<dd>Send a 1024 byte URL, the maximum allowed size.</dd>

<dt>[URLAboveMaxSize]</dt>
<dd>Send a 1025 byte URL, above the maximum allowed size.</dd>

<dt>[URLWrongPort]</dt>
<dd>A URL with an incorrect port number should be rejected.</dd>

<dt>[URLWrongHost]</dt>
<dd>A URL with a foreign hostname should be rejected.</dd>

<dt>[URLSchemeHTTP]</dt>
<dd>Send a URL with an HTTP scheme.</dd>

<dt>[URLSchemeHTTPS]</dt>
<dd>Send a URL with an HTTPS scheme.</dd>

<dt>[URLSchemeGopher]</dt>
<dd>Send a URL with a Gopher scheme.</dd>

<dt>[URLEmpty]</dt>
<dd>Empty URLs should not be accepted by the server.</dd>

<dt>[URLRelative]</dt>
<dd>Relative URLs should not be accepted by the server.</dd>

<dt>[URLInvalid]</dt>
<dd>Random text should not be accepted by the server.</dd>

<dt>[URLDotEscape]</dt>
<dd>A URL should not be able to escape the root using dot notation.</dd>

</dl>

## Contributing

Contributions are welcome!
