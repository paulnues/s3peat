s3peat
======

s3peat is a Python module to help upload directories to S3 using parallel
threads.

.. rubric:: Installing

.. code-block:: bash

   pip install s3peat

.. rubric:: Example usage

.. code-block:: python

    from s3peat import S3Bucket, sync_to_s3

    # Create a S3Bucket instance, which is used to create connections to S3
    bucket = S3Bucket('my-bucket', AWS_KEY, AWS_SECRET)

    # Call the sync_to_s3 method
    failures = sync_to_s3(directory='my/directory', prefix='my/key,
        bucket=bucket, concurrency=50)

    # A list of filenames will be returned if there were failures in uploading
    if not failures:
        print "No failures"
    else:
        print "Failed:", failures

