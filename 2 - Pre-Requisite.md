## 1. Basics

### Shell Types
- **Bourne Shell (Sh Shell)**: The original Unix shell.
- **C Shell (csh or tcsh)**: Shell with C-like syntax and scripting capabilities.
- **Z Shell (zsh)**: Advanced shell with features from bash, ksh, and tcsh.
- **Bourne Again Shell (bash)**: The most common shell in Linux, with scripting features.

## 2. Networking Basics

### Enable Packet Forwarding
1. **Temporary Enablement**:
    ```sh
    cat /proc/sys/net/ipv4/ip_forward
    echo 1 > /proc/sys/net/ipv4/ip_forward
    ```
2. **Permanent Enablement**:
    Edit `/etc/sysctl.conf`:
    ```sh
    ...
    net.ipv4.ip_forward = 1
    ...
    ```
### DNS Configuration
1. **Local DNS Entry**:
    ```sh
    cat >> /etc/hosts
    192.168.1.11 db
    ```
2. **Central DNS Configuration**:
    ```sh
    cat /etc/resolve.conf
    nameserver 192.168.100
    search yahoo.com
    ```

3. **Custom DNS Server for EC2 Instance**:
    - **Ubuntu**:
        ```sh
        sudo vim /etc/dhcp3/dhclient.conf
        prepend domain-name-servers 1.1.1.1;
        ```
    - **CentOS**:
        ```sh
        sudo vim /etc/dhcp/dhclient.conf
        ```
    - **Install and Configure resolvconf**:
        ```sh
        sudo apt install resolvconf
        /etc/resolvconf/resolv.conf.d/tail
        nameserver 1.1.1.1
        reboot
        ```


## 3. Security Basics

### Symmetric Encryption
Symmetric encryption uses the same key for both encryption and decryption. This key must be shared securely between the server and the client.

### Asymmetric Encryption
Asymmetric encryption involves a pair of keys: a private key and a public key. The private key remains on the server side, while the public key can be distributed widely.

### Key Types
- **Public Key**: Commonly stored in files with extensions such as `.crt`, `.pem`.
- **Private Key**: Commonly stored in files with extensions such as `.key`, `*-key.pem`.

### Managing Public Keys
To store a public key, you can append it to the `authorized_keys` file on the server:

```bash
cat ~/.ssh/authorized_keys
```


## 4. Applications Basics

### Popular Programming Languages

- JavaScript
- NodeJS
- Python
- Java
- C#
- PHP

### Compiler and Interpreter Usage

- **Compiler:** Java, C, C++
- **Interpreter:** Python, NodeJS, Ruby

## Java

#### Build Tools

- Maven
- Gradle
- ANT

#### Archive Types

- `.jar` (Backend)
- `.war` (Frontend & Backend)

#### Commands

- **Version check:** `java -version`
- **Compile:** `javac MyClass.java`
- **Documentation:** `javadoc -d doc MyClass.java`

#### ANT

- **Install:** `sudo yum install -y ant`
- **Compile:** `ant compile` or `ant compile jar`
- **Run:** `ant`

#### Maven

- **Install:** `sudo yum install -y maven`
- **Compile:** `sudo mvn package`
- **Run:** `java -cp /opt/maven/my-app/target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App`

## NodeJS

#### Installation

```sh
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
sudo yum install -y nodejs
```

#### Commands

- **Version check:** `node -v`
- **Run:** `node app.js`
- **Package Manager:** `NPM (package.json)`
- **Search Package:** `npm search file`
- **Install Package:** `npm install file`
- **Global Install:** `sudo npm install file -g`
- **Modules:**
  - *Built-in*: `/usr/lib/node_modules/npm/node_modules/`
  - *External*: `/usr/lib/node_modules`

## Python


#### Installation

```sh
yum install -y python36
```

#### Commands

- **Version check:** `python3 -V`
- **Run:** `python main.py`
- **Package Manager:** `pip`
- **Pip Version check:** `pip -V`
- **Install Package:** `pip2 install flask` or `pip3 install flask`
- **Check packages**: pip show flask
- **Check all packages:** `python[version] -c "import sys; print(sys.path)`
- **Install packages:** `pip install -r requirements.txt`
- **Uninstall:** `pip uninstall flask`
- **Upgrade:** `pip install flask --upgrade`


## 5. Web Server & Frameworks
 - Apache HTTP Server (Apache)
 - Nginx
 - Apache Tomcat
 - Python Web Frameworks
 - NodeJS Web Framework


## Apache HTTP Server (Apache)

#### Installation and Setup

- **Port**: 80

```sh
sudo yum update -y
```
```sh
sudo yum install httpd -y
```
```sh
sudo systemctl start httpd
```
```sh
sudo systemctl enable httpd
```
```sh
sudo systemctl status httpd
```
```sh
sudo vim /var/www/html/index.html
```
```sh
sudo systemctl restart httpd
```

### Logs
  **Access Log:** `cat /var/log/httpd/access_log`
 
  **Error Log:** `cat /var/log/httpd/error_log`

  **Config File:** `/etc/httpd/conf/httpd.conf`


### Virtual Hosts

To host multiple websites on a single server, add VirtualHost entries.

#### Example:

flipkart.conf

**Path:** `/etc/httpd/conf/flipkart.conf`

```sh
<VirtualHost *:80>
    ServerAdmin ec2-user@localhost
    DocumentRoot /var/www/flipkart
    ServerName flipkart.com
    ServerAlias www.flipkart.com

    <Directory /var/www/flipkart>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

#### Example:

amazon.conf

**Path:** `/etc/httpd/conf/amazon.conf`

```sh
<VirtualHost *:80>
    ServerAdmin ec2-user@localhost
    DocumentRoot /var/www/amazon
    ServerName amazon.com
    ServerAlias www.amazon.com

    <Directory /var/www/amazon>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

**Add the following lines to** `/etc/httpd/conf/httpd.conf:`

```sh
Include conf/flipkart.conf
Include conf/amazon.conf
```

## Apache Tomcat
 - **Port:** 8080

## Nginx
Hosting Multiple Websites on a Single Server using nginx

#### Prerequisites

- A server running a Linux distribution (e.g., Ubuntu, Linux)
- Basic knowledge of command-line operations
- nginx installed on your server

#### Installation

1. **Install nginx** (if not already installed):
    ```bash
    sudo yum update -y
    ```
    ```bash
    sudo yum install nginx -y
    
    or
    
    sudo amazon-linux-extras install nginx1
    ```
    ```bash
    sudo systemctl start nginx
    ```
    ```bash
    sudo systemctl enable nginx
    ```
    ```bash
    sudo systemctl status nginx
    ```
    ```bash
    sudo systemctl restart nginx
    ```

2. **Create directories for your websites** (assuming you have `example1.com` and `example2.com`):
    ```bash
    sudo mkdir -p /var/www/example1.com/html
    sudo mkdir -p /var/www/example2.com/html
    ```

3. **Set permissions for the directories**:
    ```bash
    sudo chown -R $USER:$USER /var/www/example1.com/html
    sudo chown -R $USER:$USER /var/www/example2.com/html
    sudo chmod -R 755 /var/www
    ```

4. **Create sample index.html files for your websites**:
    ```bash
    echo "<html><head><title>Welcome to Example1</title></head><body><h1>Success! The example1.com server block is working!</h1></body></html>" > /var/www/example1.com/html/index.html

    echo "<html><head><title>Welcome to Example2</title></head><body><h1>Success! The example2.com server block is working!</h1></body></html>" > /var/www/example2.com/html/index.html
    ```

5. **Create server block configuration files for each website**:
    - For `example1.com`:
      ```bash
      sudo nano /etc/nginx/sites-available/example1.com
      ```
      Add the following content:
      ```nginx
      server {
          listen 80;
          server_name example1.com www.example1.com;

          root /var/www/example1.com/html;
          index index.html;

          location / {
              try_files $uri $uri/ =404;
          }
      }
      ```
    - For `example2.com`:
      ```bash
      sudo nano /etc/nginx/sites-available/example2.com
      ```
      Add the following content:
      ```nginx
      server {
          listen 80;
          server_name example2.com www.example2.com;

          root /var/www/example2.com/html;
          index index.html;

          location / {
              try_files $uri $uri/ =404;
          }
      }
      ```

6. **Enable the server blocks by creating symbolic links**:
    ```bash
    sudo ln -s /etc/nginx/sites-available/example1.com /etc/nginx/sites-enabled/
    sudo ln -s /etc/nginx/sites-available/example2.com /etc/nginx/sites-enabled/
    ```

7. **Test the nginx configuration for syntax errors**:
    ```bash
    sudo nginx -t
    ```

8. **Reload nginx to apply the changes**:
    ```bash
    sudo systemctl reload nginx
    ```

9. **Update your DNS settings** to point to your server's IP address for `example1.com` and `example2.com`.


## Python Web Frameworks
 - **Port:** 8000
 - **Frameworks:** Flask, Django
 - **Production Deployment:**
   - **Gunicorn**
   - **uWSGI**
   - **Gevent**
   - **Twisted Web**

## NodeJS Web Framework
 - **Port:** 3000
 - **Framework:** ExpressJS
 - **Production Deployment:** PM2
 - `pm2 start app.js`
 - `pm2 start app.js -i 4`


## 6. Database

**Types:**
 - **SQL:** Structured Query Language, relational databases with tables.
   
   **Examples:** MySQL, PostgreSQL, Microsoft SQL Server
        
 - **NoSQL:** Non-relational databases, often document-based.
   
    **Examples:** MongoDB, Amazon DynamoDB
