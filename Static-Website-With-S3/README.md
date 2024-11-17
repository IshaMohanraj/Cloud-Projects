# Procedures : 

• Created a free tier account in amazon web services (AWS).

• Optional : Can create a user account utizing IAM, i skipping as this is a simple project and making use of root account

• Went into S3 and created a storage bucket of unique name, my case : ***static-portfolio-website-sabarimohanraj-isha*** was bucket name

• While creating, In "Object Ownership", let ACL be disabled.

• Need to allow the bucket to be accessable from anywhere, need to make public, so un-checked "Block Public Access settings for this bucket"

• Leaving the rest of the info aws default and creating the bucket

• Entered into the bucket and uploaded my mock portfolio index.html file.

• Going insto the bucket, then clicking over the file uploaded, index.html file in my case, we will be provided with "Object URL". This is the website link that we will be share to the outside would for our website.

![HTML file in Bucket](/Static-Website-With-S3/Images/URL-Page.png "S3-Object-url-page")

• Though Public Access was enabled, the bucket policy has to be updated to allow to fetch object in this bucket by anyone.

• So, using the help of policy generator, produced the below policy :

` {
    "Version": "2012-10-17",
    "Id": "Policy1731778027625",
    "Statement": [
        {
            "Sid": "AllReadAccess",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::static-portfolio-website-sabarimohanraj-isha/*"
        }
    ]
} `

![Public Access and Updated Bucket Policy](/Static-Website-With-S3/Images/permissions-bucket-policy.png "updated-bucket-policy-image")

• Go to Bucket --> Permissions --> Bucket Policy and updated the above.

• If the bucket policy is not updated, we can see a error message saying "Permission Denied" while trying to access the S3 Hosted Website (Check on incognito).

• Once policy updated, the page loaded up successfully : https://static-portfolio-website-sabarimohanraj-isha.s3.us-east-1.amazonaws.com/index.html


