# Obtain an AccessKey pair

This topic describes how to create and obtain an AccessKey pair for an Alibaba Cloud account or a Resource Access Management \(RAM\) user. When you call an API operation, you must use the AccessKey pair to verify your identity.

An AccessKey pair consists of an AccessKey ID and an AccessKey secret.

-   The AccessKey ID is used to verify the identity of the user.
-   The AccessKey secret is used to encrypt and verify the signature string. You must keep your AccessKey secret strictly confidential.

**Warning:** If the AccessKey pair of your Alibaba Cloud account is disclosed, your resources are exposed to potential risks. We recommend that you use a RAM user to call API operations. This minimizes the possibility of disclosing the AccessKey pair of your Alibaba Cloud account.

1.  Use an Alibaba Cloud account to log on to the [Alibaba Cloud Management Console](https://home-intl.console.aliyun.com/).

2.  Move the pointer over the profile picture in the upper-right corner of the page and click **AccessKey Management**.

3.  In the **Note** dialog box, click **Use Current AccessKey Pair** or **Use AccessKey Pair of RAM User**.

    ![Note dialog box](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48002.png)

    -   Obtain the AccessKey pair of an Alibaba Cloud account
        1.  Click **Use Current AccessKey Pair**.
        2.  On the AccessKey Management page, click **Create AccessKey**.
        3.  In the Create AccessKey dialog box, view the AccessKey ID and AccessKey secret. You can click **Download CSV File** to download the AccessKey pair or click **Copy** to copy the AccessKey pair.

            ![Create an AccessKey pair](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48003.png)

    -   Obtain the AccessKey pair of a RAM user
        1.  Click **Use AccessKey Pair of RAM User**.
        2.  On the Users page of the [RAM console](https://ram.console.aliyun.com/users/new), find the RAM user whose AccessKey pair you want to obtain.

            **Note:** If you do not have a RAM user, create one first. For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

        3.  Click the name of the RAM user in the User Logon Name/Display Name column.
        4.  In the User AccessKeys section of the Authentication tab, click **Create AccessKey**.
        5.  In the Create AccessKey dialog box, view the AccessKey ID and AccessKey secret. You can click **Download CSV File** to download the AccessKey pair or click **Copy** to copy the AccessKey pair.

            ![Create AccessKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48004.png)

            **Note:**

            -   The AccessKey secret is displayed only when you create an AccessKey pair and cannot be queried in the future. You must keep your AccessKey secret confidential.
            -   If your AccessKey pair is disclosed or lost, you must create another AccessKey pair. However, you can create a maximum of two AccessKey pairs for each RAM user.

