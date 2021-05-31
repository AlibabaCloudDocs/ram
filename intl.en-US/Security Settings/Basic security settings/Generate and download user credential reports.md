# Generate and download user credential reports

A user credential report contains the details of your Alibaba Cloud account and Resource Access Management \(RAM\) users. The details include logon passwords, AccessKey pairs, and multi-factor authentication \(MFA\) devices. User credential reports can be generated and downloaded in the RAM console. You can use the user credential reports for compliance checks and auditing.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using an Alibaba Cloud account. You can also log on as a RAM user that is attached with the AliyunRAMFullAccess policy.

2.  In the left-side navigation pane, click **Overview**.

3.  In the **Security Check** section of the page that appears, click **Download User Credential Report**.

4.  After the user credential report is generated, click **Download**.

    **Note:** The time period required to generate the user credential report is affected by the number of RAM users within the current Alibaba Cloud account. If a long period of time is required to generate the report, you can click **Download Later**. A new user credential report in the CSV format can only be generated every four hours. When you send a request to download a report, RAM first checks whether a report has been generated within the last four hours. If the latest report is generated within the last four hours, the latest report is downloaded. If the latest report is generated four hours or more earlier, or if no previous report has been generated, RAM generates a new report.


The following table describes the fields that are included in the user credential report.

|Field|Example|Description|
|-----|-------|-----------|
|user|username@company-alias.onaliyun.com|The usernames of the Alibaba Cloud account and the RAM users. The value in the first row of the CSV file is <root\>, which indicates the Alibaba Cloud account. The values in the remaining rows are the usernames of the RAM users within your Alibaba Cloud account, and the values are in the User Principal Name \(UPN\) format.|
|user\_creation\_time|2019-11-11T12:33:18Z|The time at which the RAM users were created. **Note:** The time follows the ISO 8601 standard in the YYYY-MM-DDThh:mm:ssZ format. The time is displayed in UTC. |
|user\_last\_logon|2019-11-11T12:45:18Z|The time at which the RAM users last logged on to the RAM console. **Note:** The RAM users may log on to the RAM console by using passwords or single sign-on \(SSO\). If a RAM user has never logged on to the RAM console, the value of this field is a hyphen \(`-`\). |
|password\_exist|TRUE|Indicates whether a password for logging on to the RAM console is available. Valid values: `TRUE` and `FALSE`. -   The value for a RAM user is determined by the logon configurations of the RAM user.
-   The value for an Alibaba Cloud account is `TRUE` and cannot be changed.

**Note:** If you use a resource account that is created on the Resource Directory page of the Resource Management console, you can view the password. However, the password cannot be used to log on to the RAM console. |
|password\_active|N/A|Indicates whether a password is active. Valid values: `TRUE`, `FALSE`, and `N/A`. -   If the logon configurations for a RAM user are unavailable, the value for the RAM user is `N/A`.
-   The value for an Alibaba Cloud account is `N/A`. |
|password\_last\_changed|2019-11-11T12:50:18Z|The time at which a password is last changed. If the logon configurations for a RAM user are unavailable, the value for the RAM user is `N/A`. **Note:** RAM records the changes that were made after April 5, 2016. If a password was changed on this date or earlier, the value for this field is `N/A`. The user credential report may not include the changes that were made in an interval leading up to the report generation time. The interval is about 24 hours, but the actual time may vary based on the scenario. |
|password\_next\_rotation|2019-11-13T12:50:18Z|The time at which a new password must be configured in compliance with the password rotation policy. -   If the password is permanently valid and password rotation is not required, the value is a hyphen \(`-`\).
-   If the logon configurations for a RAM user are unavailable, the value for the RAM user is `N/A`.
-   The value for an Alibaba Cloud account is `N/A`. |
|mfa\_active|TRUE|Indicates whether an MFA device is enabled. Valid values: `TRUE`, `FALSE`, and `N/A`. If the logon configurations for a RAM user are unavailable, the value for the RAM user is `N/A`.|
|access\_key\_1\_exist|TRUE|Indicates whether the first AccessKey pair exists. Valid values: `TRUE` and `FALSE`.|
|access\_key\_1\_active|TRUE|Indicates whether the first AccessKey pair is active. Valid values: `TRUE`, `FALSE`, and `N/A`. If no AccessKey pairs are created, the value is `N/A`.|
|access\_key\_1\_last\_rotated|2019-11-11T12:50:18Z|The time at which the first AccessKey pair is created or last changed. If no AccessKey pairs are created, the value is `N/A`.|
|access\_key\_1\_last\_used|2019-11-13T12:50:18Z|The time at which the first AccessKey pair is last used. -   If the AccessKey pair is not used since RAM started to track the AccessKey pair from the last usage, the value is a hyphen \(`-`\).
-   If no AccessKey pairs are created, the value is `N/A`.

**Note:** RAM started to track the last usage time of AccessKey pairs from June 1, 2019. The user credential report may not include the usage records of the AccessKey pairs in an interval leading up to the report generation time. The interval is about two hours, but the actual time may vary based on the scenario. |
|access\_key\_2\_exist|TRUE|Indicates whether the second AccessKey pair exists. Valid values: `TRUE` and `FALSE`.|
|access\_key\_2\_active|TRUE|Indicates whether the second AccessKey pair is active. Valid values: `TRUE`, `FALSE`, and `N/A`. If no AccessKey pairs are created, the value is `N/A`.|
|access\_key\_2\_last\_rotated|2019-11-11T12:50:18Z|The time at which the second AccessKey pair is created or last changed. If no AccessKey pairs are created, the value is `N/A`.|
|access\_key\_2\_last\_used|2019-11-13T12:50:18Z|The time at which the second AccessKey pair was last used. -   If the AccessKey pair is not used since RAM started to track the AccessKey pair from the last usage, the value is a hyphen \(`-`\).
-   If no AccessKey pairs are created, the value is `N/A`.

**Note:** RAM started to track the last usage time of AccessKey pairs from June 1, 2019. The user credential report may not include the usage records of the AccessKey pairs in an interval leading up to the report generation time. The interval is about two hours, but the actual time may vary based on the scenario. |

**Note:** A maximum of two AccessKey pairs can be created for each Alibaba Cloud account or RAM user in the RAM console. Before this limit takes effect, more than two AccessKey pairs can be created. Therefore, an Alibaba Cloud account or a RAM user may have more than two AccessKey pairs. The information about the additional AccessKey pairs is listed in the last columns of the CSV file. The names of these columns start with `additional_access_key_`.

