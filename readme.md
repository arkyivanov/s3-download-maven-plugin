# s3-download-maven-plugin
Plugin for maven to download a file or the contents of a directory (recursively) from S3.
(fork from: https://github.com/Upplication/s3-download-maven-plugin)

Changes were made to be able copy one file from S3 to local file with same name as it is specified in parameter "destination"


## Using in maven pom.xml :

Example: Download a bucket
----------------------
```xml
<build>
  ...

  <plugins>
    ...

    <plugin>
      <groupId>com.upplication.maven.plugins</groupId>
      <artifactId>s3-download-maven-plugin</artifactId>
      <version>1.0.2-SNAPSHOT</version>
      <executions>
        <execution>
            <phase>your phase</phase>
            <goals>
                <goal>s3-download</goal>
            </goals>
            <configuration>
                <bucketName>my-s3-bucket</bucketName>
                <!-- if you provide no source the whole bucket will be downloaded -->
                <destination>/my/local/dir/</destination>
                <accessKey>access key</accessKey>
                <secretKey>secret key</secretKey>
            </configuration>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

##List of configuration parameters
------------------------

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
|bucketName|The name of the bucket|*yes*| |
|source|The source amazon s3 file key. Empty to download the whole bucket.|*no*| |
|destination|The destination file or destination folder. Directories *MUST* end with */*| *yes*| |
|accessKey|S3 access key | *yes* | if unspecified, uses the Default Provider, falling back to env variables |
|secretKey|S3 secret key | *yes* | if unspecified, uses the Default Provider, falling back to env variables |
|endpoint|Use a different s3 endpoint| *no* | s3.amazonaws.com |


## Built and install in local maven repository

To build plugin and install it in local repository please use command:

```
mvn package install
```

## Authors

* *Initial work* - https://github.com/Upplication/s3-download-maven-plugin
* Arcady Ivanov

