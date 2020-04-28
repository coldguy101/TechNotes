# Install Google Authenticator 2-Factor
First, install `libpam-google-authenticator`:
```bash
sudo apt install libpam-google-authenticator
```
In `/etc/pam.d/sshd` add the following line:
```bash
auth required pam_google_authenticator.so
```
Restart sshd:
```bash
sudo systemctl restart sshd.service
```
Modify `/etc/ssh/sshd_config` (change `ChallengeResponseAuthentication` from `no` to `yes`) like the following:
```bash
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no # CHANGE THIS TO YES

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
```
_(you can also change `PasswordAuthentication` to `no`)_

Run the google authenticator command:
```bash
google-authenticator
```
Recommended answers:
```
Make tokens "time-base": yes
Update the .google_authenticator file: yes
Disallow multiple uses: yes
Increase the original generation time limit: no
Enable rate-limiting: yes
```
Save emergency scratch codes and add the profile to your authenticator app (such as Authy or Google Authenticator)
