# Common methods:

 - create s3 client

```
import boto3
s3_client = boto3.client('s3')
```

 - upload and download files:

```
s3_client.upload_file('local_file.txt', 'bucket_name', 's3_key.txt')
s3_client.download_file('bucket_name', 's3_key.txt', 'local_file.txt')
```

 - list objects in a bucket
```
response = s3_client.list_objects_v2(Bucket='bucket_name')
for obj in response['Contents']:
    print(obj['Key'])
```

 - create a bucket

```
s3_client.create_bucket(Bucket='new_bucket_name')
```

 - delete an object

```
s3_client.delete_object(Bucket='bucket_name', Key='s3_key.txt')
```
