# 设置 MFA（可选） {#concept_u2b_ww2_xdb .concept}

本文介绍了在 RAM 控制台开启 MFA（Multi-factor authentication，多因素认证）以及使用 MFA 进行登录的方法，帮助您使用 MFA 提高账号安全性。

## 为主账号开启多因素认证 {#section_gw3_xw2_xdb .section}

主账号对其名下的资源拥有完全控制权限，一旦云账号登录密码泄露，账号下的资产将面临极大的威胁。为了降低风险，我们强烈建议您给主账号绑定多因素认证。

**前提条件**

您需要在智能手机终端上安装虚拟 MFA 应用程序以完成下述操作，推荐您使用阿里云 App。

此外，常用的 MFA 应用程序还有 Google Authenticator，您可以自主选择安装使用。关于 Google Authenticator 安装问题，请参考[安卓版Google Authenticator安装及使用指导](../../../../intl.zh-CN/用户指南/Google Authenticator 安装及使用指导/安卓版Google Authenticator安装及使用指导.md)。

下文以 阿里云 App 为例来描述操作步骤，使用其他 MFA 应用程序的步骤与此类似。

**操作步骤**

1.  使用阿里云主账号登录到账号管理下 [安全设置](https://account.console.aliyun.com/#/secure) 页面。
2.  在虚拟MFA 菜单下，点击**设置** 进入启用虚拟 MFA 设备绑定流程。
3.  通过邮箱验证、手机验证或密保问题完成身份验证，进入启用虚拟MFA设备页面，如下图所示。

     ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12338/3500_zh-CN.png "身份验证") 

4.  在手机中打开**阿里云 App**，选择**+** \> **扫码添加**进行扫码。扫码完成后会自动添加用户，阿里云 App 会显示您当前账号的动态口令，每30秒更新一次。

     ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12338/3501_zh-CN.png "动态口令") 

    **说明：** 如果您的智能设备不支持扫码功能，那么您也可以选择**手输信息获取**，在 MFA 应用程序中以手动输入 MFA 密钥的方式进行配置。

5.  在启用虚拟MFA设备 页面中输入 MFA 应用中显示的连续两组动态口令，然后单击**确定启用**。如下图所示：

     ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12338/3503_zh-CN.png "启用虚拟MFA设备") 


至此，您已成功启用 MFA 设备。

## 开启 MFA 后的登录过程 {#section_nw3_xw2_xdb .section}

在开启 MFA 后，只有完成两步验证后，您才能登录到阿里云。操作步骤如下：

1.  登录控制台时先输入登录用户名和密码。
2.  校验密码成功后，还需您提供虚拟 MFA 设备的动态安全验证码，如下图所示：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12338/3503_zh-CN.png "验证动态安全验证码")


在您的手机阿里云 App 应用中，获取并输入登录账号的动态验证码，即可正常登录到阿里云。

