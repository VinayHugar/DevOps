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

## 4. Web Server

### Apache Web Server

#### Installation and Setup

- **Port**: 80

```sh
yum install httpd
service httpd start
service httpd status

