# Create an AccessKey pair for a RAM user

This topic describes how to create an AccessKey pair for a RAM user. An AccessKey pair is a long-term credential for a RAM user. A RAM user can use an AccessKey pair to access Alibaba Cloud resources by calling API operations or by using other development tools.

To ensure account security, we recommend that you create AccessKey pairs only for RAM users and do not create AccessKey pairs for your Alibaba Cloud account.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the username of the target RAM user.

4.  In the **User Access Key** section, click **Create Access Key**.

5.  Click **Close**.

    **Note:**

    -   The AccessKey secret is displayed only when you create an AccessKey pair, and is unavailable for subsequent queries. We recommend that you save the AccessKey secret for subsequent use.
    -   If the AccessKey pair is disclosed or lost, you must create a another AccessKey pair. You can create a maximum of two AccessKey pairs.

**Related topics**  


[CreateAccessKey](/intl.en-US/API Reference (RAM)/User management APIs/CreateAccessKey.md)

