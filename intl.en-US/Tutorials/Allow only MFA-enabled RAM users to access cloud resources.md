# Allow only MFA-enabled RAM users to access cloud resources

This topic describes how to allow only Resource Access Management \(RAM\) users that have multi-factor authentication \(MFA\) enabled to access Alibaba Cloud resources, such as Elastic Compute Service \(ECS\) instances.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   A RAM user is created. For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).
-   You have a basic knowledge of policy elements, structure, and syntax before you create a custom policy. For more information, see [Policy elements](/intl.en-US/Policy Management/Policy language/Policy elements.md) and [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

## Step 1: Enable MFA for a RAM user

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with the Alibaba Cloud account.

2.  In the left-side navigation pane, click **Users** under **Identities**.

3.  In the **User Logon Name/Display Name** column, click the name of the RAM user.

4.  On the **Authentication** tab, click **Enable the Virtual MFA Device**.

5.  On a mobile device, download and log on to the Google Authenticator app.

6.  On the mobile device, open the app and scan the QR code.

7.  Enter the two successive security codes that are obtained from the app and click **Enable**.


**Note:** For more information about how to use MFA, see [Enable an MFA device for a RAM user](/intl.en-US/Security Settings/Multi-factor authentication/Enable an MFA device for a RAM user.md).

## Step 2: Create a custom policy

1.  In the left-side navigation pane, click **Policies** under **Permissions**.

2.  On the Policies page, click **Create Policy**.

3.  On the Create Custom Policy page, set the **Policy Name** and **Note** parameters.

4.  In the **Configuration Mode** section, select **Script**.

5.  Copy and paste the following sample script to the Policy Document text box, and then edit the script based on your business requirements.

    ```
    {
        "Statement": [
            {
                "Action": "ecs:*",
                "Effect": "Allow",
                "Resource": "*",
                "Condition": {
                    "Bool": {
                        "acs:MFAPresent": "true"
                    }
                }
            }
        ],
        "Version": "1"
    }
    ```

    The policy indicates that only MFA-enabled RAM users can use the console to access ECS resources. This is because the value of the `acs:MFAPresent` key in the `Condition` element is `true`.

    You can modify the policy to limit the access from RAM users to other cloud resources based on your business requirements.

6.  Click **OK**.


## Step 3: Attach the policy to the RAM user

1.  In the left-side navigation pane, click **Users** under **Identities**.

2.  In the **User Logon Name/Display Name** column, find the RAM user.

3.  In the Actions column, click **Add Permissions**. In the Add Permissions pane, the Principal field is automatically filled in.

4.  In the **Authorization Policy Name** column, click the custom policy that you created in Step 2.

5.  Click **OK**.

6.  Click **Complete**.


