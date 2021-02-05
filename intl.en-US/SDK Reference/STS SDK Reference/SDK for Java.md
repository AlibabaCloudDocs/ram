# SDK for Java

This topic describes how to install the SDK for Java and provides sample code.

## Background information

-   To use the SDK for Java, you must install the core library of the Alibaba Cloud SDK for Java \(`aliyun-java-sdk-core`\) and the Security Token Service \(STS\) SDK \(`aliyun-java-sdk-sts`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For more information about STS API operations, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md).
-   For more information about STS endpoints, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Install the SDK for Java

You can use one of the following methods to install the SDK for Java. For more information about how to install the SDK for Java, see [Quick start]().

-   Method 1: \(Recommended\) Add dependencies by using Maven
    1.  Use Maven to create a project.

        ```
        mvn archetype:generate -DgroupId=com.aliyun.sts.sample \
        -DartifactId=sts-sdk-sample \
        -Dpackage=com.aliyun.sts.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  Add the following dependencies to the pom.xml file of the project:

        ```
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-sts</artifactId>
            <version>3.0.0</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>4.4.6</version>
        </dependency>
        ```

        **Note:** You can visit the [Maven repository](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core) to obtain the latest version of the `aliyun-java-sdk-core` package.

-   Method 2: Download the JAR files of the SDK for Java and add these JAR files to your project

    You can use this method to install the SDK for Java regardless of whether you are using Eclipse or IntelliJ as the integrated development environment \(IDE\). You can download the JAR files from the following links:

    -   [Java SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)
    -   [STS SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-sts)

## Example

The following sample code shows how to call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation of the SDK for Java. You can visit [OpenAPI Explorer](https://api.aliyun.com/) to debug other API operations and obtain the related sample code.

```
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.exceptions.ServerException;
import com.aliyuncs.profile.DefaultProfile;
import com.google.gson.Gson;
import java.util.*;
import com.aliyuncs.sts.model.v20150401.*;

public class AssumeRole {

    public static void main(String[] args) {
        // Construct an Alibaba Cloud client that is used to initiate requests.
        // When you construct the client, specify the AccessKey ID and AccessKey secret.
        DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);

        // Construct a request and specify request parameters. For more information about the parameters, see API Reference.
        AssumeRoleRequest request = new AssumeRoleRequest();
        request.setRegionId("cn-hangzhou");
        request.setRoleArn("<RoleArn>");
        request.setRoleSessionName("<RoleSessionName>");
        
        // Initiate a request and obtains a response.
        try {
            AssumeRoleResponse response = client.getAcsResponse(request);
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

