#Fake-S3
Simple container that runs [jubos/fake-s3](https://github.com/jubos/fake-s3)

##Run
```
docker run --name fake-s3 -d jrlangford/fake-s3
```

##Usage

The fake-s3 server can be reached through the container's IP or through a 
manually created DNS entry.

If the application using the fake-s3 server is running inside a container then
linking directly to fake-s3 is enough to make it accessible.

Example:
```
docker run --link fake-s3:fake-s3 myImage
```

###jclouds

A BlobStoreContext can be created in the following way:

```
...
import java.util.Properties;                                                                                                                                                                                                                  
import static org.jclouds.s3.reference.S3Constants.PROPERTY_S3_VIRTUAL_HOST_BUCKETS;
...

Properties properties = new Properties();                                                                                                                                                                                         
properties.setProperty(PROPERTY_S3_VIRTUAL_HOST_BUCKETS, "false");                                                                                                                                                                
																											      
BlobStoreContext context =  ContextBuilder.newBuilder("aws-s3")                                                                                                                                                                         
			 .endpoint("http://fake-s3:4567")                                                                                                                                                                     
			 .credentials("dummy_access_key", "dummy_secret_key")                                                                                                                                                 
			 .overrides(properties)                                                                                                                                                                               
			 .buildView(BlobStoreContext.class);
```
