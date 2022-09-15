# Discover and Protect Sensitive Data with Amazon Macie
## Introduction

Amazon Macie is a data security and data privacy service that uses machine learning and patch matching algorithms to scan, identify and discover sensitive data in S3 buckets with the aim of protecting them. Macie can discover Personally Identifiable Information (PII), national information, medical information, intellectual property, credentials and secrets as well as protected financial information. Other services that can be used to discover threats alongside Macie are Amazon Lambda and AWS Step Functions.

With Macie, the security of S3 buckets are managed and data breaches, anomalies and intrusions can be quickly detected and reported to the administrator.

Having discussed what Macie does, let’s quickly jump into how to use this service to discover and protect sensitive data in Amazon. 
<br></br>

<hr style="border:2px solid gray"></hr>

## Steps

1. [Create S3 bucket](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-1---create-s3-bucket) <br>
2. [Enable Amazon Macie service](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-2---enable-amazon-macie-service) <br>
3. [Upload data files to S3 bucket](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-3---upload-data-files-to-the-s3-bucket) <br>
4. [Create custom detection rule](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-4---create-custom-detection-rule) <br>
5. [Create and run a job](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-5---create-and-run-a-job) <br>
6. [Clean up](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-6---clean-up)
<br></br>

### Step 1 - Create S3 bucket
1. The first thing we need to do is sign in to the AWS console here [https://aws.amazon.com/](https://aws.amazon.com/) and create a S3 bucket to store the data files which will be used for this practical.<br>
![Search for Amazon Macie](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%201%20-%201.PNG)

2. To create a bucket, click on the **Create bucket** button. Ensure you give your bucket a **unique name** and **block public access**.
![Create bucket](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%201%20-%202.1.PNG)
![Create bucket](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%201%20-%202.2.PNG)

3. Once bucket is successfully created, go to the Amazon macie console and enable it.
![Bucket creation successful](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%201%20-%203.PNG)
<br></br>
### Step 2 - Enable Amazon Macie service
1. Navigate to the Amazon Macie console and click on the **Get started** button.
![Get started](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%202%20-%201.PNG)

2. The next screen states what happens when you enable this service. Click on the **Enable Macie** button to proceed.
![Enable Macie](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%202%20-%202.PNG)

3. Wait for some minutes for Macie to retrieve data from your s3 buckets. These data include public, encrypted and shared access of S3 buckets, top S3 findings, top finding types and policy findings.
![Retrieved data](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%202%20-%203.PNG)
<br></br>
### Step 3 - Upload data files to the S3 bucket
1. I will upload 2 data files to the recently created S3 bucket. **NB:** These [files](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/tree/main/data_files) are for demonstration purposes.
- **PII file** - This file contains some personal identifiable information
- **Custom file** - This file would be used to discover sensitive information by applying a custom detection rule ([Step 4](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/edit/main/README.md#step-4---create-custom-detection-rule))
2. After uploading the files, go to the Amazon Macie console to create a custom detection rule.
![Uploaded successfully](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%203.PNG)
<br></br>
### Step 4 - Create custom detection rule
1. On the Amazon Macie console, navigate to **Custom data identifiers** and click on the **Create** button.
![Custom data identifiers](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%204%20-%201.PNG)

2. On the create new custom data identifier screen, do the following
- Type in **Name** of your rule and add **Description** (optional)
- Type in **Regular expression (regex)** that defines the pattern to match/detect
- Type in **Keywords** and **Ignore words** that are close to the regex. These are also optional
- Type in **Maximum match distance** (optional)
- Choose **Severity**
- Add **Tags** (optional)
![Create new custom data identifiers](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%204%20-%202.PNG)

3. Click on the **Submit** button.

4. Once created, click on the **Custom data identifier** and test it to make sure it is working.
![Custom data identifier](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%204%20-%204%20.PNG)

5. Type in a **sample text** in the **Evaluate form** to test whether it is working and click on the **Test** button. If a match is found, it shows that the rule is working.
 
![Evaluate](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%204%20-%205%20.PNG)

<br></br>
### Step 5 - Create and run a job
1. On the Amazon Macie console, navigate to **Jobs** and click on the **Create job** button.
![Create a Macie job screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%201.PNG)

2. Select the **S3 bucket** you want Amazon Macie to discover and click on the **Next** button.
![Select S3 bucket screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%202.PNG)

3. On the **Review S3 buckets** screen, you can review and adjust your S3 bucket. Click on the **Next** button.
![Review S3 bucket screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%203.PNG)

4. On the **Refine the scope** screen, choose **One-time job** because we are analyzing the objects once. Click on the **Next** button.
![Refine the scope screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%204.PNG)

5. On the **Select managed data identifiers** screen, select **All** and click on the **Next** button.
![Refine the scope screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%205.PNG)

6. On the **Custom data identifiers** screen, select your **Custom data identifier** and click on the **Next** button.
![Custom data identifier screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%206.PNG)

7. On the **Select allow lists** screen, click on the **Next** button.
![Select allow lists screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%207.PNG)

8. On the **Enter general settings** screen, type in **Job name** and **Description** and add **Tags** (optional). Click on the **Next** button.
![Enter general settings screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%208.PNG)

9. On the **Review and create** screen, click on the **Submit** button to create a job.
![Review and create screen](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%209.PNG)

10. You will see created job with the **Status - Active(Running)**. It might take some minute for the status to change to **Completed**.
![Job created - active (running)](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%2010.PNG)

11. Once the status changes to **Completed**, click on the **Show results** dropdown menu and click on the **Show findings** option.
![Job completed](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%2011.PNG)

12. The results will be opened in a new tab. The findings contain the **two data files** and their **finding types**.
![Job results](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%2012.PNG)

13. Select the `SensitiveData:S3Object/Personal` finding to show its details. Click on the finding ID to check the finding which is presented in a json format.
![Details](https://github.com/iyabzz/discover-and-protect-sensitive-data-with-amazon-macie/blob/main/screens/Step%205%20-%2013.PNG)
```
"count": 1,
    "createdAt": "2022-09-15T18:14:13.677Z",
    "description": "The object contains personal information such as first or last names, addresses, or identification numbers.",
    "id": "1e21ee6a67dc279fd8340a72e6b7bb7d",
    "partition": "aws",
    "region": "us-west-2",
    "resourcesAffected": {
      "s3Bucket": {
        "allowsUnencryptedObjectUploads": "TRUE",
        "arn": "arn:aws:s3:::iyabz-macie",
        "createdAt": "2022-09-15T16:08:29.000Z",
        "defaultServerSideEncryption": {
          "encryptionType": "NONE",
          "kmsMasterKeyId": null
        },
        "name": "iyabz-macie",
```

14. Also, the `SensitiveData:S3Object/CustomIdentifier` json finding shows that a sensitive data has been detected.
```
"count": 1,
    "createdAt": "2022-09-15T18:14:13.677Z",
    "description": "This object contains content that matches one or more custom data identifiers for the organization. The content might include multiple types of sensitive information.",
    "id": "02914f1bae50c9d57a6463cd4623bb02",
    "partition": "aws",
    "region": "us-west-2",
    "resourcesAffected": {
      "s3Bucket": {
        "allowsUnencryptedObjectUploads": "TRUE",
```

### Step 6 - Clean up
1. **Disable Macie** in the Settings to stop it from running
2. Delete the bucket you created for this exercise

<hr style="border:2px solid gray"></hr>

## Conclusion
I explained how to identify and discover sensitive data in S3 buckets using Amazon Macie. This servive is of importance to ensure that there are no data breaches and also to protect the confidentiality of objects in S3 buckets. 


















