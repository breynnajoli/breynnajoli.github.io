---
title: "Cloud Security with IAM Access: A Hands-on AWS Project"
date: 2026-02-18 14:00:00 +0300
categories: [Cloud Computing, AWS]
tags: [aws, iam, ec2, cybersecurity, cloud-security]
---

Ever wondered how big tech companies keep their cloud servers from turning into hacker playgrounds? 

Earning my AWS Cloud Practitioner certification sparked my curiosity about this exact question—how do you lock down cloud resources so only the right people touch the right stuff? That curiosity led me deep into the world of **AWS Identity and Access Management (IAM)**. 

Imagine a small organization running two EC2 instances: one for testing wild ideas (Development) and another for the real deal (Production). Now picture what could happen if everyone had full access to both… yeah, chaos. 

This project dives into solving that by setting up precise permissions, secure user roles, and smart group policies so every developer, admin, and intern knows their lane. It’s like giving each team member their own digital keycard, customized for their exact role.

## Project Summary
In this project, I demonstrate how to secure AWS resources using Identity and Access Management (IAM). I stepped into the role of a cloud administrator for a small organization managing two EC2 instances—one dedicated to development and another to production workloads. 

**The Mission:** Create IAM users, groups, and policies that enforce the **principle of least privilege**, ensuring users only access what they actually need. 

### Project Objectives
* **Understand and implement IAM concepts:** Gain practical knowledge of IAM users, groups, roles, and policies.
* **Control access to EC2 instances:** Restrict permissions so developers access only development resources while production access is limited to administrators.
* **Apply the principle of least privilege:** Ensure users have only the permissions necessary to perform their tasks, reducing security risks.
* **Configure AWS account alias:** Simplify account identification within the AWS console.

---

## Step 1: Create the EC2 Instances
Amazon EC2 (Elastic Compute Cloud) allows you to launch and manage virtual servers in the cloud. Think of these instances as computers you can use to run applications or host websites. 

**1. Development Instance:**
* **Name & Tag:** `Development Instance` + Tag: `Environment=Development`
* **AMI:** Amazon Linux 2
* **Instance Type:** t2.micro (free-tier safe!)
* **Security:** Created a security group to allow SSH.

**2. Production Instance:**
Redoing the exact same procedure, I launched a second instance with the Name and Tag set to `Production Instance` and `Environment=Production`. 

Boom! Both instances are live. 

---

## Step 2: Set Up Permission Policies
Next, I created an IAM Policy to give selective access to these instances. A policy is a JSON document that defines permissions. 

Here is the JSON policy written for this project:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances",
                "ec2:DescribeInstances"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ec2:ResourceTag/Environment": "Production"
                }
            }
        },
        {
            "Effect": "Deny",
            "Action": [
                "ec2:CreateTags",
                "ec2:DeleteTags"
            ],
            "Resource": "*"
        }
    ]
}


## Step 3: IAM Users and Groups
Choose **User groups** in your left-hand navigation panel.

AWS IAM user groups are collections of IAM users that allow you to manage permissions for multiple users at once, rather than assigning policies to each individual.

Choose **Create group**.
Setting up a User Group:
* Name: `2025Users`
* Attach Permission Policies: `Environpolicy`

Select **Create User Group**.

---

## Step 4: User Creation
In AWS IAM, a user is an identity you create within your account that has specific permissions to access AWS resources. These users have credentials (name and password) for signing in to the AWS Management Console and can also be given access keys for programmatic access. You can create users individually, organize them into groups, and manage their permissions using policies.

1. Choose **Users** from the left-hand navigation panel.
2. Choose **Create user**.
3. Under username, enter a username e.g. `Breakingbird`.
4. You can opt to leave the checked box for *users must create new password at next sign-in* or uncheck it and create a custom password. For our case we’ll create a custom password.

Click **Next**.

To **Set Permissions** for your user, add your user to the user group you’ve created. Select the checkbox next to **2025Users**. — Select **Next**. — Select **Create user!**

User added to a user group.

---

## Step 5: Test User’s Access
Let's now test if the policy is really working. That way we can make sure that they have the right access to our Production instance (and not the Development Instance).

1. Copy the **Console sign-in URL**. Do not close this tab!
2. Open a new **incognito window** on your browser.
3. Open the new console sign-in URL in your incognito window.
4. Using the Username and Console password given in your IAM tab, let’s log in!

As a new user, you’ll notice that some of your dashboard panels are showing **Access denied** already.

Navigate to your **EC2** console and make sure you’re in the same **Region** as the one where you deployed your two Development and Production instances.
Choose **Instances**. Select your **Development** instance by checking the box and in the **Instance state** dropdown, select **Stop instance**.

Let’s try to stop this instance. Select **Stop**.

At the top of your page, an error banner tells us we’ve failed to stop this instance. The banner tells us it’s because we’re not authorized! We don’t have permission to stop any instance with the production tag.

Now, let’s try to stop the **Production** instance.
1. Head back to the **Instances** page and select the checkbox next to **Production Instance**.
2. Under the **Actions** drop-down, select **Manage instance state**.
3. Select **Stop**, then **Change state**. Select **Stop**.

The Instance will be successfully stopped as shown below.

Success 

Wrapping up this project, we realized how much power and responsibility comes with managing access in the cloud. What started as curiosity turned into a deeper appreciation for how AWS IAM keeps organizations secure and organized. This project might be complete, but my exploration into cloud security has only just begun.
