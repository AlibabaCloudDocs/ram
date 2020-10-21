# RAM SDK for Java

This topic describes how to install RAM SDK for Java and provides an example about how to use the SDK for Java.

## Background information

-   To use an SDK for Java, you must install the core library of Alibaba Cloud SDK for Java \(`aliyun-java-sdk-core`\) and the RAM SDK \(`aliyun-java-sdk-ram`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [List of operations by function](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Java

You can use one of the following methods to install the SDK for Java. For more information about how to install the SDK for Java, see [Quick start]().

-   Method 1: \(Recommended\) Add dependencies by using Maven
    1.  Use Maven to create a project.

        ```
        mvn archetype:generate -DgroupId=com.aliyun.ram.sample \
        -DartifactId=ram-sdk-sample \
        -Dpackage=com.aliyun.ram.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  Add the following dependencies to the pom.xml file of the project:

        ```
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-ram</artifactId>
            <version>2.0.7</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>4.4.6</version>
        </dependency>
        ```

        **Note:** You can visit the [Maven repository](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core) to obtain the latest version of the `aliyun-java-sdk-core` package.

-   Method 2: Download the JAR files of the SDK for Java and add them to your project

    You can use this method to install the SDK for Java regardless of whether you are using Eclipse or IntelliJ as the integrated development environment \(IDE\). You can download the JAR files from the following links:

    -   [Java SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)
    -   [RAM SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-ram)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for Java. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.exceptions.ServerException;
import com.aliyuncs.profile.DefaultProfile;
import com.google.gson.Gson;
import java.util.*;
import com.aliyuncs.ram.model.v20150501.*;

public class CreateUser {

    public static void main(String[] args) {
        
        // Construct an Alibaba Cloud client that is used to initiate requests.
        // When you construct the client, specify the AccessKey ID and AccessKey secret.
        DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);
        
        // Construct a request and configure the request parameters.
        CreateUserRequest request = new CreateUserRequest();
        request.setRegionId("cn-hangzhou");
        request.setUserName("<UserName>");
        
        // Initiate the request and obtain a response.
        try {
            CreateUserResponse response = client.getAcsResponse(request);
            System.out.println(new Gson().toJson(response));
        } catch (ServerException e) {
            e.printStackTrace();
        } catch (ClientException e) {
            System.out.println("ErrCode:" + e.getErrCode());
            System.out.println("ErrMsg:" + e.getErrMsg());
            System.out.println("RequestId:" + e.getRequestId());
        }

    }
}
```

