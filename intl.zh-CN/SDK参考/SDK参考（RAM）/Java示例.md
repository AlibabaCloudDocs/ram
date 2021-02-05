# Java示例

本文简要介绍了Java SDK的安装方法，并提供了示例代码。

## 背景信息

-   Java SDK包含阿里云Java SDK基础包（`aliyun-java-sdk-core`）和RAM接口定义包（`aliyun-java-sdk-ram`），两者都需要安装。
-   [OpenAPI开发者门户](https://next.api.aliyun.com)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于RAM API的详情，请参见[API概览](/intl.zh-CN/API参考/API参考（RAM）/API概览.md)。

## Java SDK的安装方法

您可以通过下面两种方法安装Java SDK。具体的安装方法，请参见[快速开始]()。

-   方法一：通过Maven管理项目依赖（推荐）
    1.  使用Maven创建项目：

        ```
        mvn archetype:generate -DgroupId=com.aliyun.ram.sample \
        -DartifactId=ram-sdk-sample \
        -Dpackage=com.aliyun.ram.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  在项目的pom.xml文件中加入相应依赖项：

        ```
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-ram</artifactId>
            <version>2.0.7</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>4.5.18</version>
        </dependency>
        ```

        **说明：** 请访问[Maven仓库](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)获取`aliyun-java-sdk-core`的最新版本。

-   方法二：手动下载并导入SDK的JAR文件

    无论您使用Eclipse还是IntelliJ作为集成开发环境，都可以通过手动下载并导入JAR文件的方式安装Java SDK。JAR文件下载地址如下：

    -   [阿里云Java SDK基础包](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)
    -   [RAM接口定义包（Java）](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-ram)

## Java SDK示例

下面为您提供[CreateUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateUser.md) API的Java SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com)调试并获取示例代码。

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
        
        //构建一个阿里云客户端, 用于发起请求。
        //构建阿里云客户端时需要设置AccessKey ID和AccessKey Secret。
        DefaultProfile profile = DefaultProfile.getProfile("<accessKeyId>", "<accessKeySecret>");
        IAcsClient client = new DefaultAcsClient(profile);
        
        //构建请求，设置参数。
        CreateUserRequest request = new CreateUserRequest();
        request.setUserName("<UserName>");
        
        //发起请求，并得到响应。
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

