# Create an AccessKey pair for a RAM user

This topic describes how to create an AccessKey pair for a Resource Access Management \(RAM\) user. An AccessKey pair is a long-term credential for a RAM user. A RAM user can use an AccessKey pair to access Alibaba Cloud resources by calling API operations or by using other development tools.

To ensure account security, we recommend that you create AccessKey pairs for RAM users instead of your Alibaba Cloud account.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, find the specific RAM user and click its name.

4.  In the **User AccessKeys** section, click **Create AccessKey**.

5.  In the Create AccessKey dialog box, view the AccessKey ID and AccessKey secret.

    You can click **Download CSV File** to download the AccessKey pair or click **Copy** to copy the AccessKey pair.

6.  Click **Close**.

    **Note:**

    -   The AccessKey secret is displayed only when you create an AccessKey pair, and is unavailable for subsequent queries. We recommend that you save the AccessKey secret for subsequent use.
    -   If the AccessKey pair is disclosed or lost, you must create another AccessKey pair. You can create a maximum of two AccessKey pairs

**Related topics**  


[CreateAccessKey](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/CreateAccessKey.md)

