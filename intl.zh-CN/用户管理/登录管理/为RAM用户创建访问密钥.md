# 为RAM用户创建访问密钥

访问密钥（AccessKey）是RAM用户的长期凭证。如果为RAM用户创建了访问密钥，RAM用户可以通过API或其他开发工具访问阿里云资源。

为保证账号安全，强烈建议您给RAM用户创建访问密钥，不要给阿里云账号（主账号）创建访问密钥。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，选择**人员管理** \> **用户**。

3.  在用户页面，单击目标RAM用户名称。

4.  在**用户AccessKey**区域，单击**创建AccessKey**。

5.  在创建AccessKey对话框，查看AccessKey ID和AccessKey Secret。

    您可以单击**下载CSV文件**，下载AccessKey信息。或者单击**复制**，复制AccessKey信息。

6.  单击**关闭**。

    **说明：**

    -   AccessKey Secret只在创建时显示，不支持查询，请妥善保管。
    -   若AccessKey泄露或丢失，则需要创建新的AccessKey，最多可以创建2个AccessKey。

**相关文档**  


[CreateAccessKey](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateAccessKey.md)

