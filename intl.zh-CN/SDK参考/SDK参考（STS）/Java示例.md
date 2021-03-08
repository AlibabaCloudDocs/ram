# Java示例

本文简要介绍了Java SDK的安装方法，并提供了示例代码。

## 背景信息

-   Java SDK包含阿里云Java SDK核心库（`aliyun-java-sdk-core`）和STS SDK（`aliyun-java-sdk-sts`），两者都需要安装。
-   [OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于STS API的详情，请参见[什么是STS](/intl.zh-CN/API参考/API 参考（STS）/什么是STS.md)。
-   关于STS的接入地址，请参见[接入地址](/intl.zh-CN/API参考/API 参考（STS）/接入地址.md)。

## Java SDK的安装方法

您可以通过下面两种方法安装Java SDK。具体的安装方法，请参见[快速开始]()。

-   方法一：添加Maven依赖（推荐）
    1.  使用Maven创建项目：

        ```
        mvn archetype:generate -DgroupId=com.aliyun.sts.sample \
        -DartifactId=sts-sdk-sample \
        -Dpackage=com.aliyun.sts.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  在项目的pom.xml文件中加入如下依赖项：

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

        **说明：** 请访问[Maven仓库](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)获取`aliyun-java-sdk-core`的最新版本。

-   方法二：手动下载并导入SDK的JAR文件

    无论您使用Eclipse还是IntelliJ作为集成开发环境，都可以通过手动下载并导入JAR文件的方式安装Java SDK。JAR文件下载地址如下：

    -   [Java SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-core)
    -   [STS SDK](https://mvnrepository.com/artifact/com.aliyun/aliyun-java-sdk-sts)

## Java SDK示例

下面为您提供[AssumeRole](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md) API的Java SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)调试并获取示例代码。

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
        //构建一个阿里云客户端，用于发起请求。
        //构建阿里云客户端时需要设置AccessKey ID和AccessKey Secret。
        DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);

        //构造请求，设置参数。关于参数含义和设置方法，请参见API参考。
        AssumeRoleRequest request = new AssumeRoleRequest();
        request.setRegionId("cn-hangzhou");
        request.setRoleArn("<RoleArn>");
        request.setRoleSessionName("<RoleSessionName>");
        
        //发起请求，并得到响应。
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

