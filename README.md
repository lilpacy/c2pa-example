# c2pa-example

## c2pa の来歴情報埋め込み

```sh
c2patool without_c2pa.png -m test.json -o with_c2pa.png -f
```

## 差分確認

```sh
c2patool with_c2pa.png
strings with_c2pa.png > with_c2pa.strings
strings without_c2pa.png > without_c2pa.strings
diff without_c2pa.strings with_c2pa.strings | colordiff
```

## 証明書の中身確認

```sh
openssl x509 -in es256_certs.pem -text -noout|less

Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            70:24:e6:24:76:05:f1:d6:5f:1b:47:75:51:d4:fa:fc:b5:ed:91:e6
        Signature Algorithm: ecdsa-with-SHA256
        Issuer: C=US, ST=CA, L=Somewhere, O=C2PA Test Intermediate Root CA, OU=FOR TESTING_ONLY, CN=Intermediate CA
        Validity
            Not Before: Jun 10 18:46:40 2022 GMT
            Not After : Aug 26 18:46:40 2030 GMT
        Subject: C=US, ST=CA, L=Somewhere, O=C2PA Test Signing Cert, OU=FOR TESTING_ONLY, CN=C2PA Signer
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (256 bit)
                pub:
                    04:0f:68:be:91:90:09:18:90:a5:38:f8:8a:f2:05:
                    26:31:24:cd:e1:ef:bb:05:88:ca:db:bd:b2:3c:7c:
                    6e:f0:d8:16:e5:f6:8b:4d:1b:f7:1c:87:70:c0:c3:
                    9a:c6:00:f5:7b:35:69:32:97:74:06:b9:5f:f0:b7:
                    43:2b:00:f0:e8
                ASN1 OID: prime256v1
                NIST CURVE: P-256
        X509v3 extensions:
            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Extended Key Usage: critical
                E-mail Protection
            X509v3 Key Usage: critical
                Digital Signature, Non Repudiation
            X509v3 Subject Key Identifier:
                17:39:CF:D3:2F:37:8E:88:8D:38:27:9D:42:4C:53:B4:03:32:35:CA
            X509v3 Authority Key Identifier:
                0E:7C:8D:72:66:BF:A2:C9:E5:00:94:EF:B5:6E:80:E2:B6:0E:2F:6B
    Signature Algorithm: ecdsa-with-SHA256
    Signature Value:
        30:44:02:20:39:8f:f6:b3:35:e3:b2:58:3f:33:22:45:67:6c:
        bb:38:7f:20:88:f6:13:b2:f4:bb:50:f4:4f:f4:62:3d:36:02:
        02:20:34:0f:30:aa:c4:2d:05:09:12:d8:a9:67:44:ea:bc:8f:
        f8:9a:27:a8:c9:10:9e:22:24:2d:ca:e4:b4:2c:00:b3
```

```sh
openssl ec -in es256_private.key -text -noout|less

Private-Key: (256 bit)
priv:
    7c:d2:41:b1:a4:4b:49:e1:e2:ce:fd:26:18:bf:a0:
    72:7e:fc:42:6b:5f:2d:29:be:9f:ea:86:f6:f7:82:
    d9:6d
pub:
    04:0f:68:be:91:90:09:18:90:a5:38:f8:8a:f2:05:
    26:31:24:cd:e1:ef:bb:05:88:ca:db:bd:b2:3c:7c:
    6e:f0:d8:16:e5:f6:8b:4d:1b:f7:1c:87:70:c0:c3:
    9a:c6:00:f5:7b:35:69:32:97:74:06:b9:5f:f0:b7:
    43:2b:00:f0:e8
ASN1 OID: prime256v1
NIST CURVE: P-256
```
