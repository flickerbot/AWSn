S3 simple storage bucket -it is a global policy 

we create bucket in S# - that is region specific in nature

## launching a bucket
> Search for s3 
> Create bucket 
> type bucket name must be unique 
> leave rest properties as it is 
> launch bucket

## adding objects to bucket
> goto created bucket
> upload -- upload files can be of any nature upto 5tb 


## launching a static website using s3 

> create a basic file of index.html 
it will be containing our code for the website 


```
<html>
<body>
<h1> hey this is rishi </h1>
</body>
</html>

``` 

> now we can view this webpage using open option of s3 
here the site will not be visible if we try to access it via the object url because we have not allowed public settings so we can only view it by open url 

> now to view it in another tab we need to allow some permissions 

click on bucket and it will open a new window after clicking on our created bucket 

> click on permissions
> click edit Block public access (bucket settings) and uncheck all the properties allowing the bucket to be publically visible


> go to permission and in bucket policy write 

```
{
    "Version": "2012-10-17",
    "Id": "Policy1693973929155",
    "Statement": [
        {
            "Sid": "Stmt1693973927500",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::awsbuck666/*"
        }
    ]
}

```
this is a json file giving permission to access the bucket objects 
last line arn defines which objects are accessible 
like awsbuck666 is bucket name and after that * specifies all the objects in bucket are accessible 




### now we can view our site by clicking on object and accessing the object URL 



# note :
  
> we can also access our site by turning on static hosting which gives us a url to access the site
> we can use this option because as compared to object url, using the static website hosting URL provides a more polished and user-friendly experience. It simplifies URL structure, 
> handles error pages gracefully, and can be integrated more effectively with CDNs and other web services. It's a best practice for hosting static websites on AWS S3.



# hosting an isntance using s3 
https://medium.com/@KerrySheldon/ec2-exercise-1-3-host-a-static-webpage-with-content-from-s3-4496f1e642c2



![Screenshot (15)](https://github.com/flickerbot/AWSn/assets/78339973/f0b40feb-e743-46fa-99f4-cba6a85281b2)


![Screenshot (12)](https://github.com/flickerbot/AWSn/assets/78339973/bf97e768-d691-4557-b5d4-f98fdf4b04fe)


