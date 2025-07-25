# TLS Configuration

```{.yaml linenums="1"}
proxies:
- name: "tls-example"
  tls: true
  sni: example.com
  servername: example.com
  fingerprint: xxx
  alpn:
  - h2
  - http/1.1
  skip-cert-verify: true
  client-fingerprint: random
  reality-opts:
    public-key: xxxx
    short-id: xxxx
    support-x25519mlkem768: true
  ech-opts:
    enable: true
    config: base64_encoded_config
```

## TLS

Enables TLS, applicable only to protocols that use `tls`, with the `trojan` protocol requiring it to be enabled.

## SNI/Servername

The server name indication, referred to as `servername` in [`VMess`](./vmess.md)/[`VLESS`](./vless.md). If left empty, it defaults to the address in `server`.

## Fingerprint

Certificate fingerprint, applicable only to protocols that use `tls`.

## ALPN

List of supported Application Layer Protocol Negotiation options, arranged in order of priority.

If both peers support ALPN, the selected protocol will be one from this list; if there are no mutually supported protocols, the connection will fail.

Refer to [Application-Layer Protocol Negotiation](https://en.wikipedia.org/wiki/Application-Layer_Protocol_Negotiation)

## Skip Cert Verify

Bypasses certificate verification, applicable only to protocols that use `tls`.

## Client Fingerprint

Client uTLS fingerprint, applicable only to [`VMess`](./vmess.md)/[`VLESS`](./vless.md)/[`Trojan`](./trojan.md) protocols. For optional details, refer to [Global Client Fingerprint](../general.md#global-client-fingerprint).

## Reality Options

Configuration for reality; if not empty, reality will be enabled.

### reality-opts.public-key

Public key corresponding to the reality server's private key.

### reality-opts.short-id

One of the server's short IDs.

### reality-opts.support-x25519mlkem768

Support for X25519-MLKEM768 key exchange.

## ECH Options

### ech-opts.enable

Enables ECH (Encrypted Client Hello). If not empty, ECH will be enabled.

### ech-opts.config

Base64-encoded configuration for ECH.

