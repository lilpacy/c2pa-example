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
