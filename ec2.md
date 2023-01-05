### Creating first EC2 instance
- dkdj
- dksfsjdf
- dskf
- use below user data
  ```
    #!/bin/bash
    # install httpd (Linux 2 version)
    yum update -y
    yum install -y httpd
    systemctl start httpd
    systemctl enable httpd
    echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
  ``` 
 - SSH in to EC2
   - Open command prompt or powershell windows.
   - Go to .pem directory
   - 
