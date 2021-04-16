# 通过SCIM协议将企业内部账号同步到阿里云RAM

企业上云的过程中，为减少维护和管理成本，需要基于一套原则将企业内部系统中已有的账号同步到云上。阿里云通过SCIM标准协议，结合OAuth应用的安全授权，可以将企业内部系统中的账号数据同步到阿里云访问控制（RAM）中。

-   您的阿里云账号或RAM用户有创建OAuth应用的权限。
-   您的阿里云账号或RAM用户有为ServerApp授权的权限，且您仅能给自己账号下的ServerApp授权。

-   SCIM（System for Cross-domain Identity Management）主要用于多用户的云应用身份管理。SCIM 2.0建立在一个对象模型上，所有SCIM对象都继承Resource。Resource具有id、externalId和meta属性，RFC7643定义了扩展公共属性的User、Group和EnterpriseUser。本文的示例将采用User来同步用户信息。更多关于SCIM的信息，请参见[SCIM](http://www.simplecloud.info/#Overview)。
-   开放授权OAuth（Open Authorization）是为用户资源的授权定义了一个安全、开放及简单的标准，第三方无需知道用户的账号和密码，就可获取到用户的授权信息。阿里云当前的OAuth授权形态分为**WebApp**、**NativeApp**和**ServerApp**三种。**WebApp**和**NativeApp**都属于3-legged OAuth，而**ServerApp**属于2-legged OAuth。SCIM主要使用2-legged OAuth机制来完成应用程序（消费者）和API（服务提供商）之间的授权，从而进行下一步的数据同步业务。更多关于OAuth的信息，请参见[OAuth 2.0](https://tools.ietf.org/html/rfc6749)和[OAuth应用概览](/cn.zh-CN/开放授权管理（OAuth）/OAuth应用概览.md)。
-   阿里云SCIM Endpoint：`https://scim.aliyun.com`。
-   阿里云OAuth获取access\_token的Endpoint：`https://oauth.aliyun.com/v1/token`。

## 步骤1：创建OAuth应用并授权

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  选择**OAuth应用管理** \> **创建应用**，创建OAuth应用。

    其中，**应用类型**选择**ServerApp**。

    ![创建OAuth应用](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5804778851/p98016.png)

3.  单击应用名称，然后在**应用OAuth范围**页签下单击**添加OAuth范围**。

    其中，**OAuth范围**选择**/acs/scim**。

    ![添加OAuth范围](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5804778851/p98017.png)

4.  在**应用OAuth范围**页签，先单击**去授权**，然后单击**管理员授权**。

    ![123](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5804778851/p98025.png)

5.  在**应用密钥**页签，单击**创建密钥**。

    ![创建密钥](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5804778851/p98034.png)

    **说明：**

    -   密钥仅在创建时可见，请您注意保存。
    -   **AppSecretId**是密钥的ID，不是密钥（client\_secret）内容。

## 步骤2：同步账号数据

支持通过客户端（例如：One Identity）或SCIM API两种方式同步账号数据。

-   客户端：您可以在客户端（One Identity）中配置SCIM信息，然后通过One Identity同步账号数据。One Identity配置方法，请参见[Setting up Synchronization with a Cloud Application](https://support.oneidentity.com/technical-documents/identity-manager/8.0/administration-guide-for-connecting-to-cloud-applications#TOPIC-852179)。
-   SCIM API：您可以通过SCIM API将企业内部系统中的账号映射成RAM用户，进行创建、删除、查询和修改操作。支持对RAM用户的如下字段进行操作：
    -   `id`：RAM用户ID，全局唯一，服务端生成。
    -   `externalId`：RAM用户外键，用户级别唯一，客户端指定，用于将阿里云的RAM用户和企业内部系统中的用户关联。

        **说明：** 通过控制台创建的RAM用户无`externalId`字段。

    -   `userName`：RAM用户名称，用户级别唯一，客户端指定。
    -   `displayName`：RAM用户显示名称，客户端指定。

通过阿里云SCIM API同步账号数据的操作如下所示。

1.  获取已授权的ServerApp的ID（client\_id）和密钥（client\_secret）。

    -   client\_id：在RAM控制台的**企业应用**页签，查看ServerApp的ID（client\_id）。

        ![client_id](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5804778851/p98032.png)

    -   client\_secret：在RAM控制台，创建密钥时保存的密钥。
2.  通过`client_id`和`client_secret`访问`https://oauth.aliyun.com/v1/token`，获取`access_token`。

    其中，请求头中的Authorization内容为`"Authorization: Basic Base64Encode(client_id:client_secret)"`，例如：cliet\_id=cid，client\_secret=123456，那么请求头中需要输入的Authorization内容为`"Authorization: Basic Y2lkOjEyMzQ1Ng=="`。

    请求示例：

    ```
    curl --location --request POST --header "Authorization: Basic Y2lkOjEyMzQ1Ng==" https://oauth.aliyun.com/v1/token?grant_type=client_credentials&client_id=463790568674183****
    ```

    返回示例：

    ```
    {
        "scope": "/acs/scim",
        "request_id": "8dc768e0-d6fe-4f52-a788-05631dd6c584",
        "access_token": "eyJ***hKg",
        "token_type": "Bearer",
        "expires_in": "3599"
    }
    ```

3.  查询阿里云SCIM支持的`ResourceType`和`Schema`。

    查询SCIM支持的`ResourceType`：

    ```
    curl --location --request GET 'https://scim.aliyun.com/ResourceTypes'
    ```

    查询SCIM支持的`Schema`：

    ```
    curl --location --request GET 'https://scim.aliyun.com/Schemas'
    ```

4.  创建、查询、修改和删除RAM用户。

    -   创建RAM用户。

        根据企业内部系统中的账号信息，指定与之对应的RAM用户名称（userName）、显示名称（displayName）和外键（externalId），然后创建RAM用户。

        请求示例：

        ```
        curl --location --request POST 'https://scim.aliyun.com/Users' \
        --header 'Authorization: Bearer  eyJ***hKg' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "displayName": "j2gg0s_****",
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:User"
            ],
            "externalId": "6e74eec4-ddb5-4e74-bd12-5e7b99b2****",
            "userName": "j2gg0screatedbyscim_exa****"
        }'
        ```

        返回示例：

        ```
        {
            "displayName": "j2gg0s_****",
            "meta": {
                "created": "2020-02-14T03:58:59Z",
                "location": "https://scim.aliyun.com/Users/27648498165273****",
                "lastModified": "2020-02-14T03:58:59Z",
                "resourceType": "User"
            },
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:User"
            ],
            "externalId": "6e74eec4-ddb5-4e74-bd12-5e7b99b2****",
            "id": "27648498165273****",
            "userName": "j2gg0screatedbyscim_exa****"
        }
        ```

    -   查询指定的RAM用户。
        -   通过`GET /Users/{id}`，查询指定`id`的RAM用户。
        -   通过`GET /Users?filter=externalId eq xxx`，查询指定`externalId`的RAM用户。
        -   通过`GET /Users?filter=userName eq xxx`，查询指定`userName`的RAM用户。请求示例和响应示例如下。

            请求示例：

            ```
            curl --location --request GET 'https://scim.aliyun.com/Users?filter=userName%20eq%20%22j2gg0screatedbyscim****%22' \
            --header 'Authorization: Bearer  eyJ***hKg'
            ```

            返回示例：

            ```
            {
                "startIndex": 1,
                "totalResults": 1,
                "itemsPerPage": 30,
                "schemas": [
                    "urn:ietf:params:scim:api:messages:2.0:ListResponse"
                ],
                "Resources": [
                    {
                        "displayName": "j2gg0screatedbyscim****",
                        "meta": {
                            "created": "2019-12-11T01:53:19Z",
                            "location": "https://scim.aliyun.com/Users/27769827602919****",
                            "lastModified": "2019-12-11T02:10:39Z",
                            "resourceType": "User"
                        },
                        "schemas": [
                            "urn:ietf:params:scim:schemas:core:2.0:User"
                        ],
                        "externalId": "6e74eec4-ddb5-4e74-bd12-5e7b99b2****",
                        "id": "27769827602919****",
                        "userName": "j2gg0screatedbyscim****"
                    }
                ]
            }
            ```

            **说明：** 对于SCIM Filter，阿里云仅支持对`id`、`userName`和`externalId`进行and和eq操作。

    -   修改RAM用户属性。

        请求示例：

        ```
        curl --location --request PUT 'https://scim.aliyun.com/Users/27648498165273****' \
        --header 'Authorization: Bearer  eyJ***hKg' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "displayName": "j2gg0s_new_****",
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:User"
            ],
            "externalId": "6e74eec4-ddb5-4e74-bd12-5e7b99b2****",
            "userName": "j2gg0screatedbyscim_new_exa****"
        }'
        ```

        返回示例：

        ```
        {
            "displayName": "j2gg0s_new_****",
            "meta": {
                "created": "2020-02-14T03:58:59Z",
                "location": "https://scim.aliyun.com/Users/27648498165273****",
                "lastModified": "2020-02-14T04:03:55Z",
                "resourceType": "User"
            },
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:User"
            ],
            "externalId": "6e74eec4-ddb5-4e74-bd12-5e7b99b2****",
            "id": "27648498165273****",
            "userName": "j2gg0screatedbyscim_new_exa****"}
        ```

    -   删除RAM用户。

        请求示例：

        ```
        curl --location --request DELETE 'https://scim.aliyun.com/Users/27648498165273****' \
        --header 'Authorization: Bearer  eyJ***hKg' \
        --header 'Content-Type: application/json'
        ```

        返回的HTTP状态码为204时，表示删除RAM用户成功。

        **说明：**

        -   如果RAM用户有关联的AccessKey、RAM Policy等，考虑到安全因素，不支持通过SCIM API直接删除RAM用户。
        -   阿里云暂时不支持软删除。如果您的系统支持软删除，建议先将软删除映射成硬删除，再同步到阿里云。

