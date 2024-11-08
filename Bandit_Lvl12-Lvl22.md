## Bandit Walkthrough: Levels 12-22

### Level 12: Hexdump and Compression
The password is hidden within a series of compressed files.

**Steps:**
1. **Reverse Hexdump:**
   ```bash
   xxd -r data.txt data
   ```
2. **Decompress:**
   Repeatedly use `gzip -d`, `bzip2 -d`, and `tar -xvf` to extract the final password. The exact steps may vary based on the compression levels used.

### Level 13: SSH Key Access
The password is stored in `/etc/bandit_pass/bandit14` and can only be accessed using an SSH key.

**Steps:**
1. **Use SSH with the private key:**
   ```bash
   ssh -i sshkey.private bandit14@localhost -p 2220
   ```
2. **Retrieve the password:**
   ```bash
   cat /etc/bandit_pass/bandit14
   ```

### Level 14: Network Service
The password for the next level is obtained by submitting the current password to a network service.

**Steps:**
1. **Use `netcat` to connect to the specified port:**
   ```bash
   nc localhost 30000
   ```
2. **Enter the current password.**
3. **The next password will be displayed.**

### Level 15: SSL Network Service
The password for the next level is obtained by submitting the current password to a network service using SSL encryption.

**Steps:**
1. **Use `openssl s_client` to connect:**
   ```bash
   openssl s_client -connect localhost:30001
   ```
2. **Enter the current password.**
3. **The next password will be displayed.**

### Level 16: Network Service Discovery
The password for the next level is obtained by submitting the current password to a specific port within a range of ports.

**Steps:**
1. **Scan the port range:**
   ```bash
   nmap localhost -p 31000-32000
   ```
2. **Connect to the correct port using `openssl s_client`:**
   ```bash
   openssl s_client -connect localhost:<port_number>
   ```
3. **Enter the current password.**
4. **The next password will be displayed.**

### Level 17: File Comparison
The password for the next level is the only line that has been changed between `passwords.old` and `passwords.new`.

**Steps:**
1. **Use `diff` to compare the files:**
   ```bash
   diff passwords.new passwords.old
   ```
2. **The first line of the output is the password.**

### Level 18: Bypassing `.bashrc`
The password for the next level is stored in the `readme` file. However, the `.bashrc` file is configured to log you out immediately.

**Steps:**
1. **Use `ssh` to directly execute commands:**
   ```bash
   ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
   ```

### Level 19: Setuid Binary
The password for the next level is stored in `/etc/bandit_pass/bandit20`. A setuid binary is provided to access it.

**Steps:**
1. **Execute the setuid binary:**
   ```bash
   ./bandit20-do cat /etc/bandit_pass/bandit20
   ```

### Level 20: Network Service with Password Check
A setuid binary is provided that connects to a local port and checks the password.

**Steps:**
1. **Run the `suconnect` script:**
   ```bash
   ./suconnect <port_number>
   ```
2. **On another terminal, use `nc` to connect to the specified port:**
   ```bash
   nc localhost <port_number>
   ```
3. **Enter the current password.**
4. **The next password will be received.**

### Level 21: Cron Job
The password for the next level is stored in a temporary file created by a cron job.

**Steps:**
1. **Identify the cron job:**
   ```bash
   cat /etc/cron.d/cronjob_bandit22
   ```
2. **Find the temporary file:**
   The script will create a temporary file with a random name. Use the script's logic to determine the filename.
3. **Read the password from the temporary file:**
   ```bash
   cat /tmp/<filename>
   ```

### Level 22: Cron Job and Script Analysis
The password for the next level is stored in a temporary file created by a cron job.

**Steps:**
1. **Identify the cron job:**
   ```bash
   cat /etc/cron.d/cronjob_bandit23
   ```
2. **Analyze the script:**
   ```bash
   cat /usr/bin/cronjob_bandit23.sh
   ```
3. **Determine the temporary filename:**
   The script creates a temporary file based on the current user's username.
4. **Read the password from the temporary file:**
   ```bash
   cat /tmp/<filename>
   ```
