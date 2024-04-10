## S3 Error: NewerNoncurrentVersions for NoncurrentVersionExpiration action must be a positive integer

### Got this error on s3 while setting up S3 Lifecycle rules ?


One common issue that users face when setting lifecycle rules for versioned objects is that they are unable to set retention on versions less than 1. When attempting to set a lifecycle rule to retain non-current versions for 0 days, an error is thrown ```NewerNoncurrentVersions for NoncurrentVersionExpiration action must be a positive integer```

![image](https://github.com/ChroniclesOfDevOps/ChroniclesOfDevOps.github.io/assets/166585975/62bc97b7-7795-415b-bec7-b638a856f684)

The reason for this error is due to a small miss in the way the retention policy is set. In the S3 management console, users are asked to specify the "Number of newer versions to retain". If this value is set to 0, an error is thrown.

![image](https://github.com/ChroniclesOfDevOps/ChroniclesOfDevOps.github.io/assets/166585975/61a67dc0-3384-4eae-882b-40cc406b2875)

To avoid this error, users should ensure that they leave the "Number of newer versions to retain" field blank when setting a retention policy for noncurrent versions, as shown in below image. S3 will interpret this as a value of 0 and allow the retention policy to be set accordingly. This will allow them to set a retention policy of 0 days, which is useful when managing objects that are no longer needed or that are outdated.

![image](https://github.com/ChroniclesOfDevOps/ChroniclesOfDevOps.github.io/assets/166585975/a9a690e0-bdbe-4db9-b0e2-cb467b114d5d)

To conclude, Amazon S3 versioning is a valuable feature that enables businesses to store and manage multiple versions of their objects. By understanding the nuances of how S3 interprets retention policies, users can avoid common errors and manage their objects more effectively.
