<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Website Delivery with CloudFront

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-cloudfront)

**Author:** SHIVARAMAN RAMAKRISHNAN  
**Email:** shivaraman.r02@gmail.com

---

## Website Delivery with CloudFront

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_1dddddwe)

---

## Introducing Today's Project!

In this project we will see how cloudformation works to host a web application globally and how different it is from just static hosting. 
We will also see the 3 tiers of an application
the presentation tier, logic and data tier.

### Tools and concepts

The services we used were S3 to store the web files, Cloudfront to host the web page globally and load them faster than standard static hosting. CDN use edge location caching to make web pages load faster. OAC is a type of permission that lets the CDN get access to the webpage files stores in the S3 bucket.

### Project reflection

Not long

yes, I learnt a lot about webpage hosting

---

## Set Up S3 and Website Files

While the star AWS service in this project is CloudFront, CloudFront is not a storage solution. CloudFront is a content delivery network that simply hosts content that is stored somewhere else, like Amazon S3.


The 3 files are HTML, CSS and JS. 

index.html is the main file for a website. It's where you organise the text, pictures, and everything that makes up your webpage.

style.css is where you write down the visual appearance of your website's HTML elements. It controls everything from font sizes and colors to layout designs, helping you keep a consistent style across your website.

script.js refers to a JavaScript file that adds interaction to your website. It's where you would write the instructions for making things on your website move or change when you click a button or submit a form.

I validated the website works by simply opening them from my local browser

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_qgo7wcd3)

---

## Exploring Amazon CloudFront

Cloudfront is a Content Delivery Network which means it speeds up the distribution of the web application to the users from anywhere in the world. This happens because the files are stored as cache in multiple locations, thus when someone opens a web page, they are routed to the nearest location.

Businesses and Developers use cloudfront because it has high performance and the possibility of unsatisfied end users is not there.

A CloudFront distribution is a set of instructions that tells CloudFront how to deliver your content.

It specifies where your website's files are stored (called the origin), how they should be cached, and other delivery settings like security standards.

Paths help organize and structure the content on websites, making it easier for both users and systems like search engines or CDNs like CloudFront find specific information.

When you set up a CloudFront distribution, you don't have to get CloudFront to distirbute your entire website - you can cherry pick a specific file or section of your website to distribute. To do this, you'd configure your distribution with a specific origin path.


My CloudFront distribution's default root object is index.html. This means that when users visit this webpage, the index file is called and rendered in to their display as the default page and then they can navigate from there.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_qgo7wcdt)

---

## Handling Access Issues

We haven't given CloudFront permission to access our S3 bucket yet.

By default, S3 buckets are private. CloudFront needs explicit permission to access the files in your bucket.

The origin setting was initially public, it means anyone can access the content directly from the origin i.e. your S3 bucket, not just via CloudFront. This can become a security risk if sensitive data is accessible.

An origin access control (OAC) is a special user for CloudFront that prevents this. An OAC lets you keep your S3 bucket and objects not publicly accessible, while still making sure they can be accessed through CloudFront.

OAC also gives you granular control over how CloudFront accesses the content. For example, you can add other authentication or security settings to make sure only legitimate users can access your content.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_egrhntyu)

---

## Updating S3 Permissions

The OAC's role is that it makes sure only CloudFront can access the files stored in the S3 bucket. For this restricted access to be effective, the S3 bucket's policy still needs to explicitly grant the OAC permission to the bucket's contents.

Creating an OAC automatically gives me a policy I could copy, which grants our cloudfront distribution access to all the items in the s3 bucket. 

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_eg98ntyu)

---

## S3 vs CloudFront for Hosting

For my project extension, I'm comparing cloudfront and static hosting. I initially had an error with static website hosting because we enabled s3 web hosting without making our objects publically available.

Unchecking Block all public access doesn't grant permission to access the objects. It simply stops blocking all public access attempts.

In other words, think of it as another security guard for your bucket's front door, but disabling it doesn't mean you've opened the door yet - it only means than you've sent the guard away, and you can open the door to traffic now.

You still need a bucket policy to explicitly grant permissions. When you set up a bucket policy that allows public read access, you're telling AWS to let anyone on the internet to read the files in the bucket.

I could finally see my S3 hosted website when i updated the policy to the bucket. This worked because initailly only cloudfront OAC had access and now the added policy statement lets the static page also access the items inside the bucket

Compared to the permission settings for my CloudFront distribution, using S3 meant I had to enable public access to my bucket. I prefer using Cloudfront because it means I get to keep the bucket access to the CDN only which is great for security and privacy. 

---

## S3 vs CloudFront Load Times

Load times mean how quickly content on your website loads.

The faster the load time, the quicker the user accesses your website content. This is a great way to improve the user experience and can contribute to your site having better search engine rankings!

The load time in cloudfront is faster because CloudFront's CDN caches content closer to users globally, while S3 static website hosting serves files directly from a single region.

A business would prefer CloudFront when they require high performance and faster load times to run their applications. S3 static website hosting might be sufficient when those requirements aren't needed and its just a simple webpage.



![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-networks-cloudfront_12verpuh)

---

---
