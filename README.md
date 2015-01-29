docker-s3ql
===========

Docker build for s3ql-2.12.

To use the image:
1. Create an AWS bucket.
2. Create an IAM user with proper bucket policy.
3. Configure authinfo2 with your S3 crendential to the s3 bucket. 
4. Run the image

        docker pull xueshanf/s3ql
        docker run --rm --cap-add mknod --cap-add sys_admin --device=/dev/fuse -it xueshanf/s3ql

   You are dropped to /bin/bash command inside of the container.

See s3ql documentation about how to use s3ql.

The s3ql mounted volumes (FUSE-based file system) in the container are not visiable from docker host through -v `<hostvol`>:`<containervol`> option, nor from other containsers through --volumes-from `<containername`>. 
    

