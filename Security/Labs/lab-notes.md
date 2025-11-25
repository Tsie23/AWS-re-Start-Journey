# Security Lab: Data Protection

## Objective
Learn how to:
Create an AWS KMS encryption key
Install the AWS Encryption CLI
Encrypt plaintext
Decrypt ciphertext

## Steps Taken

## 🔑 Part 1: Make Your Encryption Key

This first part shows you how to create a special encryption key, which we call a **KMS key**, that you'll use to protect your secret files.

### Step 1: Head Over to the Key Management Service

Start in your management console. Look for the **KMS** tool in the search bar, then click the result that says **Key Management Service**. Once you're on the KMS page, click the button to **Create a key**.

### Step 2: Choose the Key Type

For the **Key type**, select **Symmetric**. A symmetric key is fast and efficient because it uses the exact same key to both scramble (encrypt) and unscramble (decrypt) your data. After choosing Symmetric, hit **Next** to move on.

### Step 3: Name and Describe Your Key

Now you'll give your key a name and a description so you can easily find it later. For the **Alias**, type in **MyKMSKey**. For the **Description**, enter: **Key used to encrypt and decrypt data files.** Double-check that both look right, and then click **Next**.

### Step 4: Grant Key Administrative Rights

On the next screen, you need to decide who can manage or administrate this key. In the **Key administrators** section, find and select the checkbox for **voclabs**. This grants the necessary administrative control. When that's done, select **Next**.

### Step 5: Grant Key Usage Permissions

Next, you'll specify who can *use* the key to actually encrypt and decrypt files. In the **This account** section, make sure you find and select the checkbox for **voclabs** again. This gives the necessary usage permissions. Once selected, choose **Next**.

### Step 6: Finish the Key Creation and Copy the Key ARN

Take a moment to look over the settings on the final review page. If everything looks correct, click **Finish**. Immediately after the key is created, click the link for **MyKMSKey**. You will see a long, unique code for your key called the **ARN (Amazon Resource Name)**. **Copy this entire ARN value and paste it into a simple text editor.** You'll need this specific code later on.

## Task 2: Set Up the File Server

Before you can use your new key to scramble and protect files, you need to prepare the computer that will be doing the work—the **File Server EC2 instance**.

### Step 7: Connect to the File Server

In your console's search bar, type **EC2** and select the EC2 service. Look for the list of running instances and click the checkbox next to the **File Server** instance. With the server selected, click the **Connect** button at the top. Choose the **Session Manager** tab on the connection screen, and then click **Connect** again to open a terminal window to the server.

### Step 8: Create a Temporary Credentials File

Once you have the terminal open, you'll need to run two quick commands. First, run `cd ~` to make sure you are in the main (home) directory. Second, run `aws configure`. When prompted, temporarily enter **1** for both the **AWS Access Key ID** and **AWS Secret Access Key**, and then press Enter after each. For the **Default region name**, copy and paste the correct region from the Vocareum AWS Details page. Just press Enter for the **Default output format**. This creates a temporary configuration file that you'll update next.

### Step 9: Get the Real AWS Credentials

Now, switch back to the main Vocareum console page and click the **AWS Details** button. Next to the **AWS CLI** section, click **Show**. You will see a block of code starting with `[default]`. **Copy this entire code block and paste it into the text editor** where you saved your key's ARN.

### Step 10: Update the Server Credentials File

Return to your File Server terminal. You need to open the temporary credentials file you just created by running the command: `vi ~/.aws/credentials`. Inside the file, type the characters **dd** repeatedly to delete all the temporary contents. Now, **paste the real code block** you copied from Vocareum into this file. When the new content is in, press the **Escape** key, type `:wq`, and then press **Enter**. This command saves the new file contents and closes the editor. You can confirm the update by running `cat ~/.aws/credentials`.

### Step 11: Install the Encryption Tool

The last step to prepare the server is to install the special command-line tool that handles the encryption. Run the following two commands, one after the other, in the terminal:

  * `pip3 install aws-encryption-sdk-cli`
  * `export PATH=$PATH:/home/ssm-user/.local/bin`

This installs the necessary tool and sets up your terminal so you can easily run the encryption and decryption commands.

## Task 3: Encrypt and Decrypt a File

With your key created and your server set up, you can now practice securing a file.

### Step 12: Create a Mock Sensitive File

First, you need a file to protect. Run the following two commands to create a file named `secret1.txt` and put some test data in it:

  * `touch secret1.txt secret2.txt secret3.txt`
  * `echo 'TOP SECRET 1!!!' > secret1.txt`

You can verify the contents by running the command `cat secret1.txt`. Next, create a directory where the encrypted file will be placed by running: `mkdir output`.

### Step 13: Prepare the Encryption Command

Go back to your text editor where you saved the key ARN. You are going to create a variable on the server that holds your key ARN. Copy this line: `keyArn=(KMS ARN)`. Now, **replace the text (KMS ARN) with the actual ARN code** you copied in Step 6. Once updated, run this command in your File Server terminal.

### Step 14: Encrypt the File

You will use the encryption tool you installed to scramble the file. Run the following full command in your terminal:

```bash
aws-encryption-cli --encrypt \
 --input secret1.txt \
 --wrapping-keys key=$keyArn \
 --metadata-output ~/metadata \
 --encryption-context purpose=test \
 --commitment-policy require-encrypt-require-decrypt \
 --output ~/output/.
```

This command takes your readable file (**plaintext**) and uses your KMS key (`$keyArn`) to scramble it into an unreadable form (**ciphertext**), saving the new file in the `output` directory. If the command succeeds, you won't see any output. You can check for success by running `echo $?`; a result of **0** means it worked.

### Step 15: View the Encrypted File

Run `ls output` to see the new file—it will be named `secret1.txt.encrypted`. Change into the output directory by running `cd output`, and then use `cat secret1.txt.encrypted` to view the contents. What you see is **ciphertext**—the data is protected and unreadable.

### Step 16: Decrypt the File

Finally, you will unscramble the file to prove the process works. Use the following command in the terminal:

```bash
aws-encryption-cli --decrypt \
 --input secret1.txt.encrypted \
 --wrapping-keys key=$keyArn \
 --commitment-policy require-encrypt-require-decrypt \
 --encryption-context purpose=test \
 --metadata-output ~/metadata \
 --max-encrypted-data-keys 1 \
 --buffer \
 --output .
```

This command uses the same key (`$keyArn`) to take the ciphertext and turn it back into plaintext, saving it as a new file. Run the `ls` command and you'll see a file named `secret1.txt.encrypted.decrypted`. Run `cat secret1.txt.encrypted.decrypted` to view its contents. You should see the original **TOP SECRET 1\!\!\!** text—the data is safely decrypted and readable again.

## Challenges
- I incorrectly put the *Default Region* in place of the *AWS Secret Access Key* when creating the AWS Configuration file. I remedied this mistake by terminating the session manager and starting again.
- While encrypting the secret data, I ran the example command *keyArn=(KMS ARN)* without substituting the value in the parenthesis with the correct ARN(Amazon Resource Name) value I copied after creating the KMS(Key Management Service). Corrected that by making the substitution and running the command again.

## Screenshot
_(To Be Added)_

## Takeaways
Encryption is very important in securing sensitive data. I scrambles the original data, making it illegible gibberish and thus useless in the hands of hackers who do not possess the encryption/decryption key. The only way to restore the encrypted data to it's original form is by making use of the decryption key.
