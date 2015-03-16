#Fake-S3
Simple container that runs [jubos/fake-s3](https://github.com/jubos/fake-s3)

##Run
docker run --name fake-s3 -d jrlangford/fake-s3

##Usage

To create a "context" with jclouds

```
...
import java.util.Properties;                                                                                                                                                                                                                  
import static org.jclouds.s3.reference.S3Constants.PROPERTY_S3_VIRTUAL_HOST_BUCKETS;
...

Properties properties = new Properties();                                                                                                                                                                                         
properties.setProperty(PROPERTY_S3_VIRTUAL_HOST_BUCKETS, "false");                                                                                                                                                                
																											      
context =  ContextBuilder.newBuilder("aws-s3")                                                                                                                                                                         
			 .endpoint("http://fake-s3:4567")                                                                                                                                                                     
			 .credentials("dummy_access_key", "dummy_secret_key")                                                                                                                                                 
			 .overrides(properties)                                                                                                                                                                               
			 .buildView(BlobStoreContext.class);
```
