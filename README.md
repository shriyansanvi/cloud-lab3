# AWS EC2 Static Website Hosting

## Objective
Deploy a static HTML website on an AWS EC2 instance using the Apache HTTP Server (httpd).

## Prerequisites
- AWS Account
- EC2 Instance (Amazon Linux)
- Key Pair (.pem file)
- SSH Client
- Basic HTML file (index.html)

## Steps

### 1. Launch an EC2 Instance
- Create an EC2 instance.
- Download the key pair (.pem).
- Allow the following inbound rules:
  - SSH (22)
  - HTTP (80)

### 2. Connect to the Instance

```bash
chmod 400 keys.pem
ssh -i "keys.pem" ec2-user@<public-dns>
```

### 3. Update Packages

```bash
sudo yum update -y
```

### 4. Install Apache

```bash
sudo yum install -y httpd
```

### 5. Start and Enable Apache

```bash
sudo systemctl enable --now httpd
```

### 6. Create the Website

```bash
nano index.html
```

Paste your HTML code and save the file.

### 7. Move the File

```bash
sudo mv index.html /var/www/html/
```

### 8. Verify the Website

Open your browser and visit:

```
http://ec2-13-63-49-164.eu-north-1.compute.amazonaws.com
```


## Commands Used

```bash
chmod 400 keys.pem
ssh -i "keys.pem" ec2-user@<public-dns>
sudo yum update -y
sudo yum install -y httpd
sudo systemctl enable --now httpd
nano index.html
sudo mv index.html /var/www/html/
```

## Concepts

- **Cloud Computing:** Delivery of computing resources (servers, storage, networking, etc.) over the internet.
- **EC2:** Elastic Compute Cloud, a virtual server provided by AWS.
- **Apache (httpd):** A web server used to host websites.
- **Security Group:** Acts as a virtual firewall that controls inbound and outbound traffic.

## Output

The website is successfully hosted on an AWS EC2 instance and is accessible through the instance's public IP address or public DNS.
