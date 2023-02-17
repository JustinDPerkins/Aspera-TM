---
title: "Create Node for S3"
chapter: true
weight: 21
pre: "<b>3.2 </b>"
---


### S3 Bucket Creation

---

{{% notice warning %}}
<p style='text-align: left;'>
If attending this workshop with Trend Micro. The S3 buckets have already been deployed for you in the Event Engine Account provided. Skip over this launch stack button below.
</p>
{{% /notice %}}

This template creates two S3 buckets. A source S3 bucket to configure with Aspera and FSS. The other to quarantine files marked by FSS.

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=c1fss-aspera-buckets&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/aspera_lab_buckets.yaml)

<details>
  <summary> -> <code>CLICK HERE</code> to see steps to create the Stack above.</summary>

**1.** Clicking Launch Stack will direct you to AWS Cloudformation.
- Accept all the defaults.
- Click Next
- Create Stack.

---


</details>
<br>



---

# IBM Aspera Node Creation

---

**1.** In the Aspera on Cloud Admin app, Go to **Nodes and storage > Nodes > Create new**.
-  Click **Attach my cloud storage** tab.
- Enter a Node name for the transfer service node.[This name refers to the AWS S3 storage]
- In the Storage field, select Amazon S3.
- In the Region field, select the Amazon region that contains the S3 bucket.
- In the Storage class field, select **Standard**.
- **Copy the trust relationship policy contents** and leave this page open. We need to create an IAM role in the AWS account with the provided policy.

![Aspera](/images/aspera/node.jpg)


**2.** Create an Aspera IAM Role and Policy.
- Log in to the AWS portal. **Go to Services > IAM > Roles**.
- Click Create Role.
- Select **Custom trust policy** for trusted entity type.
- Paste the provided trust relationship policy contents in the editor.
- Click **Next**.

![Aspera](/images/aspera/node2.jpg)
![Aspera](/images/aspera/node3.jpg)

---

**3.** Create an Aspera policy to allow S3 access.
- Click **Create policy**.
- Click the **JSON** tab.

![Aspera](/images/aspera/node4.jpg)

---

**4. Copy** the following JSON policy.

```
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Sid":"VisualEditor0",
         "Effect":"Allow",
         "Action":[
            "s3:PutObject",
            "s3:GetObject",
            "s3:AbortMultipartUpload",
            "s3:DeleteObject",
            "s3:ListMultipartUploadParts"
         ],
         "Resource":"arn:aws:s3:::bucket-name/*"
      },
      {
         "Sid":"VisualEditor1",
         "Effect":"Allow",
         "Action":[
            "s3:ListBucketMultipartUploads",
            "s3:ListBucket",
            "s3:GetBucketLocation"
         ],
         "Resource":"arn:aws:s3:::bucket-name"
      }
   ]
}
```
---

**4. Paste** it in the IAM policy editor. 
- **Replace/modify the resource bucket name with the name of your S3 bucket.**
- Click **Next:Tags**.
- Click **Next:Review**.**
![Aspera](/images/aspera/node5.jpg)

---

**5.** Review and Create Policy.
- Policy Name: ```aspera-s3-policy```
- Click **Create policy**.
![Aspera](/images/aspera/node6.jpg)

---

**6.** Attached the Aspera policy to the Aspera role.
- Search for the policy by name: ```aspera-s3-policy```
- Check the box to select.
- Click **Next**.

![Aspera](/images/aspera/node7.jpg)


---

**7.** Name, review and create role.
- Role Name: ```aspera-s3-role```
- **Create role**.

![Aspera](/images/aspera/node8.jpg)


---
**8.** Search for the **aspera-s3-role and copy its ARN**.

![Aspera](/images/aspera/node9.jpg)


---

## Complete Node Creation

---

**1.** Return to the IBM Aspera admin portal.
- For IAM role ARN: **Paste the aspera IAM role arn**.
- Bucket: ```the name of your bucket```
- Path: ```/```
- Click **Create**.

![Aspera](/images/aspera/node10.jpg)

{{% notice warning %}}
<p style='text-align: left;'>
If the connection fails, refresh the webpage. Repeat the steps above and update the IAM trust policy in AWS created before with the latest provided.
</p>
{{% /notice %}}

---

**2.** Download and safely store your access keys.
![Aspera](/images/aspera/node11.jpg)

---

</details>

----