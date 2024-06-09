## Create a bucket

```sh
aws s3 mb s3://bucket-policy-example-1 \
--region me-central-1
```

## Update bucket policy

```sh
aws s3api put-bucket-policy \
--bucket bucket-policy-example-1 \
--policy file://policy.json \
--region me-central-1
```
