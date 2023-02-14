---
title: "IBM Aspera"
chapter: true
weight: 20
pre: "<b>3. </b>"
---


# Client Setup

---
 **1** Create an EC2 Keypair.


<details>
  <summary> -> <code>CLICK HERE</code> to see how to create a key pair</summary>

**AWS Console -> EC2 -> Key Pairs -> Create key pair**

![DEPLOY](/images/aspera/kp.jpg) 
![DEPLOY](/images/aspera/kp2.jpg)

</details>
<br>
 
 ---
 
 **2.** Launch the cloudformation template in a new tab. The template deploys the IBM Aspera Connect client package and mock data to use for testing. 

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=c1fss-aspera-workshop&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/aspera_instance.yaml)

 - Click the **Launch Stack** button.
 - Select your **KeyPair** created in the previous step.
 - Click **Next**.
 - Click **Next**.
 - Check the box for IAM acknowledgement.
 - Click **Submit**.

![DEPLOY](/images/aspera/cft.jpg) 
![DEPLOY](/images/aspera/cft2.jpg)

{{% notice info %}}
<p style='text-align: left;'>
A Key Pair is required before continuing this CloudFormation deployment. If you need help creating a Key Pair -> <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair" target="_top">Create a key pair</a>
</p>
{{% /notice %}}

---

**3. This machine will be used later on.**

---

# IBM Aspera

---

**1.** Sign up for a free IBM Aspera on Cloud trial. Click [here to register for a free trial](https://www.ibm.com/account/reg/us-en/signup?formid=urx-30538).

- Enter your Account informations and create a password.
- Click **Next**.
- Enter your additional details. Click **Next**.

![Aspera](/images/aspera/setup.jpg)
![Aspera](/images/aspera/setup2.jpg)

---

**2.** Verify email for Aspera on Cloud.

- Check the inbox of the email address provided in steps 1.
- Copy the confirmation code.

![Aspera](/images/aspera/setup3.jpg)

---

**3.** Start free Aspera on Cloud trial.
- Provide the confirmation code back in the Aspera borwser.
- Click on **Start your free trial**.

![Aspera](/images/aspera/setup4.jpg)

---


## Set Up-MFA
---

**1.** Choose the verification method to add MFA.

- Click Setup next to Authenticator App.
- Click **Connect your authenticator**.

![Aspera](/images/aspera/mfa.jpg)
![Aspera](/images/aspera/mfa2.jpg)

**2.** In an application such as Duo Mobile configure MFA with IBM Aspera.

- Test and Verify your authenitcator has been set up.
- Click **Done**.

![Aspera](/images/aspera/mfa3.jpg)
![Aspera](/images/aspera/mfa4.jpg)

---

## Sign into you IBM account.

---

**1.** Launch Aspera on Cloud.

- Click **Launch** to be directed to IBM Aspera on Cloud.

![Aspera](/images/aspera/account.jpg)

**2.** Authenticate to IBM Aspera on Cloud.

- Click on **Log in with IBMid**.

![Aspera](/images/aspera/aspera.jpg)
![Aspera](/images/aspera/aspera2.jpg)