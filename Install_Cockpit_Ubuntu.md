# Installing Cockpit on Ubuntu With 2-Factor Authentication
## Install Cockpit
Instructions: https://cockpit-project.org/running.html#ubuntu
```bash
sudo apt-get install cockpit
```

### If you want 2-factor, follow: "Install Google Authenticator 2-Factor" then:
Edit the file `/etc/pam.d/cockpit`, and at the bottom of the file, append:
```bash
# google authenticator for two-factor
auth required pam_google_authenticator.so
```
Then, restart cockpit:
```bash
sudo systemctl restart cockpit
```