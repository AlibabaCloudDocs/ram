# Use RAM to limit the period of time in which users are allowed to access Alibaba Cloud resources

This topic describes how to use Resource Access Management \(RAM\) to limit the period of time in which users are allowed to access Alibaba Cloud resources. This ensures a higher level of data security.

You have a basic knowledge of policy elements, structure, and syntax before you create a custom policy. For more information, see [Policy elements](/intl.en-US/Policy Management/Policy language/Policy elements.md) and [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

An enterprise has purchased multiple types of Alibaba Cloud resources. The resources include Elastic Compute Service \(ECS\) instances, ApsaraDB RDS instances, Server Load Balancer \(SLB\) instances, and Object Storage Service \(OSS\) buckets. To ensure business and data security, the enterprise requires users to access Alibaba Cloud resources only during working hours.

To allow a RAM user to access Alibaba Cloud resources only during a specific period of time, create a custom policy and attach the policy to the RAM user.

## Step 1: Create a custom policy

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Permissions** \> **Policies**.

3.  On the Policies page, click **Create Policy**.

4.  On the Create Custom Policy page, specify the **Policy Name** and **Note** parameters.

5.  Set **Configuration Mode** to **Script** and enter the following information.

    The following policy indicates that the authorized RAM user can access Alibaba Cloud ECS only before 17:00 on August 12, 2019 \(UTC+8\). In this case, the `acs:CurrentTime` parameter in `Condition` is set to `2019-08-12T17:00:00+08:00`.

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
              "DateLessThan": {
                  "acs:CurrentTime": "2019-08-12T17:00:00+08:00"
              }
          }
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** The `Condition` element applies only to the actions specified for the current policy. You can change the value `2019-08-12T17:00:00+08:00` based on your business requirements.

6.  Click **OK**.


## Step 2: Create a RAM user

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, click **Create User**.

4.  On the Create User page, specify **Logon Name** and **Display Name** in the **User Account Information** section.

    **Note:** You can click **Add User** to create multiple RAM users at a time.

5.  In the **Access Mode** section, select Console Access or Programmatic Access.

    -   **Console Access**: If you select this access mode, you must complete the logon security settings. These settings specify whether to use a system-generated or custom logon password, whether the password must be reset on the next logon, and whether to enable multi-factor authentication \(MFA\).

        **Note:** If you select Custom Logon Password in the Console Password section, you must specify a password. The password must meet the complexity requirements. For more information about the complexity requirements, see [Configure the password policy for RAM users](/intl.en-US/Security Settings/Passwords/Configure the password policy for RAM users.md).

    -   **Programmatic Access**: If you select this access mode, an AccessKey pair is automatically created for the RAM user. The RAM user can call API operations or use other development tools to access Alibaba Cloud resources.
    **Note:** We recommend that you select only one access mode for the RAM user to ensure the security of your Alibaba Cloud account. This prevents the RAM user from using an AccessKey pair to access Alibaba Cloud resources after the RAM user leaves the organization.

6.  Click **OK**.


## Step 3: Attach the policy to the RAM user

Attach the policy that is created in [Step 1](#section_ar7_odt_vzq) to the RAM user that is created in [Step 2](#section_2um_0fm_46h).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, find the RAM user to which you want to grant permissions. Click **Add Permissions** in the **Actions** column.

4.  In the Add Permissions panel, grant permissions to the RAM user.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM user to which permissions are granted. By default, the current RAM user is specified. You can also specify another RAM user.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


