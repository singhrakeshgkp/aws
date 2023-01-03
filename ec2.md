### Creating first EC2 instance
- dkdj
- dksfsjdf
- dskf
- use below user data
  ```
    yum update -y
    yum install -y httpd
    systemctl start httpd
    system ctl enable httpdt
    echo "<h1>Hello world $(hostname -f)<h1/>"/var/www/html/index.html
  ``` 
