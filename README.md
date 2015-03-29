# Minimum TLS version

Allows you to easily specify a mimimum TLS/SSL version for node.js and io.js [`secureProtocol` option](https://iojs.org/api/tls.html).

All TLS/SSL versions older than the minimum will be disabled. The full list of TLS/SSL versions is below.

## Usage

Just load the module:

	var minimumTLSVersion = require('minimum-tls-version');

Then specify the minimum TLS version. For example:

	minimumTLSVersion('tlsv11')

...would disable all TLS/SSL versions older than tlsv11 (eg, tlsv1, sslv3 and sslv2 are now disabled):

Whereas:

	minimumTLSVersion('sslv3')

...would disable all TLS/SSL versions older than sslv3 (eg, sslv2 is disabled):

You'd normally use these values with `https.createServer`s `secureOptions` option, eg, in plain node:

	https.createServer({
		key: privateKey,
		cert: certificate,
		ca: certificateAuthority,
		secureOptions: minimumTLSVersion('tlsv11')
	});

Or for express.js

	var server = https.createServer({
		key: privateKey,
		cert: certificate,
		ca: certificateAuthority,
		secureOptions: minimumTLSVersion('tlsv11')
	}, app);


## Quick recap of TLS/SSL versions

### tlsv12 (when using OpenSSL 1.0.1 and later)

Defined in [RFC 5246](https://tools.ietf.org/html/rfc5246)

### tlsv11 (when using OpenSSL 1.0.1 and later)

Defined in [RFC 4346](https://tools.ietf.org/html/rfc4346).

### tlsv1

The Transport Layer Security (TLS) protocol, version 1.0, defined in [RFC 2246](https://tools.ietf.org/html/rfc2246).

### sslv3

The Secure Sockets Layer (SSL) protocol, version 3.0, from the Netscape Corporation.

### sslv2

The Secure Sockets Layer (SSL) protocol, version 2.0. It is the original SSL protocol as designed by Netscape Corporation. Though its use has been deprecated, because of weaknesses in the security of the protocol.
