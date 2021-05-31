# 通过RAM对操作审计进行权限管理

通过RAM的权限管理功能，您可以创建自定义权限策略并授予RAM用户，RAM用户便可以登录操作审计服务进行相应的操作。

-   使用RAM对操作审计进行权限管理前，请先了解以下系统策略：

    -   AliyunActionTrailFullAccess：管理操作审计的权限。
    -   AliyunActionTrailReadOnlyAccess：只读访问操作审计的权限。
    当系统策略不能满足您的需求时，您可以创建自定义策略。

-   使用RAM对操作审计进行授权前，请先了解操作审计的权限定义。更多信息，请参见[RAM鉴权](/intl.zh-CN/API参考/API参考（2017-12-04）（不推荐）/RAM鉴权.md)。

## 操作步骤

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/intl.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_xqm_lnm_xgb)。

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/intl.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：授予RAM用户只读权限。

    ```
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*"
        }]
    }
                        
    ```

-   示例2：仅允许RAM用户从指定的IP地址发起只读操作。

    ```
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*",
            "Condition":{
                "IpAddress": {
                    "acs:SourceIp": "42.120.XX.X/24"
                }
            }
        }]
    }
    ```


