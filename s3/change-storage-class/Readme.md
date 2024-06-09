## Create a bucket

aws s3 mb s3://change-storage-class-tuts --region me-central-1

## Create a file

echo "Hello world" > hello.txt
aws s3 cp hello.txt s3://change-storage-class-tuts --storage-class STANDARD_IA --region me-central-1

## Cleanup

aws s3 rm s3://change-storage-class-tuts/hello.txt --region me-central-1

aws s3 rb s3://change-storage-class-tuts --region me-central-1
