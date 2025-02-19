---------------# SOP: Create an S3 Bucket, Host a static website, Bucket Versioning # ---------------------

# How to Create an S3 Bucket on AWS # 

1. Go to S3 service and click on create bucket.
   ![image](https://github.com/user-attachments/assets/959e88fd-6daf-4341-a788-a00ff5249af5)

2. Next, choose the Region in which you want to create a bucket.
   ![image](https://github.com/user-attachments/assets/63acab21-3ba5-4b24-a9d5-3e6bb9bdfea7)

3. In the left navigation pane, choose General purpose buckets.
4. a) Choose a bucket name, it must be across all regions and all accounts ever created in aws.
   ![image](https://github.com/user-attachments/assets/1d654b9a-b2f5-45aa-aae3-2e13c1bf3afa) <br>
   b) AWS allows you to copy an existing bucket's settings to your new bucket. If you do not want to copy the settings of an existing bucket, skip to the next step.<br>
   c) Under Ownership, ACLs(Access Control List) is disabled.<br>
   d) Next, Enable the blocking bucket policy as it so that it will block all the public access. By default, your bucket is always private.<br>
   e) Under Bucket Versioning, keep it disable. We will see later, how to enable it.<br>
   f) No tags are needed and Keep everything as default.<br>
   g) Click on “Create Bucket”.
   ![image](https://github.com/user-attachments/assets/4e88202a-69ea-4b96-9862-41179b25fdae) <br>

## Upload file ## 
5. Go inside your bucket. Let’s upload object--> click on upload--> add files--> then choose this coffee.jpeg file--> also see the destination of the file--> click on upload.
   ![image](https://github.com/user-attachments/assets/cd8e3866-d029-41bf-89f9-72585f3c752d)
6. Click on the object: you can see the more details about the object.
   ![image](https://github.com/user-attachments/assets/c668e08a-4ca1-45bb-877f-e93ab97c2a36)
7. Copy the object URL--> try to open it to see whether it is working or not. I get an access denied error, so let’s fix this error.
   ![image](https://github.com/user-attachments/assets/53e8440c-dd33-4c24-95c5-8485547411bc)

## Set Bucket Policy for Public Access   ## 
8. For that, Go to the bucket permission--> allow public access(edit—unchecked—save changes--confirm)--> it is a dangerous action off course if you using real data of your company on s3 bucket, and you make it public then may have data leak.
9. Under Bucket policy (edit—go to policy generators – Select type of policy = S3 bucket Policy, Effect = Allow , Principal= *  Actions= GetObject, ARN = your_bucket_arn/* --> click on add statement--> click on policy generate--> copy this policy and paste in the bucket policy--> Save Changes.
10. Copy the object URL and see it is working now.
    ![image](https://github.com/user-attachments/assets/728018c2-90cb-4805-b3fd-b71cd24c34e6)


# Static Website Hosting # 
1. Upload a new index.html file.
   ![image](https://github.com/user-attachments/assets/ef1c23ad-1c1c-4b5c-a8ec-da83f39bcb74)
2. Go to the bucket properties--> scroll down and at the bottom you can see static website hosting--> Click on edit--> Enable--> and then index document is index.html--> save changes.
   ![image](https://github.com/user-attachments/assets/c6436cf3-0f87-47a5-9ac6-71467e883245)
3. Copy the Bucket website endpoint URL seen in static website hosting.
   ![image](https://github.com/user-attachments/assets/7f9756c4-b0d1-4705-babf-90670972d8c6)
4. Copy the url and paste on any browser. It is working and we successfully hosted a static website.
   ![image](https://github.com/user-attachments/assets/4c20bf6a-4093-4c7e-b524-ba368361ec41)


# Bucket Versioning #
1. Go to Bucket Properties--> see Bucket Versioning--> edit--> enable it--> save the changes.
   ![image](https://github.com/user-attachments/assets/80a02bdb-9359-4368-bcab-69d3eeaf6678)
2. Now, any file we override is having versioning.
Update the index.html file--> save file--> upload it on S3--> Copy the static url.
![image](https://github.com/user-attachments/assets/ab4ac41a-ad49-494d-b8b1-fc32c8a81ce1)
4. Go to bucket--> Click on show versions toggle
   ![image](https://github.com/user-attachments/assets/d1bcce3c-02e9-431a-a0a2-56066a4c8663)
5. The file shows null id becoz it's upload before the versioning is enabled.
6. We can roll back by deleting the versioning id file.


   




















   
