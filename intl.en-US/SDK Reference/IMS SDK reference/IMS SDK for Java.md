# IMS SDK for Java

This topic describes how to install Identity Management Service \(IMS\) SDK for Java and provides an example on how to use IMS SDK for Java.

## Background information

For more information about IMS API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md).

## Install IMS SDK for Java

You can use one of the following methods to install IMS SDK for Java.

-   Method 1: \(Recommended\) Add dependencies by using Maven
    1.  Use Maven to create a project.

        ```
        mvn archetype:generate -DgroupId=com.aliyun.ims.sample \
        -DartifactId=ims-sdk-sample \
        -Dpackage=com.aliyun.ims.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  Add the following dependencies to the pom.xml file of the project:

        ```
        <dependency>
              <groupId>com.aliyun</groupId>
              <artifactId>ims20190815</artifactId>
              <version>1.0.0</version>
        </dependency>
        ```

-   Method 2: Download the JAR files of the SDK for Java and add them to your project

    You can use this method to install IMS SDK for Java regardless of whether you are using Eclipse or IntelliJ as the integrated development environment \(IDE\). To download the JAR files, click [Alibaba Cloud IMS SDK for Java](https://mvnrepository.com/artifact/com.aliyun/ims20190815).


## Sample code

The following code provides an example on how to call the CreateUser API operation by using IMS SDK for Java.

```
import com.aliyun.ims20190815.Client;
import com.aliyun.ims20190815.models.CreateUserRequest;
import com.aliyun.ims20190815.models.CreateUserResponse;
import com.aliyun.ims20190815.models.GetDefaultDomainRequest;
import com.aliyun.ims20190815.models.GetDefaultDomainResponse;
import com.aliyun.tearpc.models.Config;
import com.google.gson.Gson;

public class CodeSample {

    /**
     * Initialize common request parameters.
     */
    public static Client initialization() throws Exception {
        Config config = new Config();
        // The AccessKey ID.
        config.accessKeyId = "<AccessKeyId>";
        // The AccessKey secret.
        config.accessKeySecret = "<AccessKeySecret>";
        // The ID of the region.
        config.regionId = "<RegionId>";
        return new Client(config);
    }

    public static void main(String[] args) throws Exception {
        try {
            Client client = CodeSample.initialization();

            // Obtain the default domain name of the Alibaba Cloud account in the <AccountAlias>.onaliyun.com format.
            GetDefaultDomainRequest getDefaultDomainRequest = new GetDefaultDomainRequest();
            GetDefaultDomainResponse getDefaultDomainResponse = client.getDefaultDomain(getDefaultDomainRequest);
            String defaultDomain = getDefaultDomainResponse.getDefaultDomainName();

            // Create a RAM user.
            CreateUserRequest createUserRequest = new CreateUserRequest();
            // Set the logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
            String userName = "<UserName>";
            createUserRequest.userPrincipalName = String.format("%s@%s", userName, defaultDomain);
            // Set the display name of the RAM user.
            createUserRequest.displayName = "<DisplayName>";
            CreateUserResponse createUserResponse = client.createUser(createUserRequest);
            System.out.println(new Gson().toJson(createUserResponse));

        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
}
```

