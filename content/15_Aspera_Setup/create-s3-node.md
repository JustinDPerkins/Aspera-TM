---
title: "Create Node and S3"
chapter: true
weight: 21
pre: "<b>3.2 </b>"
---


### S3 Bucket Creation

---

**1.** Sign in to the AWS Management Console and open the Amazon S3 console at https://console.aws.amazon.com/s3/.
![Diagram](/images/create_s3.png)

---

**2.** Choose Create bucket. The Create bucket wizard opens.
![Diagram](/images/create_s3_2.png)


**3.** In Bucket name, enter a DNS-compliant name for your bucket.
The bucket name must:

- Be unique across all of Amazon S3.
- Be between 3 and 63 characters long.
- Not contain uppercase characters.
- Start with a lowercase letter or number.

After you create the bucket, you can't change its name. For information about naming buckets, see Bucket naming rules.

{{% notice warning %}}
<p style='text-align: left;'>
Remember that S3 bucket are an unique name globally for all AWS customers. If you try to use the same name from this workshop you will have some issues with an existing S3 bucket name already created.
</p>
{{% /notice %}}

![Diagram](/images/create_s3_3.png)

**4.** Scroll down and click on Create bucket. 

![Diagram](/images/create_s3_4.png)

---
**5.** Now you have successfully create a S3 bucket for the workshop.

![Diagram](/images/create_s3_5.png)

---

### IBM Aspera Node Creation.

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

---

**2.** Download and safely store your access keys.
![Aspera](/images/aspera/node11.jpg)

---

Let's start the Cloud One - File Storage Security deployment now. :laptop::cloud::rocket:
</details>
----