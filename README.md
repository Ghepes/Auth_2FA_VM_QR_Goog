# VM_Google_Auth_QR
SSH SFTP - VM 2-step authentication via Google AUTH the most secure 2-step authentication for your server that you need to install. installation time 5 minutes.
I LOVE This Authenticator, if I knew it existed for VM server, I would have installed it a long time ago.

WINSCP:

![image](https://github.com/user-attachments/assets/6efa55e6-01b0-4872-b461-fe2c9a2ff2cf)
![image](https://github.com/user-attachments/assets/a7f8a4da-0e9d-4735-b95e-76048c292690)


PUTTY:

![image](https://github.com/user-attachments/assets/7101bcd9-7972-4802-a9d8-a5cc91e01ca3)




### Installation steps for Ubuntu TEST of Ubuntu 22.04.1 - ( Login as ROOT to SSH or SFTP to your VM or SERVER )

1. Install Google Authenticator:

```
sudo apt-get update
sudo apt-get install libpam-google-authenticator
```

2. Set up Google Authenticator for a user:

   ```
   google-authenticator
   ```
   And follow the steps carefully (yes or no) ... By skan QR code if it doesn't scan with the phone. There is a code to attach manually.


3. Configure PAM for SSH:
```
   sudo nano /etc/pam.d/sshd
```
Add to the end of the file:
```
auth required pam_google_authenticator.so

```

4. Modify your SSH configuration to enable two-step authentication:
 Edit the file /etc/ssh/sshd_config:
```
sudo nano /etc/ssh/sshd_config

```
Make sure the ChallengeResponseAuthentication line is set to yes:
```
ChallengeResponseAuthentication yes

```

Passwordless Authentication (SSH Key Authentication) Add :
```
AuthenticationMethods publickey,password publickey,keyboard-interactive
```

Comment out any line that disables password authentication to allow OTP entry:
```
#PasswordAuthentication no

```

5. Restart SSH to apply the changes:
   ```
   sudo systemctl restart sshd

   ```





   This method will secure your SSH connections by adding an extra layer of verification, making it much more difficult for unauthorized access to your server.


