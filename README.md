aws s3api create-bucket --bucket schoollm-test-app1 --region eu-west-2 --create-bucket-configuration LocationConstraint=eu-west-2

aws s3 website s3://schoollm-test-app1/ --index-document index.html

{   
  "Version":"2012-10-17",   
  "Statement":[{  
    "Sid":"PublicReadGetObject",           
    "Effect":"Allow",    
    "Principal": "*",       
    "Action":["s3:GetObject"],       
    "Resource":["arn:aws:s3:::schoollm-test-app1/*"]
  }] 
}


aws cloudfront create-distribution \
  --origin-domain-name schoollm-test-app1.s3.amazonaws.com \
  --default-root-object index.html


domain name: d103x6ebu78uzq.cloudfront.net