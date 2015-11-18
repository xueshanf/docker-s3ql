docker-s3ql
===========

Docker build for s3ql-2.15.

To use the image:

* Create an AWS bucket.
* Create an IAM user with proper bucket policy.
* Configure authinfo2 with your S3 crendential to the s3 bucket. 
* Run the image:
* 
        docker pull xueshanf/s3ql
        docker run --rm --cap-add mknod --cap-add sys_admin --device=/dev/fuse -it xueshanf/s3ql

   You are dropped to /bin/bash command inside of the container.

Quick test:

        mkfs.s3ql --plain s3://<bucket/test
        mount.s3ql s3://<bucket/test /mnt
  
  When prompted for backend login name and passphrase, use the AWS credential that has access to the bucket. An auth template file /root/.s3ql/authinfo2 will be generated and you can put login info there so future s3ql command can use --authinfo2 file for authentication.

See [s3ql documentation](http://www.rath.org/s3ql-docs/installation.html) about how to use s3ql.

The s3ql mounted volumes (FUSE-based file system) in the container are not visiable from docker host through -v `<hostvol`>:`<containervol`> option, nor from other containsers through --volumes-from `<containername`>. 
    

