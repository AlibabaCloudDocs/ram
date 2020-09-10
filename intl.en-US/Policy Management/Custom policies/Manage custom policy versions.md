# Manage custom policy versions

This topic describes how to manage custom policy versions, including how to view a policy version, specify the default policy version, and delete a policy version.

RAM allows you to manage the versions of custom policies.

-   A custom policy has a maximum of five versions.
-   If you modify a custom policy and the policy already has five versions, the earliest version that is not in use is deleted and a version is created. You can also delete the versions that you no longer need.
-   If a policy has more than one version, only the default version is active.
-   The default version can be viewed but cannot be deleted.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  In the left-side navigation pane, click **Policies** under **Permissions**.

3.  In the **Policy Name** column on the Policies page, click the name of the policy that you want to manage.

4.  On the page that appears, click the **Versions** tab. On this tab, you can view, specify, and delete policy versions.

    -   To view a policy version and its document, click **View** in the Actions column.
    -   To specify a policy version as the default version, click **Use This Version** in the **Actions** column.
    -   To delete a policy version, click **Delete** in the **Actions** column. In the message that appears, click **OK**.

**Related topics**  


[SetDefaultPolicyVersion](/intl.en-US/API Reference (RAM)/Policy management APIs/SetDefaultPolicyVersion.md)

[GetPolicyVersion](/intl.en-US/API Reference (RAM)/Policy management APIs/GetPolicyVersion.md)

[ListPolicyVersions](/intl.en-US/API Reference (RAM)/Policy management APIs/ListPolicyVersions.md)

[DeletePolicyVersion](/intl.en-US/API Reference (RAM)/Policy management APIs/DeletePolicyVersion.md)

