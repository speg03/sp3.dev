# AWS

## S3

* 署名付きURLの発行

```
aws s3 presign --expires-in 3600 s3://bucket_name/object_key
```

指定したオブジェクトを一時的に公開してダウンロードできるURLを発行する。`expires-in`は発行した署名付きURLの期限。デフォルトでは3600秒（1時間）。
