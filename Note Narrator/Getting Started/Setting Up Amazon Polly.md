---
title: Setting Up Amazon Polly
description: Create an AWS user that can only synthesize speech with Polly, give its access keys an end date and a budget, and choose an engine, voice and region.
tags:
  - note-narrator
  - getting-started
  - amazon-polly
publish: true
permalink: note-narrator/getting-started/setting-up-amazon-polly
plugin-version: 1.2.0
updated: 2026-10-26
---

# Setting Up Amazon Polly

Note Narrator can generate speech with Amazon Polly. You need an AWS account and an access key pair (an access key ID and a secret access key). AWS charges for the audio at Polly's prices.

> [!warning] Keep the keys limited
> Note Narrator only needs one permission, `polly:SynthesizeSpeech`. Create a **separate IAM user** with **only that permission**, give its policy an **end date**, and set up a **budget** that blocks it when spending gets too high. Never use your root user's keys, or keys of a user with broader permissions such as `AdministratorAccess` or `AmazonPollyFullAccess`: if they leak, anyone can use your whole AWS account.

## 1. A user that can only synthesize speech

1. Sign in to the [AWS console](https://console.aws.amazon.com) and open **IAM, Users, Create user**. Name it, for example, `note-narrator`. Don't give it console access.
2. Attach a policy with only `polly:SynthesizeSpeech` (choose **Attach policies directly, Create policy**, then the **JSON** editor). The `aws:CurrentTime` condition is the keys' end date: after it, AWS refuses the user's requests. Replace the date with one a few months away.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "polly:SynthesizeSpeech",
      "Resource": "*",
      "Condition": {
        "DateLessThan": { "aws:CurrentTime": "2027-01-31T23:59:59Z" }
      }
    }
  ]
}
```

3. Open the new user, then **Security credentials, Create access key**. Choose **Application running outside AWS**, and copy both the access key ID and the secret access key: AWS shows the secret only once.

> [!info] Access keys don't expire on their own
> AWS access keys stay valid until you deactivate or delete them, so the policy's end date is what makes them stop working. When it passes, create a new access key, paste it into Obsidian, move the policy's date forward, and delete the old key under the user's **Security credentials**.

## 2. A budget that blocks the user

1. Open **Billing and Cost Management, Budgets, Create budget**, and create a monthly **cost budget** filtered to the **Polly** service, with the most you would be comfortable losing.
2. Add an **alert** below that amount, to get an email first.
3. Add a **budget action** at the amount: **IAM policy**, attaching the AWS managed **AWSDenyAll** policy to the `note-narrator` user. AWS Budgets needs a role it can use to apply the action; the console helps create it.

AWS updates budgets a few times a day, so the block isn't instant and spending can go past the amount. Once the action has run, detach **AWSDenyAll** from the user to use it again. See AWS's [budget actions documentation](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-controls.html).

## 3. Add it to Note Narrator

1. In Obsidian, open **Settings, Note Narrator, Providers**, select **+** and choose **Amazon Polly** (or switch an existing provider's **Type** to Amazon Polly).
2. Under **Access key ID** and **Secret access key**, pick or create a secret for each and paste the values.
3. Choose the **Region** Polly requests go to, ideally one near you. Some voices and engines are only offered in some regions.

> [!info] Where the keys live
> Both keys are stored with Obsidian's [secret storage](https://docs.obsidian.md/plugins/guides/secret-storage), not in the plugin's `data.json`. The secret access key is never sent: it only signs each request.

## Engines and voices

A narrator profile using Polly has:

| Setting | What it does |
| --- | --- |
| **Engine** | **Neural** (default), **Standard**, **Long-form** or **Generative**. They differ in quality and price |
| **Voice** | The chosen engine's voices, with their language. Changing the engine switches to its first voice if the current one doesn't have it |

Each part of a note is at most 3,000 characters. If Polly throttles a request, Note Narrator retries automatically. See [[Providers Settings]] and [[Profiles Settings]].

> [!info] What is sent
> The text being read and the engine and voice go to AWS (`polly.<region>.amazonaws.com`), signed with your keys, under the AWS Customer Agreement. See [[Privacy and Network Use]].
