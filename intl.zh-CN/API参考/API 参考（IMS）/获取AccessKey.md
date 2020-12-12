# 获取AccessKey

您可以为阿里云账号（主账号）和RAM用户创建一个访问密钥（AccessKey）。在调用阿里云API时您需要使用AccessKey完成身份验证。

AccessKey包括AccessKey ID和AccessKey Secret。

-   AccessKey ID：用于标识用户。
-   AccessKey Secret：用于验证用户的密钥。AccessKey Secret必须保密。

**警告：** 阿里云账号AccessKey泄露会威胁您所有资源的安全。建议您使用RAM用户AccessKey进行操作，可以有效降低AccessKey泄露的风险。

1.  使用阿里云账号登录[控制台](https://home-intl.console.aliyun.com/)。

2.  将鼠标置于页面右上方的账号图标，单击**AccessKey管理**。

3.  在**安全提示**对话框，选择使用阿里云账号AccessKey或RAM用户AccessKey。

    ![安全提示](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3675425061/p48002.png)

    -   使用阿里云账号AccessKey
        1.  单击**继续使用AccessKey**。
        2.  在AccessKey管理页面，单击**创建AccessKey**。
        3.  在创建AccessKey对话框，查看AccessKey ID和AccessKey Secret。可以单击**下载CSV文件**，下载AccessKey信息。或者单击**复制**，复制AccessKey信息。

            ![新建用户AccessKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8947359951/p48003.png)

    -   使用RAM用户AccessKey
        1.  单击**开始使用子用户AccessKey**。
        2.  系统自动跳转到[RAM控制台](https://ram.console.aliyun.com/users/new)的用户页面，找到需要获取AccessKey的RAM用户。

            **说明：** 如果没有RAM用户，请先创建RAM用户，详情请参见[创建RAM用户](/intl.zh-CN/用户管理/创建RAM用户.md)。

        3.  单击用户登录名称。
        4.  在认证管理页签下的用户AccessKey区域，单击**创建AccessKey**。
        5.  在创建AccessKey页面，查看AccessKey ID和AccessKey Secret。可以单击**下载CSV文件**，下载AccessKey信息。或者单击**复制**，复制AccessKey信息。

            ![创建AccessKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7037906061/p48004.png)

            **说明：**

            -   RAM用户的AccessKey Secret只在创建时显示，不提供查询，请妥善保管。
            -   若AccessKey泄露或丢失，则需要创建新的AccessKey，最多允许为每个RAM用户创建2个AccessKey。

