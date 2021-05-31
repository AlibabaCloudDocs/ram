# 通过RAM对OSS进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对对象存储（OSS）进行权限管理，以满足RAM用户操作OSS的多种需求。

-   使用RAM对OSS进行权限管理前，请先了解以下系统策略：

    -   AliyunOSSFullAccess：管理OSS的权限。
    -   AliyunOSSReadOnlyAccess：只读访问OSS的权限。
    当系统策略不能满足您的需要时，您可以创建自定义策略。

-   使用RAM对OSS进行权限管理前，请先了解OSS的权限定义。更多信息，请参见[RAM Policy概述](/cn.zh-CN/开发指南/数据安全/访问控制/RAM Policy/RAM Policy概述.md)。

## 操作步骤

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/cn.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_mlc_ww2_vgb)。

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：授权RAM用户管理一个名为`myphotos`的存储空间。

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": "oss:*",
                "Resource": [
                    "acs:oss:*:*:myphotos",
                    "acs:oss:*:*:myphotos/*"
                ]
            }
        ]
    }
    ```

-   示例2：授权RAM用户列出并读取一个存储空间中的资源。
    -   授权RAM用户通过OSS SDK或OSS命令行工具列出并读取一个存储空间中的资源。存储空间名称为`myphotos`。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": "oss:ListObjects",
                    "Resource": "acs:oss:*:*:myphotos"
                },
                {
                    "Effect": "Allow",
                    "Action": "oss:GetObject",
                    "Resource": "acs:oss:*:*:myphotos/*"
                }
            ]
        }
        ```

    -   授权RAM用户能够通过OSS控制台进行操作。

        **说明：** 为了操作体验的优化，用户登录OSS控制台时，OSS控制台会额外调用`ListBuckets`、`GetBucketAcl`和`GetObjectAcl`，以确定存储空间属性是公开还是私有。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketTagging",
                              "oss:GetBucketAcl" 
                              ],    
                    "Resource": "acs:oss:*:*:*"
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetBucketAcl"
                    ],
                    "Resource": "acs:oss:*:*:myphotos"
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject",
                        "oss:GetObjectAcl"
                    ],
                    "Resource": "acs:oss:*:*:myphotos/*"
                }
            ]
        }
        ```

-   示例3：授权RAM用户通过特定的IP地址访问OSS。
    -   在`Allow`授权中增加IP限制：允许通过`192.168.0.0/16`, `172.12.0.0/16`两个IP地址段读取`myphotos`中的信息。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketTagging",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos",
                        "acs:oss:*:*:myphotos/*"
                    ],
                    "Condition":{
                        "IpAddress": {
                            "acs:SourceIp": ["192.168.0.0/16", "172.12.0.0/16"]
                        }
                    }
                }
            ]
        }
        ```

    -   在`Deny`授权中增加IP限制：如果源IP不在`192.168.0.0/16`中，则禁止对OSS执行任何操作。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketTagging",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos",
                        "acs:oss:*:*:myphotos/*"
                    ]
                },
                {
                    "Effect": "Deny",
                    "Action": "oss:*",
                    "Resource": [
                        "acs:oss:*:*:*"
                    ],
                    "Condition":{
                        "NotIpAddress": {
                            "acs:SourceIp": ["192.168.0.0/16"]
                        }
                    }
                }
            ]
        }
        ```

        **说明：** 因为权限策略的鉴权规则是Deny优先，所以访问者从`192.168.0.0/16`以外的IP地址访问`myphotos`中的内容时，OSS会提示没有权限。

-   示例4：OSS目录级别的授权。

    假设用于存放照片的存储空间名为`myphotos`，该存储空间下有一些目录，代表照片的拍摄地，每个拍摄地目录下又有年份子目录。

    ```
    myphotos[Bucket]
      ├── beijing
      │   ├── 2014
      │   └── 2015
      ├── hangzhou
      │   ├── 2013
      │   ├── 2014
      │   └── 2015 //授予该目录只读权限
      └── qingdao
          ├── 2014
          └── 2015
    ```

    若要授权RAM用户访问`myphotos/hangzhou/2015/`目录的只读权限。目录级别的授权属于授权的高级功能，根据使用场景不同，授权策略的复杂程度也不同，以下几种场景可供参考。

    -   场景1：授予RAM用户读取文件内容的权限，不需要列出文件的权限。

        RAM用户知道文件的完整路径，可以使用完整的文件路径直接去读取文件内容，通常会将这样的权限授予应用程序。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                }
            ]
        }
        ```

    -   场景2：授权RAM用户使用OSS命令行工具访问目录`myphotos/hangzhou/2015/`并列出目录中文件的权限。

        RAM用户不清楚目录中有哪些文件，可以使用OSS命令行工具或API直接获取目录信息，通常会将这样的权限授予软件开发者。

        此场景需要新增`ListObjects`的权限。

        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos"
                    ],
                    "Condition":{
                        "StringLike":{
                            "oss:Prefix":"hangzhou/2015/*"
                        }
                    }
                }
            ]
        }
        ```

    -   场景3： 授予RAM用户使用OSS控制台访问目录。

        RAM用户使用可视化的OSS客户端访问目录`myphotos/hangzhou/2015/`，可视化的客户端类似Windows文件管理器，RAM用户可以从根目录开始，一层一层的进入要访问的目录，此场景是最易用的场景。

        此场景需要新增以下权限：

        -   列出所有`Bucket`的权限。
        -   列出`myphotos`下目录的权限。
        -   列出`myphotos/hangzhou`下的目录的权限。
        ```
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketTagging",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject",
                        "oss:GetObjectAcl"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos"
                    ],
                    "Condition": {
                        "StringLike": {
                            "oss:Delimiter": "/",
                            "oss:Prefix": [
                                "",
                                "hangzhou/",
                                "hangzhou/2015/*"
                            ]
                        }
                    }
                }
            ]
        }
        ```


