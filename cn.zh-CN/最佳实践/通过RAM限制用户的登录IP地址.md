# 通过RAM限制用户的登录IP地址 {#task_1614402 .task}

RAM可以限制用户只能通过指定的IP地址访问企业的云资源，从而增强访问安全性。

-   请确保您已经注册了阿里云账号。如还未注册，请先完成账号注册。详情请参见[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。
-   请确保您已经开通RAM服务并登录[RAM控制台](https://ram.console.aliyun.com/)。如还未开通，请先开通RAM服务。详情请参见[开通方法](../../../../intl.zh-CN/产品定价/开通方法.md#)。
-   创建自定义策略前，需要先了解权限策略语言的基本结构和语法。详情请参见[权限策略基本元素](../../../../intl.zh-CN/用户指南/权限策略/权限策略语言/权限策略基本元素.md#)和[权限策略语法和结构](../../../../intl.zh-CN/用户指南/权限策略/权限策略语言/权限策略语法和结构.md#)。

企业A购买了很多阿里云资源来开展业务，例如：ECS实例、RDS实例、SLB实例和OSS存储空间等。为了确保其业务和数据安全，企业希望RAM用户只能通过企业专用网络的IP地址访问阿里云，而不是在任意地点都可以访问阿里云。

## 解决方案 {#section_7fb_2lv_k12 .section}

您可以根据需要创建自定义策略并为RAM用户添加相应的权限，从而保证RAM用户只能通过指定的IP地址访问阿里云。

1.  [创建RAM用户](../../../../intl.zh-CN/用户指南/用户/创建 RAM 用户.md#)。
2.  [创建自定义策略](#section_9ti_0x8_228)。
3.  [为RAM用户授权](../../../../intl.zh-CN/用户指南/用户/为 RAM 用户授权.md#)。

## 创建自定义策略 {#section_9ti_0x8_228 .section}

1.  在左侧导航栏的**权限管理**菜单下，单击**权限策略管理**。
2.  单击**新建权限策略**。
3.  填写**策略名称**和**备注**。
4.  **配置模式**选择**脚本配置**，拷贝下述策略示例到[策略内容](https://ram.console.aliyun.com/policies/new)区域下并根据实际情况进行修改。 

    ![限制用户登录IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1280070/156689736254965_zh-CN.png)

    下述策略表示：RAM用户只能通过192.168.0.0/16这个IP地址访问ECS。您可以通过设置`Condition`下`acs:SourceIp`的值为`192.168.0.0/16`来实现。

    ``` {#codeblock_3ci_blk_288 .lanuage-xml}
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
            "IpAddress": {
              "acs:SourceIp": "192.168.0.0/16"
            }
          }
        }
      ],
      "Version": "1"
    }
    ```

    **说明：** `Condition`（限制条件）只针对当前权限策略描述的操作有效。您可以修改IP：`192.168.0.0/16`为企业的专用网络IP地址。

5.  单击**确认**。

