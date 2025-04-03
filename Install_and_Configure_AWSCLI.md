# # Installing and Configuring AWS CLI on macOS

## 1. Installing AWS CLI on macOS

### Method 1: Using Homebrew (Recommended)
1. Open Terminal.
2. Run the following command to install AWS CLI:
   ```sh
   brew install awscli
   ```
3. Verify installation:
   ```sh
   aws --version
   ```
   Expected output (version may vary):
   ```sh
   aws-cli/2.x.x Python/x.x.x Darwin/x86_64 source
   ```

### Method 2: Using AWS Installer
- Follow the steps for installing the latest AWS CLI for macOS from:
  [AWS CLI Installation Page](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
---

## 2. Configuring AWS CLI

### Step 1: Create AWS IAM User and Get Credentials
1. Go to [AWS IAM Console](https://console.aws.amazon.com/iam/).
2. Create a new IAM user with programmatic access or Go to the User if already created and attach policies like `AdministratorAccess` or specific permissions.
3. Generate Security Credentials using AWS Management Console
   * Go to Services -> IAM -> Users -> "Your-Admin-User" -> Security Credentials -> Create Access Key
4. Note down the **Access Key ID** and **Secret Access Key**.

### Step 2: Configure AWS CLI
Run the following command:
```sh
aws configure
```
It will prompt for:
- **AWS Access Key ID**: Enter your Access Key.
- **AWS Secret Access Key**: Enter your Secret Key.
- **Default region name** (e.g., `us-east-1`).
- **Default output format** (choose `json`, `table`, or `text`).

### Step 3: Verify Configuration
Run:
```sh
aws s3 ls
```
If everything is configured correctly, this will list your S3 buckets.

---

## 3. Managing AWS CLI Profiles
You can create multiple profiles using:
```sh
aws configure --profile myprofile
```
To use a specific profile:
```sh
aws s3 ls --profile myprofile
```
To list all profiles:
```sh
cat ~/.aws/credentials
```

---

## 4. Updating AWS CLI
To update AWS CLI using Homebrew:
```sh
brew upgrade awscli
```
To check the latest version:
```sh
aws --version
```

---

## 5. Uninstalling AWS CLI
To remove AWS CLI installed via Homebrew:
```sh
brew uninstall awscli
```
To remove AWS CLI installed via `.pkg` file:
```sh
sudo rm -rf /usr/local/aws-cli
sudo rm /usr/local/bin/aws
```
