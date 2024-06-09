## Create a bucket

```sh
aws s3api create-bucket --bucket acl-bucket-example --region me-central-1 --create-bucket-configuration LocationConstraint=me-central-1
```

## Turn off Block Public Access for ACLs

```sh
aws s3api put-public-access-block \
  --bucket acl-bucket-example \
  --public-access-block-configuration '{
    "BlockPublicAcls": false,
    "IgnorePublicAcls": false,
    "BlockPublicPolicy": true,
    "RestrictPublicBuckets": true
  }' \
  --region me-central-1
```

## Verify Public Access block

```sh
aws s3api get-public-access-block \
--bucket acl-bucket-example \
--region me-central-1
```

## Change Bucket Ownership

```sh
aws s3api put-bucket-ownership-controls \
    --bucket acl-bucket-example \
    --ownership-controls '{
        "Rules": [
            {
                "ObjectOwnership": "BucketOwnerPreferred"
            }
        ]
    }' \
    --region me-central-1
```

## Change ACLs to allow for a user from another AWS account

```sh
aws s3api put-bucket-acl \
--bucket acl-bucket-example \
--access-control-policy file://policy.json
```

## Access Bucket from other account

```sh
touch bootcamp.txt
aws s3 cp bootcamp.txt s3://acl-bucket-example
aws s3 ls s3://acl-bucket-example
```

## Cleanup

```sh
aws s3 rm s3://acl-bucket-example/bootcamp.txt
aws s3 rb s3://acl-bucket-example --region me-central-1
```
