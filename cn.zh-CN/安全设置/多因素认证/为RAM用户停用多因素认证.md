# 为RAM用户停用多因素认证

如果您不再需要为RAM用户启用多因素认证设备或需要更换多因素认证设备时，可以使用阿里云账号或RAM管理员为RAM用户停用多因素认证设备。

1.  阿里云账号或RAM管理员登录[RAM控制台](https://ram.console.aliyun.com/)。

    **说明：** 如果阿里云账号允许RAM用户自主管理多因素认证设备，RAM用户也可以登录控制台停用MFA。将鼠标悬停在右上角头像的位置，单击**安全信息管理**，在 **虚拟MFA**页签单击**停用虚拟MFA设备**，或在**U2F安全密钥**页签单击**停用U2F安全密钥**。

2.  在左侧导航栏，选择**人员管理** \> **用户**。

3.  在RAM用户列表中，单击目标RAM用户名称。

4.  单击**认证管理**页签，停用虚拟MFA或U2F安全密钥。

    -   单击**虚拟MFA**页签，然后单击**停用虚拟MFA设备**，停用虚拟MFA认证。
    -   单击**U2F安全密钥**页签，然后单击**停用U2F安全密钥**，停用U2F安全密钥认证。
5.  单击**确定**。


**相关文档**  


[UnbindMFADevice](/cn.zh-CN/API参考/API参考（RAM）/用户管理接口/UnbindMFADevice.md)

