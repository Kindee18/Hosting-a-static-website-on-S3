
# Host a Website on Amazon S3


**Author:** Kindson Nathan  
**Email:** kindsonegbule15@gmail.com

---

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I will demonstrate how to host a static website on Amazon Simple Storage Service(S3). I'm doing this project to learn the basics on AWS services.

### Tools and concepts

Services I used were Amazon S3, Access Control Lists (ACLs), and the AWS Management Console. I used Amazon S3 to store and host my website files, ACLs to manage basic access permissions at the object level, and the AWS Management Console to create, configure, and test my bucket policy.

Key concepts I learned include the difference between ACLs and bucket policies — ACLs provide simple, object-level permissions, while bucket policies offer more detailed, centralized, and flexible access control. I also learned how to make my S3 bucket publicly accessible for website hosting, how to protect important files like index.html from being deleted, and how S3 regions can affect performance and pricing. Overall, this project helped me understand how to secure, manage, and host a static website effectively using AWS S3.

### Project reflection

This project took me approximately 20 minutes to complete. The most challenging part was understanding and correctly setting up the bucket policy to prevent deletion of specific files while still allowing public read access. It was most rewarding to see my website successfully hosted and protected on Amazon S3, knowing that I had configured both the permissions and security settings correctly.

---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me 3 minutes.

The Region I picked for my S3 bucket was Ireland(Europe) because it is geographically close to me, helping reduce latency and improve performance, and it often offers lower costs compared to some other regions.

S3 bucket names are globally unique! This means that no two buckets anywhere in the world can have the same name — once a name is taken by one AWS user, it cannot be used by anyone else in any AWS account or region.

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and image assets

I uploaded two files to my S3 bucket - they were an index.html file and a folder contain other supplementary things(like images e.t.c) needed in the webpage.

Both files are necessary for this project as one file which is the index.html file displays the text, images and videos while the other contains the document to be displayed in the index.html file. 

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting means storing a website’s files (such as HTML, CSS, images, and scripts) on a server (in this case our S3 bucket) so that they can be accessed over the internet by anyone using a web browser.

To enable website hosting with my S3 bucket, I chose General Purpose Buckets on the left hand side navigation bar, and then chose the bucket I created for this project. After that I chose the Properties Tab and then scroll all the way down to the Static website hosting panel and chose edit. Then under static web hosting, I chose Enable. Under hosting type, I chose Host a static website and then specified the index document by typing index.html. After that I clicked on save changes.

An ACL is a set of rules that desides who can get access to your resource. In this project, I enabled it.

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

Once static website hosting is enabled, S3 produces a bucket endpoint URL, which is a public web address that allows anyone to access your hosted site through a browser. It usually looks like this:

http://your-bucket-name.s3-website-region.amazonaws.com


This endpoint serves as the URL of your static website, allowing users to view the files (like index.html) directly from your S3 bucket.

When I first visited the bucket endpoint URL, I saw a 403 Forbidden error page. The reason for this error was that my S3 bucket or objects did not have the correct public access permissions.

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

To resolve this 403 Forbidden error, I checked my S3 bucket permissions and policy to ensure that public access was properly allowed. I verified that the “Block all public access” option was turned off, updated my bucket policy to grant public read access to my website files, and confirmed that the object ACLs also allowed public reading. After making these changes, I refreshed my website link and confirmed that it loaded successfully without the error.

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

An alternative to ACLs are bucket policies, which are JSON-based rules that define permissions at the bucket level and can specify who can access the bucket and what actions they can perform.

The benefit of using bucket policies is that they provide fine-grained, centralized control over access permissions, support complex conditions (like IP address restrictions or encryption requirements), and are easier to manage and audit than ACLs.

While ACLs are useful for granting simple, object-level access—especially when you need to make specific objects public or share them between AWS accounts—they are more limited and less flexible than bucket policies.

My bucket policy prevents anyone from deleting my index.html file while still allowing access to view it. I tested this by trying to delete the file from the S3 console and saw that the action was denied, confirming that my policy is working correctly.

![Image](http://learn.nextwork.org/restful_orange_loyal_cumin/uploads/aws-host-a-website-on-s3_sm2sm2sm)

---

---
