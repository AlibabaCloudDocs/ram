# Create a custom policy

This topic describes how to create a custom policy. Custom policies provide more fine-grained access control than system policies.

Before you can create a custom policy, you must be familiar with the basic structure and grammar of the policy language. For more information, see [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **Policies** under **Permissions**.

3.  On the Policies page, click **Create Policy**.

4.  On the page that appears, specify the **Policy Name** and **Note** parameters.

5.  Configure the **Configuration Mode** parameter. Valid values: **Visualized** and **Script**.

    -   If you select **Visualized**, click **Add Statement**. In the panel that appears, configure the Permission Effect, Actions, and Resources parameters, select a service from the Select Product/Service drop-down list, and then click **OK**.

        **Note:** You can select ECS, SLB, RDS, VPC, or Redis from the Select Product/Service drop-down list

    -   If you select **Script**, edit the policy in the text editor below Policy Document. For more information, see [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

        **Note:** To improve efficiency, you can import an existing system policy and edit the policy based on your business requirements.

6.  Click **OK**.


**Related topics**  


[CreatePolicy](/intl.en-US/API Reference/API Reference (RAM)/Policy management APIs/CreatePolicy.md)

